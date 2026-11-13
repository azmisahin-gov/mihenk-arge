# 56.12 – Yerel Benchmark Düzeneği Tasarımı

> **Durum:** Araştırma/test altyapısı tasarımı; kod veya MİHENK üretim bileşeni değildir  
> **Tarih:** 13 Kasım 2026  
> **İlgili belgeler:** [Test planı](56-12-test-plani-ve-basari-olcutleri.md), [motor/runtime uyumluluk araştırması](56-12-motor-runtime-uyumluluk-arastirmasi.md), [test senaryoları](56-12-test-senaryolari.md)

## 1. Amaç ve sınır

Benchmark düzeneği, ASR, VAD, forced alignment ve diarization adaylarını aynı veri, aynı anotasyon, kayıtlı parametreler ve izlenebilir donanım koşullarıyla karşılaştırmak için tasarlanır.

Bu araç:
- MİHENK masaüstü uygulamasının kendisi değildir.
- MİHENK'in nihai teknoloji yığınını belirlemez.
- Gerçek bilirkişi dosyalarını kamuya açık CI sistemine taşımaz.
- Otomatik transkript veya uzman görüşü üretip onaylamaz.
- Bir modelin WER/DER sonuçlarından hukukî veya adli yeterlilik çıkarmaz.

İlk amaç, **yerel araştırma makinesinde tekrar üretilebilir model/runtime ölçümü** yapmaktır. Benchmark aracı hangi dilde yazılırsa yazılsın bu seçim ana uygulamanın dili/çatısı hakkında karar oluşturmaz.

## 2. Tasarım ilkeleri

1. **Aynı girdi, aynı referans:** Adaylar aynı test split'i ve aynı sürümlü insan referansıyla değerlendirilir.
2. **Model ile runtime ayrılır:** Aynı Whisper ağırlığının whisper.cpp ve faster-whisper gibi farklı runtime'lardaki sonuçları ayrı koşu olarak kaydedilir.
3. **Ham çıktı korunur:** Ham ASR, normalize edilmiş metrik girdisi ve uzman düzeltmesi birbirinin üzerine yazılmaz.
4. **Yerel ve ağsız çalışma:** Test çalışırken ağ erişimi kapatılır veya izlenir; beklenmeyen dış bağlantı testi başarısız yapar.
5. **Tekrarlanabilirlik:** Model checksum, runtime sürümü, parametreler, donanım, veri split'i, normalizasyon kuralı ve ölçüm yazılımı sabitlenir.
6. **Lisans/veri kökeni:** Kod lisansı ile model ağırlığı ve veri kümesi lisansı ayrı kaydedilir.
7. **Güvenli hata davranışı:** Bir worker çökerse diğer testlerin sonuçları ve kaynak veriler bozulmaz.
8. **İnsan incelemesi ayrı:** Referans anotasyonu, model çıktısına bakılarak değiştirilmez; hata kararı modelin kendi güven puanına bırakılmaz.

## 3. Önerilen mimari

Benchmark düzeneği araştırma ortamında beş katmana ayrılır:

| Katman | Sorumluluk | İlk uygulama biçimi |
|---|---|---|
| Test tanımı | Veri kümesi, split, senaryo, model/runtime, parametre ve tekrar sayısını seçer | Sürümlü JSON/YAML test tanımı |
| Orkestratör | Koşuları sıraya koyar, kaynakları ve süreçleri yönetir | Küçük yerel CLI/iş yöneticisi |
| Motor bağdaştırıcıları | Her ASR/VAD/alignment/diarization motorunu kendi desteklediği biçimde çalıştırır | Ayrı adapter/worker |
| Ölçüm ve kaynak izleme | WER/CER/DER, zaman sapması, süre, RAM/VRAM, CPU/GPU ve hata bilgisini toplar | Ayrı metrik modülleri |
| Sonuç deposu/raporlama | Ham çıktı, normalize sonuç, makine koşusu ve karşılaştırma tablolarını saklar | Yerel deney klasörü + JSONL/CSV raporları |

### 3.1 Test tanımı

