# 56.12 – İlk Benchmark Koşu Matrisi ve Uygulama Sırası

> **Durum:** Koşu tasarımı; henüz model çalıştırılmadı  
> **Tarih:** 13 Kasım 2026  
> **Amaç:** ASR model kalitesi, runtime/quantization etkisi ve hedef cihaz kaynak ihtiyacını birbirine karıştırmadan ölçmek.

## 1. Bu belgenin karar sınırı

Bu matris, 56.12'nin ilk model karşılaştırmasının nasıl yürütüleceğini sabitler. Bir modelin seçildiği, kabul edildiği veya MİHENK içinde üretime hazır olduğu anlamına gelmez.

Üç farklı soru ayrı koşu ailesidir:

1. **Model kalitesi:** Aynı insan referansına karşı, her modelin kendi resmî/önerilen çalışma biçiminde ürettiği transkript ne kadar doğru?
2. **Dağıtım/runtime:** Aynı modelin desteklenen farklı runtime, nicemleme ve donanım seçenekleri doğruluğu, süreyi ve belleği nasıl etkiliyor?
3. **Uzman iş akışı:** ASR taslağı, bilirkişinin dinleme, düzeltme, belirsiz bölümü işaretleme ve rapora taşıma süresini gerçekten azaltıyor mu?

Bu soruların ölçümleri tek puana indirgenmez. Model seçimi ancak üç sonuç birlikte değerlendirildikten sonra yapılır.

## 2. Test veri grupları

Test kaynağı ve split'i her koşuda açıkça kaydedilir. Farklı kaynakların puanları tek bir “Türkçe WER” altında birleştirilmez.

| Veri kimliği | Veri kaynağı | İlk kullanım | Kullanım koşulu / sınırlama | Öncelik |
|---|---|---|---|---|
| CV27-TEST | Common Voice Turkish 27.0 resmî test split'i | Okunmuş konuşma temel ASR | Sürüm, lisans, resmi split ve indirme snapshot'ı kullanım tarihinde yeniden kaydedilir | P1 |
| FLEURS-TR-TEST | Google FLEURS tr_tr resmî test split'i | Okunmuş konuşma dış karşılaştırma | CC BY atfı ve kaynak kartı korunur; split kilitli tutulur | P1 |
| CONTROL-READ | MİHENK kurgusal okuma seti | Özel ad, sayı, tarih, olumsuzluk ve yazım regresyonu | Gönüllü rızası, sentetik metin, ayrı referans anotasyonu; henüz kayıt alınmadı | P1 |
| CONTROL-DIALOGUE | MİHENK kontrollü doğal diyalog | Doğal konuşma, kısa geri bildirim, kesilme ve tereddüt | Gönüllü rızası, bağımsız insan anotasyonu; henüz kayıt alınmadı | P1 |
| CONTROL-MONO-OVERLAP | Aynı miks/mono kanalda kontrollü örtüşen konuşma | Gerçek diarization karşılaştırması | İki veya daha fazla gönüllü, zamanlı anonim referans, örtüşme anotasyonu; henüz kayıt alınmadı | P1 – diarization |
| TURKASR-EXTERNAL | TurkASR-Bench ve harici leaderboard | Yayımlanmış sonucu kıyaslama | Karma kaynak lisansı; her alt küme ayrı hak kontrolünden geçmeden indirilmeyecek/dağıtılmayacak. Harici skor, MİHENK koşusu değildir | Yalnız dış referans |
| REAL-TURNTURK-EXP | Real-TurnTurk | Zaman/VAD/konuşma sırası keşfi | Ayrı konuşmacı kanalları içerir; tek miks mono diarization kabul verisi değildir. Görsel özellikler kullanılmaz | P2 |

**İlk ASR karşılaştırması:** CV27-TEST ve FLEURS-TR-TEST ayrı tablolarla raporlanır. CONTROL-READ ve CONTROL-DIALOGUE kayıt/onay tamamlanınca eklenir. Doğal konuşma seti hazır değilse temiz okuma sonucuyla gerçek iş yüküne uygunluk kararı verilemez.

**İlk diarization karşılaştırması:** CONTROL-MONO-OVERLAP olmadan üretim diarization kararı verilmez. Real-TurnTurk'ün ayrı kanalları tek başına bu boşluğu kapatmaz.

## 3. Model kalite koşuları