Bir test tanımı aşağıdaki alanları belirler:
- test kimliği ve sürümü;
- veri kümesi ve split kimliği;
- anotasyon politikası ve referans sürümü;
- çalıştırılacak görev (ASR, VAD, alignment veya diarization);
- model ve runtime adapter kimliği;
- model ağırlığı checksum ve lisans kaydı;
- parametreler, chunk/VAD/overlap seçenekleri;
- test tekrar sayısı ve soğuk/sıcak başlatma türü;
- kullanılacak metrik profili;
- ağ politikası ve yerel dosya izinleri.

Aynı test tanımında model parametresi değişirse yeni koşu kimliği oluşturulur. Önceki sonuç üzerine yazılmaz.

### 3.2 Motor bağdaştırıcısı sözleşmesi

Her motor adapter'ı şu ortak işlevleri sunacak şekilde tasarlanmalıdır:
1. **prepare:** Model/runtime dosyasını ve checksum/lisans durumunu doğrula.
2. **capabilities:** Dil, model biçimi, kanal, sample rate, timestamp ve GPU/CPU desteğini bildir.
3. **run:** Verilen yerel ses ve parametrelerle işleme başlat.
4. **collect:** Ham çıktı, exit code, süre, stdout/stderr ve hata kodunu al.
5. **normalize-output:** Yalnız ortak sonuç şemasına dönüştür; ham motor çıktısını değiştirme.
6. **cleanup:** Geçici dosyaları güvenli biçimde temizle; model cache'i açıkça politika ile yönet.

Adapter'lar aynı komut satırını veya aynı model dosyasını kullanmak zorunda değildir. whisper.cpp GGML, faster-whisper CTranslate2, Transformers/PyTorch ve sherpa-onnx gibi runtime'lar farklı adapter olarak kalır.

### 3.3 Önerilen ilk adapter listesi

| Adapter | İlk amaç | Girdi/çıktı koşulu | Öncelik |
|---|---|---|---|
| whisper.cpp | Çok dilli Whisper temel modeli ve nicemlenmiş varyantlar | GGML model biçimi; ham segment/token çıktısı | P1 |
| faster-whisper | Whisper modelini CTranslate2 runtime ile çalıştırmak | CTranslate2 model klasörü; segment ve süre bilgisi | P1 |
| Transformers/PyTorch | TurkMedSTT M1 gibi kaynak mimari modeller | Model kartındaki desteklenen mimari/processor | P1 |
| WhisperX alignment | Uzman tarafından doğrulanmış metne zaman önerisi | ASR çıktısı ve Türkçe alignment ağırlığı | P2 |
| pyannote.audio | Diarization kalite karşılaştırma hattı | Gated ağırlık koşulları kabul edilmiş, yerel model | P2 |
| sherpa-onnx | ONNX tabanlı yerel VAD/diarization denemesi | Her segmentation/embedding ağırlığının lisansı ayrı | P2 |

Bu tablo test sırasıdır; üretim dağıtımına kabul veya nihai motor tercihi değildir.

## 4. Önerilen yürütme sırası

Tek bir test koşusu aşağıdaki adımları izler:

1. Test tanımını oku ve şema doğrulaması yap.
2. Veri kümesi manifestinin lisans/kullanım durumunu denetle.
3. Girdi sesinin yerel varlığını, boyutunu, formatını ve checksum değerini doğrula.
4. Referans metin/anotasyon sürümünü doğrula; model çıktısının referans anotasyon alanlarına erişmesini engelle.
5. İşletim sistemi, CPU, RAM, GPU/VRAM, driver, runtime ve model manifestini kaydet.
6. Model ağırlığının checksum ve lisans kaydını doğrula.
7. Ağ kapalı koşuda adapter'ı çalıştır; ağ isteği gözlenirse koşuyu başarısız yap.
8. İşlem süresi, ilk çıktı gecikmesi, tepe RAM/VRAM, CPU/GPU ve disk geçici alanını kaydet.
9. Ham motor çıktısını salt okunur deney çıktısına yaz.
10. Aynı sürümlü normalizasyon ve puanlayıcıyla WER/CER/DER/zaman metriklerini hesapla.
11. Hata, durdurma, çökme ve kurtarma durumunu kaydet.
12. Karşılaştırma raporu üret; model sıralamasını tek skora indirgeme.

## 5. Ortak sonuç şeması

Her koşu için:
- run_id, test_id, started_at, completed_at, status.
- dataset_id, dataset_version, split, sample_id.
- source_audio_sha256, varsa türev ses ilişkisi.
- model_id, model_revision, model_sha256, model_license.
- runtime_id, runtime_version, runtime_build, runtime_license.
- parameters, preprocessing, quantization.
- environment (OS, CPU, RAM, GPU, VRAM, driver).
- raw_output_ref, normalized_output_ref, error_ref.
- metrics (WER, CER, critical error counts, RTF, RAM, VRAM, diarization DER components, timestamp error as applicable).
- network_policy, network_violation, human_review_status.

Gerçek dosya yolu, kişi adı, mahkeme adı, görev numarası ve gerçek konuşmacı kimliği ortak rapor şemasına yazılmaz. Yerel ses referansı ayrı ve erişim kontrollü dosya konumunda tutulur; public raporda anonim sample ID kullanılır.

Makinece okunabilir bir başlangıç örneği [test koşusu JSON şablonunda](56-12-test-kosu-kaydi-sablonu.json) bulunur.

## 6. Metrik modülleri

### 6.1 ASR

- WER-TR-1 ve WER-TR-2 ayrı raporlanır.
- CER-TR-1, normalizasyon sürümüyle birlikte tutulur.
- Özel ad, sayı, tarih, saat, olumsuzluk ve kısaltma kritik hata sayıları ayrıca gösterilir.
- Sessizlikte metin, anlaşılmayan bölümün doldurulması ve atlanan konuşma ayrıca sayılır.
- Mikro ortalama, dosya bazında skor ve test alt grubu skorları birlikte gösterilir.

### 6.2 VAD

- Konuşma süresi recall/kaçırılan konuşma aralığı.
- Sessiz bölgede yanlış konuşma işaretleme.
- Başlangıç/bitiş sınır farkı ve kesilen kelime sayısı.
- VAD'nin çıkardığı her segment için kaynak dosya zaman ofseti ve padding kaydı.

VAD hızlı ASR için kullanılabilir; ancak doğruluğu kanıtlanana kadar VAD çıktısı orijinal sesin yerine veya eksiksiz konuşma kanıtı olarak geçmez.

### 6.3 Forced alignment

- Başlangıç/bitiş zaman sapması.
- Zaman verilemeyen token/karakter oranı.
- Sayı, kısaltma, özel ad, belirsiz kelime ve örtüşme alt grupları.
- Yanlış metne hizalama yapıldığında bunun “metin doğru” statüsü üretmediği kontrolü.

### 6.4 Diarization

- DER; FA, Miss ve Confusion bileşenleri.
- JER ve konuşmacı sayısı hatası (uygunsa).
- Örtüşen konuşma dahil/hariç duyarlılık karşılaştırması.
- Kayıt içinde etiket tutarlılığı; kayıtlar arasında kişi eşleştirmesi yok.

## 7. Kaynak kullanımı ve ölçüm yöntemi

Her koşuda şu ölçüler alınır:
- soğuk model yükleme süresi;
- sıcak çalıştırmada ilk çıktı gecikmesi;
- işlem süresi ve RTF;
- tepe sistem RAM'i ve GPU VRAM'i;
- model, runtime, cache ve geçici dosya boyutu;
- CPU/GPU kullanım yüzdeleri ve mümkünse sıcaklık/güç sınırı;
- işlem çökmesi, kilitlenmesi, yeniden deneme ve devam süresi.

İlk PoC'de süreç ölçümü için OS'ye özgü sistem araçları veya uygun bir kaynak izleme kütüphanesi kullanılabilir. Bu ölçüm aracı MİHENK üretim bağımlılığı olarak kabul edilmemelidir. Windows, Linux/Pardus ve macOS sonuçları kendi işletim sistemi bağlamında raporlanır; ham sayılar donanım/OS farkı notu olmadan kıyaslanmaz.

RAM ile VRAM ayrı gösterilir. Model dosyasının disk boyutu RAM ihtiyacı olarak raporlanmaz. Soğuk ve sıcak koşular karıştırılmaz; tek koşu yerine tekrarlı koşuların medyanı ve P95 değeri verilir.

## 8. Güvenlik ve veri saklama