Aşağıdaki satırlar farklı model/çalışma biçimi kombinasyonlarıdır. Her satırın kendi koşu kimliği, model revision, artifact checksum, runtime ve parametre kaydı vardır.

| Koşu kimliği | Model | Referans runtime / biçim | İlk deney | Neden |
|---|---|---|---|---|
| MQUAL-WHISPER-LV3 | Whisper Large v3 | whisper.cpp'nin desteklediği temel GGML modeli; önce FP16/FP32 referans desteği doğrulanır | P1 | Çok dilli ana karşılaştırma |
| MQUAL-WHISPER-TURBO | Whisper Large v3 Turbo | whisper.cpp'nin desteklediği temel GGML modeli | P1 | Daha düşük gecikme olasılığı; kalite farkı ölçülecek |
| MQUAL-TURKMED-M1 | TurkMedSTT M1 | Kaynak model kartındaki Transformers/PyTorch çalışma yolu | P1 | Türkçe uyarlama; dönüştürme varsayımı yok |
| MQUAL-QWEN-06B | Qwen3-ASR-0.6B | Resmî qwen-asr / Transformers yerel ağırlık | P1 | Daha küçük çok dilli alternatif |
| MQUAL-QWEN-17B | Qwen3-ASR-1.7B | Resmî qwen-asr / Transformers yerel ağırlık | P1 | Bağımsız model ailesi karşılaştırması |
| MQUAL-UFAKZEKA | ufakzeka-kulak | Model kartının desteklediği Parakeet.cpp veya sherpa-onnx dışa aktarımı | P2 | Küçük/CPU adayı; doğal diyalogta kalite boşluğu |
| MQUAL-VOSK | Vosk Turkish Small | Vosk resmî runtime | P3 | Çok düşük kaynak taban çizgisi; yayımlanmış Türkçe WER yok |

### 3.1 Referans koşu kuralı

- Modelin özgün mimarisini destekleyen runtime ilk referanstır. Bir modelin başka runtime'a dönüştürülebileceği varsayılmaz.
- Önce referans modelin dosyası, tokenizer/processor ve runtime sürümü birlikte sabitlenir.
- Model ağırlığı veya tokenizer değişirse yeni model kimliği/koşu oluşur.
- Tüm adaylara aynı test örnekleri, aynı kilitli referans metinleri ve aynı normalizasyon profilleri uygulanır.
- Modelin kendi iç güven puanı, konuşma doğruluğu veya bilirkişi kanaati yerine kullanılamaz.
- Model çıktısı insan referansı kilitlendikten sonra puanlanır.

## 4. Runtime ve nicemleme koşuları

Runtime deneyi, model kalite karşılaştırmasından sonra yapılır. Her model için yalnızca resmen desteklenen ve dönüştürme zinciri doğrulanmış seçenekler açılır.

| Model ailesi | Runtime/format koşusu | İlk donanım deneyi | Açılma şartı |
|---|---|---|---|
| Whisper Large v3 | whisper.cpp GGML FP16/FP32 referans | CPU; uyumlu GPU varsa ayrıca | GGML model ve build doğrulaması |
| Whisper Large v3 | whisper.cpp GGML Q5_0 veya Q8_0 | CPU ve uyumlu GPU | Nicemleme sonrası WER/CER ve kritik hata yeniden ölçülür |
| Whisper Turbo | whisper.cpp GGML referans ve desteklenen quant | CPU; uyumlu GPU varsa ayrıca | Model/runtime desteği ve checksum |
| Whisper Large v3 / Turbo | faster-whisper + CTranslate2 FP16 | Uyumlu NVIDIA GPU | Aynı modelin CTranslate2 dönüşümü ve çıktının referansla doğrulanması |
| Whisper Large v3 / Turbo | faster-whisper + CTranslate2 INT8 | CPU; destek varsa GPU | Runtime'ın gerçekten seçtiği compute type loglanır |
| TurkMedSTT M1 | Transformers/PyTorch referans | CPU ve uyumlu GPU ayrı | Model kartı, bağımlılık ve kaynak tüketimi doğrulaması |
| TurkMedSTT M1 | CTranslate2/başka optimize edilmiş biçim | Yalnız ayrı PoC | Model mimarisi, tokenizer, ağırlık dönüşümü ve çıktı eşdeğerliği başarıyla doğrulanmadan açılmaz |
| Qwen3-ASR 0.6B / 1.7B | Transformers qwen-asr offline | CPU/GPU kapasitesine göre | Yerel ağırlıkla ağsız çıkarım doğrulaması |
| Qwen3-ASR 0.6B / 1.7B | vLLM batch | Uyumlu NVIDIA GPU | vLLM'nin resmî model desteği, sürüm ve GPU uyumu doğrulanır |
| ufakzeka-kulak | Parakeet.cpp GGUF f32 / q8_0 | CPU | Yalnız model kartında belirtilen Parakeet.cpp |
| ufakzeka-kulak | sherpa-onnx INT8 | CPU | ONNX export, tokenizer ve decoder uyumluluğu |
| Vosk Turkish Small | Vosk runtime | CPU | Model dosyası/sürüm/checksum doğrulaması |

**Nicemleme ilkesi:** INT8, Q5_0, Q8_0, FP16, BF16 ve GGUF/GGML/ONNX aynı kavram değildir. Dosya biçimi, ağırlık nicemleme türü ve runtime compute türü ayrı alanlarda kaydedilir. Örneğin CTranslate2'nin talep edilen compute type'ı, donanım/backend desteğine göre başka bir türe dönüştürülebilir; yapılandırma metninden gerçek çalışma türü varsayılmaz.

**GGUF ilkesi:** GGUF, bazı model aileleri ve özel runtime'lar için kullanılabilir; whisper.cpp GGML modelinin yerine geçmez. Bir GGUF dosyası yalnızca onu destekleyen model/runtime çiftiyle test edilir.

## 5. Diarization koşuları

Diarization ASR'den bağımsız değerlendirilir. Aynı-miks tek kanal ve ayrı kanal kayıt sonuçları farklı deney türleridir.

| Koşu kimliği | Aday | Veri | Beklenen ölçüm | Açılma şartı |
|---|---|---|---|---|
| DQUAL-PYANNOTE-C1 | pyannote speaker-diarization-community-1 | CONTROL-MONO-OVERLAP | DER, FA, Miss, Confusion, JER, overlap | Model şartları/HF erişim koşulu, yerel test ve model lisansı |
| DQUAL-SHERPA-ONNX | sherpa-onnx + desteklenen segmentation/embedding pipeline | CONTROL-MONO-OVERLAP | DER bileşenleri, RAM, RTF | Türkçe/konuşmacı verisi ve her model ağırlığı lisansının doğrulanması |
| DQUAL-NEMO-RESEARCH | NVIDIA NeMo Sortformer/Nemotron adayı | CONTROL-MONO-OVERLAP | DER bileşenleri, GPU bellek, RTF | Araştırma ön koşulu; paketleme kararı değildir |

Ayrı mikrofon kanalları, mono diarization referansı gibi puanlanmaz. Mono karışım üretildiyse karışım parametreleri, kaynak kanallar, gecikme/ofset ve clipping kontrolü kaydedilir. Konuşmacı kimliği veya kayıtlar arası kişi eşleştirmesi yapılmaz.

## 6. İşlem sırası

| Aşama | İş | Gerekli çıktı | Durum |
|---|---|---|---|
| B0 | Manifest, anotasyon şeması, test koşusu kaydı ve puanlayıcı doğrulama | Tekrarlanabilir örnek/koşu kimliği | Tasarlandı; kodlanıp doğrulanmadı |
| B1 | CV27 ve FLEURS kaynak snapshot/split/lisans kontrolü | Yerel test seti kabul kaydı | Bekliyor |
| B2 | İnsan referans transkript kontrolü | Kilitli anotasyon sürümü | Bekliyor |
| B3 | Whisper Large v3/Turbo ve TurkMedSTT M1 temel koşuları | İlk WER/CER sonuç raporu | Bekliyor |
| B4 | Qwen3-ASR 0.6B/1.7B koşuları | Model ailesi karşılaştırması | Bekliyor |
| B5 | ufakzeka-kulak ve düşük kaynak adayları | CPU/quantization kıyaslaması | Bekliyor |
| B6 | Runtime/nicemleme/donanım matrisi | RAM/VRAM/RTF + kalite farkı | Bekliyor |
| B7 | Kontrollü diyalog ve mono örtüşme kayıtları | Doğal konuşma ASR ve diarization seti | Gönüllü/izin/anotasyon bekliyor |
| B8 | Diarization motor karşılaştırması | DER ve kaynak tüketimi raporu | B7 sonrasında |
| B9 | Uzman iş akışı pilotu | Süre, düzeltme yükü ve uzman kabul notu | Ön koşullar tamamlandıktan sonra |