- Koşu varsayılanı yerel ağ erişimi kapalıdır.
- Model indirme ve lisans onayı, vaka materyali işlenmeden önce ve ayrı kurulum adımında yapılır.
- Model dosyaları checksum doğrulaması yapılmadan çalıştırılmaz.
- Decoder ve model worker'ı görev klasörü dışında dosya okuyamaz; uygulama izinleriyle sınırlandırılır.
- Worker ortam değişkenleri, log ve crash dump'ları ses içeriği veya kişisel veri yazmamalıdır.
- Gerçek dosya veya transkript public test fixture, CI, GitHub issue veya PR eki yapılmaz.
- Ham test çıktıları için yerel saklama süresi ve silme politikası belirlenir.
- Referans metinler ve anotasyonlar model adapter'ına verilmez; yalnız skorlayıcı aşaması erişir.
- Bir model/worker hata verirse orijinal ses ve diğer görev alanları değişmeden kalır.

## 9. LLM, GGUF ve embedding sınırı

- ASR benchmark döngüsüne LLM eklenmez. Modelin kendi ürettiği metne başka bir LLM ile düzeltme yaptırmak, ASR motorunun ham başarımını ölçmeyi bozar.
- GGUF, genel amaçlı LLM modelleri için kullanılan bir model biçimidir; whisper.cpp'nin GGML biçiminin yerine geçmez. Bir model biçimi ancak ilgili mimari ve runtime açıkça destekliyorsa kullanılır.
- Diarization embedding'leri, metin arama/semantic retrieval embedding'leriyle aynı amaçta değildir. Bu vektörler gerçek kişi kimliği veya kayıtlar arasında kişi eşleştirme için kullanılmaz.
- Rapor dil kontrolü veya alan eşleme gibi LLM yardımları ileride ayrı bir deney olarak değerlendirilebilir; ASR ve anotasyon benchmark'ıyla aynı skor hattına konmaz.
- İlk benchmark için LLM, RAG veya genel metin embedding motoru zorunlu bağımlılık değildir.

## 10. İlk PoC kapsamı

İlk benchmark PoC'si şu dar kapsamda başlayabilir:
1. FLEURS tr_tr test split'i ve izin koşulları doğrulanmış Common Voice Turkish split'i.
2. whisper.cpp GGML ve faster-whisper/CTranslate2 üzerinde desteklenen aynı Whisper ağırlığı.
3. CPU koşusu ve varsa desteklenen GPU koşusu.
4. Tekrarlı koşularla WER/CER, kritik hata, RTF, tepe RAM/VRAM, soğuk/sıcak yükleme.
5. JSON sonuç kaydı ve karşılaştırma tablosu.

TurkMedSTT M1, diarization, WhisperX alignment ve sherpa-onnx ikinci aşamada eklenir. İlk PoC başarıyla çalışmadan MİHENK'e runtime paketleme kararı verilmez.

## 11. Açık kararlar

1. Benchmark PoC'sinin Python CLI/izole worker olarak mı, yoksa farklı bir araçla mı hazırlanacağı.
2. Test koşusu ve sonuç şemasının kesin sürümü.
3. Desteklenecek ilk OS/hardware profilleri.
4. Model ağırlığı ve veri seti arşivlerini kim indirecek, kim lisans/koşul onayı verecek.
5. Yerel test alanının şifreleme, saklama ve silme yöntemi.
6. Test raporunun JSON/CSV/Markdown dışa aktarma biçimi ve kıyaslama arayüzü.

## 12. Kaynaklar

- [whisper.cpp – GGML modeli, VAD ve tinydiarize](https://github.com/ggml-org/whisper.cpp)
- [faster-whisper – CTranslate2 tabanlı yerel Whisper](https://github.com/SYSTRAN/faster-whisper)
- [CTranslate2 – quantization](https://opennmt.net/CTranslate2/quantization.html)
- [WhisperX – ASR, VAD, forced alignment ve diarization](https://github.com/m-bain/whisperX)
- [pyannote community-1 – yerel diarization](https://huggingface.co/pyannote/speaker-diarization-community-1)
- [sherpa-onnx – offline speech processing](https://github.com/k2-fsa/sherpa-onnx)

Bu belge test altyapısı önerisidir. Araçların kurulumu, model çalıştırılması veya gerçek verinin işlenmesi henüz yapılmış değildir.