İlk model kalite koşuları tamamlanmadan LLM, embedding veya masaüstü framework seçimi için benchmark sonuçları kullanılamaz.

## 7. Ölçüm alanları

Her koşu için aşağıdaki alanlar tutulur. Ölçümler dosya ve test alt grubu bazında da raporlanır.

### Model / runtime

- Model deposu, model adı, tam revision/commit ve artifact SHA-256.
- Tokenizer/processor kimliği ve checksum.
- Runtime/kütüphane sürümü, build seçenekleri ve bağımlılık lock dosyası.
- Dosya biçimi (GGML/GGUF/ONNX/Transformers/CTranslate2 vb.) ve gerçek compute/quantization türü.
- ASR decode parametreleri, VAD/chunk ayarı, kanal ve örnekleme dönüşümü.

### Donanım / işletim

- İşlemci modeli, çekirdek/thread, RAM miktarı ve işletim sistemi sürümü.
- GPU modeli, VRAM miktarı, sürücü ve CUDA/Vulkan/Metal/OpenVINO sürümü; varsa NPU.
- Başlangıç anında boş RAM/VRAM ve arka plan yükü.
- Güç profili ve güç kaynağı (taşınabilir cihazda batarya/AC ayrımı).
- Disk tipi/boş alanı ve modelin depolama boyutu.

### Performans

- Modeli ilk yükleme süresi ve soğuk başlangıç süresi.
- İlk token/ilk kısmi transkript gecikmesi (streaming destekleniyorsa).
- Toplam işleme süresi ve RTF = işlem süresi / ses süresi.
- Saniyelik/segment bazlı throughput, kuyrukta bekleme ve çoklu dosya verimi.
- Süreç tepe RSS/working set RAM, tepe VRAM ve model dosya boyutu.
- CPU/GPU kullanım örneklemesi; termal throttling ve çökme/yeniden başlatma.
- Tekrar koşularında medyan, P95 ve aralık; yalnız en iyi koşu yayımlanmaz.

### Kalite

- WER-A, WER-B, CER.
- Özel ad, sayı, tarih, saat, olumsuzluk ve kısaltma hataları.
- Atlanan konuşma, sessizlikte metin üretimi ve belirsiz aralık davranışı.
- Zaman aralığı/kelime hizalama hatası.
- İnsan düzeltme süresi ve segment başına düzeltme sayısı.
- Diarization koşusunda DER bileşenleri, overlap dahil/hariç sonuç ve konuşmacı sayısı hatası.

## 8. Tekrarlanabilirlik ve raporlama

- Test örnek kimliği, kaynak sürüm, split, anotasyon sürümü ve model koşusu kimliği değişmez kayıtlarla bağlanır.
- Rastgelelik varsa seed kaydedilir; deterministik olmayan GPU davranışı not edilir.
- Aynı koşu tekrarlandığında sonuçlar üzerine yazılmaz; yeni koşu kimliği oluşturulur.
- Model/decoder parametresi ayarlandıysa bu ayar yalnız development split üzerinde yapılır. Kilitli test seti yeniden açılırsa locked statüsünü kaybeder.
- Model karşılaştırmalarında aynı test örneği eşleştirilmiş şekilde analiz edilir; mümkünse bootstrap güven aralıkları rapora eklenir.
- Genel skor yanında konuşma biçimi (okuma/doğal diyalog/örtüşme), kaynak, dosya süresi ve akustik koşul alt grupları ayrı gösterilir.
- Harici leaderboard sonuçları “dış referans” etiketiyle sunulur ve MİHENK test tablosuna karıştırılmaz.
- Bir koşu yalnız teknik olarak tamamlandığında “başarılı” sayılmaz. Güvenlik, lisans, veri bütünlüğü ve referans koşulları da sağlanmalıdır.

## 9. Henüz sabitlenmeyecek değerler

Aşağıdaki kararlar hedef donanım ve gerçek ölçüm olmadan verilmeyecek:

- Asgari RAM/VRAM.
- En az kabul edilebilir RTF veya toplam görev süresi.
- Üretim için en düşük WER/CER.
- Belirli quantization seviyesinin varsayılan olması.
- LLM/embedding modeline ihtiyaç olup olmadığı.
- Masaüstü uygulama çatısı ve mobil geçiş mimarisi.
- Diarization'ın her görevde otomatik çalıştırılması.

Özellikle “en hızlı” ya da “en az RAM kullanan” model tek başına en iyi model değildir. Hatalı kritik kelime üretimi, düşük kaynak tüketimiyle telafi edilmiş sayılmaz.

## 10. Çıkış ölçütü – 56.12 araştırma aşaması ne zaman tamamlanmış sayılır?

Aşağıdaki maddeler tamamlanınca 56.12 araştırma ve test tasarımı aşaması kapatılıp uygulama mimarisine geçilebilir:

- [ ] Görev kapsamı ve 56.12/56.11 ayrımı alan uzmanı tarafından doğrulandı.
- [ ] Test veri kümelerinin lisans/erişim ve split kayıtları tamamlandı.
- [ ] Anotasyon yönergesi ve Türkçe normalizasyon profilleri uzman tarafından onaylandı.
- [ ] En az bir kilitli okuma/temel ASR seti insan referansıyla hazırlandı.
- [ ] Doğal konuşma ve örtüşme gereksinimi için yeterli kontrollü veri/anotasyon hazırlandı veya bu sınır açıkça kabul edildi.
- [ ] Benchmark düzeneği küçük sentetik testle tekrar üretilebilir olduğunu gösterdi.
- [ ] Ana ASR adayları aynı test örneklerinde çalıştırıldı.
- [ ] Hedef donanım profillerinde RAM/VRAM/RTF ve sıcak/soğuk başlangıç ölçüldü.
- [ ] Diarization gerekli bulunuyorsa mono örtüşmeli veri üzerinde ayrı değerlendirme yapıldı; gerekmiyorsa pilot kapsamından çıkarıldığı gerekçelendirildi.
- [ ] Bilirkişi ile görev süresi/düzeltme eforu ve iş akışı kabulü ölçüldü.
- [ ] Lisans, güvenlik, veri saklama, model güncelleme ve geri alma riskleri karara bağlandı.
- [ ] İlk sürümde hangi motorların gerçekten paketleneceği ADR ile seçildi.

**Önerilen tahmini iş yükü (takvim değil, çalışma paketleri):**
- Araştırma ve tasarım belgelerinin bütünleştirilmesi: son bütünlük kontrolü.
- Test ortamı/manifest/puanlayıcı PoC: 1 çalışma paketi.
- Açık veri kaynaklarının yerel snapshot ve referans kontrolü: 1 çalışma paketi.
- İlk ASR kalite koşuları: 1 çalışma paketi.
- Runtime/donanım ölçümleri: 1 çalışma paketi.
- Kontrollü doğal diyalog/diarization anotasyonu: veri hazırlığına bağlı 1 çalışma paketi.
- Uzman iş akışı doğrulaması ve karar kayıtları: 1 çalışma paketi.

Bu paketler süre taahhüdü değildir; her birinin bitişi ölçülebilir çıktı ile tanımlanır.

## 11. Sonraki somut iş

İlk uygulama işi, gerçek veri veya model eğitimi değil, **B0 benchmark doğrulayıcısı ve koşu kaydı** olmalıdır: manifest şemasını denetleyen, model/runtime kimliklerini toplayan, ses dosyasını hash'leyen, ağ erişimini test koşusunda kapatan ve sonuçları JSON olarak yazan küçük yerel araç. Ardından FLEURS/Common Voice test snapshot'ı ve anotasyon kontrolü yapılır.

## 12. Kaynaklar

- [whisper.cpp README – model boyutu, bellek ve nicemleme](https://github.com/ggml-org/whisper.cpp)
- [CTranslate2 – nicemleme ve compute türü dönüşümü](https://opennmt.net/CTranslate2/quantization.html)
- [Qwen3-ASR – Türkçe desteği, offline/streaming ve yerel ağırlık kullanımı](https://github.com/QwenLM/Qwen3-ASR)
- [Qwen3-ASR-1.7B model kartı](https://huggingface.co/Qwen/Qwen3-ASR-1.7B)
- [TurkASR-Bench / Turkish ASR Leaderboard](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench)

Bu belge test planıdır; model çalıştırma, benchmark sonucu veya ürün kabul kararı içermez.
