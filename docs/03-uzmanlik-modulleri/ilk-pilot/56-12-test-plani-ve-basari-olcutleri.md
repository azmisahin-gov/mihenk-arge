# 56.12 – Test Planı ve Başarı Ölçütleri

> **Durum:** Test tasarımı; henüz model/ürün kabul eşiği veya üretim kararı değildir  
> **Tarih:** 13 Kasım 2026  
> **İlişkili belgeler:** [56.12 uçtan uca teknik iş akışı](56-12-teknik-is-akisi.md), [veri kümeleri kaydı](56-12-veri-kumesi-kayitlari.md), [transkripsiyon anotasyon kuralları](56-12-transkripsiyon-anotasyon-kurallari.md), [veri kümesi manifest şablonu](56-12-veri-kumesi-manifest-sablonu.json)

## 1. Amaç

Bu plan, MİHENK 56.12 modülünün ses dosyası kabulünden uzman tarafından doğrulanmış transkript ve rapor taslağına kadar olan işlevlerini tekrarlanabilir testlerle değerlendirmek için hazırlanmıştır.

Testler üç ayrı soruyu cevaplamalıdır:

1. **Doğruluk:** Motor ve uygulama hangi koşullarda ne tür hata yapıyor?
2. **İşletilebilirlik:** Seçilen model/runtime donanımda ne kadar hızlı ve kararlı çalışıyor?
3. **Uzman iş akışına katkı:** Bilirkişinin toplam işini, tekrar dinleme ve manuel düzenleme yükünü gerçekten azaltıyor mu; yeni hata veya risk yaratıyor mu?

Tek bir WER puanı, modelin adli doğruluğunu, kaydın özgünlüğünü veya bilirkişi raporunun yeterliliğini kanıtlamaz. Ürün kabulü; lisans, güvenlik, teknik kalite, uzman denetimi ve iş akışı sonuçlarının birlikte değerlendirilmesini gerektirir.

## 2. Test ilkeleri

- Her aday aynı sabitlenmiş test örneklerinde değerlendirilir.
- Test sesleri, referans metinler, anotasyonlar ve model sonuçları ayrı sürümlenir.
- Model, runtime, model ağırlığı, quantization, parametreler, decoder ve ön işleme zinciri kaydedilir.
- Model seçimi için kullanılan veri, ince ayar/eğitim verisiyle çakışmamalıdır. Konuşmacı ve kayıt oturumu düzeyinde veri sızıntısı kontrol edilir.
- Test kümesi üzerinde model/parametre ayarı yapılmaz. Gerekirse ayrı geliştirme kümesi kullanılır; nihai test kümesi dokunulmadan saklanır.
- Orijinal sesin hash'i alınır; test için üretilen her türev kaynakla ilişkilendirilir.
- Gerçek mahkeme/soruşturma sesleri GitHub'a, CI sistemine, bulut ASR'ye veya izinsiz haricî hizmete gönderilmez.
- İnsan referansı ve uzman düzeltmesi makine çıktısından ayrı tutulur.
- Kabul eşikleri önceden keyfî biçimde belirlenmez; pilot sonuçları, riskler, donanım hedefi ve uzman değerlendirmesi görüldükten sonra karara bağlanır.
- Üretim iş akışında ASR ve diarization çıktıları taslaktır; bilirkişinin inceleme/onay yükümlülüğünü kaldırmaz.

## 3. Test veri kümeleri ve lisans incelemesi

Açık veri kaynaklarının kapsamadığı doğal okuma, serbest konuşma ve aynı miks içinde örtüşen konuşmacı testleri için gönüllü kayıt düzeni, kurgusal Türkçe cümle seti ve kontrollü kayıt koşulları [56.12 Kontrollü Ses Kayıt Protokolü](56-12-kontrollu-ses-kayit-protokolu.md) belgesinde tanımlanmıştır. Henüz gerçek gönüllü kaydı alınmamıştır.

Kaynak bazında güncel inceleme, kısıtlar ve ön kullanım kararları [56.12 Türkçe Test Veri Kümeleri Kaydı](56-12-veri-kumesi-kayitlari.md) belgesinde tutulur. Her indirilen sürüm için [manifest şablonu](56-12-veri-kumesi-manifest-sablonu.json) doldurulur; kaynak sayfasının güncel lisansına erişim anında yeniden bakılır.

### 3.1 İlk araştırmada bulunan kaynaklar

| Kaynak | Konuşma türü / kullanım | Yayımlanan lisans bilgisi | Testte önerilen rol ve sınırlama |
|---|---|---|---|
| Mozilla Common Voice Turkish 27.0 | Gönüllülerin okuduğu Türkçe cümleler | Mozilla Data Collective sayfasında CC0-1.0 | Genel ASR başlangıç testi; okuma konuşması doğal diyalog yerine geçmez. Konuşmacı kimliği çıkarımı yapılmaz. |
| Google FLEURS – tr_tr | Çok dilli, kontrollü/okunmuş konuşma; veri kartında Türkçe train 2.526, validation 338, test 743 örnek | CC BY 4.0 | Temel ASR karşılaştırması için önerilen aday; test split'i sabitlenir, atıf koşulu korunur. |
| MediaSpeech – Türkçe | Kaynak README dört dil için 10'ar saat bildiriyor ve tr yapılandırmasını listeliyor; görünür güncel kart dili/önizlemesi Türkçe alt kümeyi açıkça göstermiyor | Veri kartında CC BY 4.0 | Yayın tarzı konuşma için beklemede; Türkçe erişim ve kaynak medya hakları doğrulanmadan ana test setine alınmaz. |
| Real-TurnTurk | Altı doğal diyalog; altı konuşmacı ve konuşmacı başına izole ses kanalları; zamanlı transkript | Özgün veri kartında Apache 2.0; TurkASR-Bench lisans listesinde farklı kayıt var | Zaman/konuşma sırası için keşifsel kaynak; ayrı kanallar mono diarization testi değildir. Kişi eşleştirmesi ve görsel öznitelikler kullanılmaz. |
| TurkASR-Bench | Yedi kaynaktan 5.200 ifade / 14,7 saat; kaynak ağırlıklı dengeli Türkçe ASR testi | mixed-per-source; her örneğin lisansı kaynak bazında | Hazır karşılaştırma için güçlü aday; erişim koşulları, her alt kümenin lisansı ve referans kalitesi incelenmeden tek bir serbest lisanslı paket gibi kullanılamaz. |

#| Common Voice Spontaneous Speech Turkish 5.0 | Sorulara verilen doğal/serbest yanıtlar; kaynak kartında 54 klip / 13 konuşmacı / 0,28 saat, yalnız 41 doğrulanmış klip | CC0-1.0; konuşmacı kimliğini belirleme ve yeniden barındırma/paylaşma yasak | Doğal tek konuşmacılı konuşma için küçük keşifsel kontrol; split atanmamış ve ana benchmark olamaz. |
| MediaSpeech – Türkçe | Medya konuşması; kaynak README Türkçe yapılandırmasını listeliyor fakat güncel görünür kart/önizleme bunu açıkça göstermiyor | CC BY 4.0 | Türkçe alt küme ve kaynak hakları doğrulanana kadar beklemede. |
| IARPA Babel Turkish | Yaklaşık 213 saat telefon konuşması ve senaryolu telefon konuşması; 8 kHz / 8-bit A-law | LDC üzerinden ücretli ve amaca göre değişen sözleşme | Telefon kalitesi testi için gelecekte ücretli aday. |
| SpeechDataAI Turkish Conversational Speech | Sağlayıcı beyanı: 2.000 saat, 200 konuşmacı, iki kanal | Ticari lisans; ses dosyaları HF üzerinde barındırılmıyor | Yalnız gelecekteki ücretli tedarik seçeneği; numune/sözleşme/rıza doğrulaması gerekir. |
| SesMetin-v2 | TTS ile oluşturulmuş sentetik Türkçe konuşma; telephony/ITN odaklı | Apache 2.0 olarak listelenmiş | Yazılım regresyonu için yardımcı; insan konuşması benchmark'ı değildir. |

## 3.2 Lisans ve veri kökeni uyarıları

- TurkASR-Bench kendi sayfasında erişim için koşulları kabul etmeyi, her örneğin kaynak lisansına uymayı ve konuşmacı kimliğini belirlemeye çalışmamayı ister.
- TurkASR-Bench'in lisans tablosunda Real-TurnTurk için CC BY 4.0 bilgisi görünürken, Real-TurnTurk'ün kendi kaynak kartı Apache 2.0 gösterir. Bu uyuşmazlık açıklığa kavuşmadan bu alt küme için toplulaştırılmış lisans bilgisine dayanılmamalıdır; kaynak veri sahibinin güncel koşulları ayrıca doğrulanmalıdır.
- TurkASR-Bench; CC BY-NC-SA 3.0 lisanslı Khan Academy ve GPL-3.0 olarak listelenen VoxForge gibi farklı koşullardaki alt kümeler içerir. Bu alt kümeler MİHENK'in ticari/yeniden dağıtım senaryosuna otomatik olarak uygun sayılamaz.
- TurkASR-Bench veri kartı, bazı referanslarda olası yazım hatalarının bulunduğunu ve bunların otomatik denetimle işaretlendiğini belirtir. Bu nedenle hazır referanslar uzman kontrolü olmadan mutlak altın standart kabul edilmez.
- Common Voice sürümü değiştikçe veri sürümü ve lisansı yeniden kaydedilir. “Common Voice Türkçe” gibi sürümsüz bir kayıt testin tekrarlanabilirliği için yeterli değildir. Spontaneous Speech Türkçe 5.0 sayfasında train/dev/test atamasının henüz yapılmadığı ve yeniden barındırmanın yasak olduğu belirtilmiştir.
- Açık lisans, ses kaydındaki tüm üçüncü taraf haklarının veya kullanım koşullarının otomatik olarak temizlendiği anlamına gelmez. Her veri kümesi için kaynak, sürüm, lisans metni, erişim koşulu, konuşmacı kısıtları ve amaç uygunluğu kaydedilir.

### 3.3 MİHENK test deposunda neler bulunabilir?

**Public araştırma deposuna:**
- Veri kümesinin adı, kaynak URL'si, sürümü/commit'i ve erişim tarihi.
- Lisans ve kullanım kısıtları özeti.
- İzin verilen örnek kimlikleri veya kamuya açık kaynak referansları.
- SHA-256 manifest şablonu; gerekiyorsa yerel testte hesaplanmış değerler yalnızca veri paylaşımı ve gizlilik incelemesi sonrası.
- Test kodu, normalizasyon kuralları, anotasyon şeması ve sentetik örnekler.
- Sentetik ses örnekleri; yalnızca üretenlerin açık izni ve uygun lisansla.

**Public depoya konulmayacak:**
- Gerçek dava/soruşturma kayıtları, UYAP görüntüleri, taraf/kişi bilgileri veya bilirkişinin vaka materyali.
- İzin koşulu netleşmemiş açık veri kümesi sesleri.
- Lisans incelemesi yapılmamış toplu ses arşivleri.
- Gerçek kayıtların transkriptleri, hash manifestleri, dosya adları veya bunlardan kimlik/olay çıkarılmasını mümkün kılabilecek metadata.

Sesler ve referans transkriptleri gerekiyorsa araştırma deposundan ayrı, şifreli ve erişim kontrollü yerel test alanında tutulur.

## 4. İnsan referans transkripti ve anotasyon protokolü

Türkçe sözcüğü sözcüğüne yazım, belirsizlik, örtüşme, anonim konuşmacı etiketleri ve WER normalizasyonunun ayrıntılı önerisi [56.12 Türkçe Transkripsiyon ve Anotasyon Kuralları](56-12-transkripsiyon-anotasyon-kurallari.md) belgesindedir. Makinece okunur örnek için [anotasyon kaydı şablonu](56-12-anotasyon-kaydi-sablonu.json), [kontrollü ses kayıt protokolü](56-12-kontrollu-ses-kayit-protokolu.md), [motor/runtime uyumluluk araştırması](56-12-motor-runtime-uyumluluk-arastirmasi.md), [yerel benchmark düzeneği tasarımı](56-12-yerel-benchmark-harness-tasarimi.md), [test koşusu JSON şablonu](56-12-test-kosu-kaydi-sablonu.json) kullanılır.

WER/CER için referans metin, model çıktısından bağımsız hazırlanmalıdır.

### 4.1 Referans üretimi

1. Test örneği ve kaynak hash'i kaydedilir.
2. Türkçeyi yeterli düzeyde bilen iki anotatör birbirinden bağımsız dinleyerek transkript hazırlar.
3. Anlaşmazlıklar zaman aralığına bağlanır.
4. İkinci dinleme ve gerekirse üçüncü uzman/adjudikatör incelemesiyle referans karara bağlanır.
5. Duyulmayan bölüm tahminle doldurulmaz; anotasyon şeması içinde belirsiz olarak tutulur.
6. Referans metin sürümlenir; her değişikliğin gerekçesi ve anotatörü kaydedilir.

İki anotatörlü süreç, tüm sesin otomatik olarak açık ve tek anlamlı olduğu varsayımını engeller. Anlaşılamayan konuşmada referans metni zorla oluşturmak yerine belirsizlik işaretlenir ve ilgili aralık ana WER hesabından ayrı raporlanabilir.

### 4.2 Önceden karara bağlanacak anotasyon kuralları

- Sözcüğü sözcüğüne transkripsiyon mu, temizlenmiş transkripsiyon mu?
- Dolgu sesleri, tekrarlar, yarım bırakılan kelimeler ve kendini düzeltmeler nasıl yazılacak?
- Anlaşılmayan bölüm ve kısmen anlaşılan kelime nasıl işaretlenecek?
- Konuşma dışı sesler ve anlamlı vokal tepkiler nasıl gösterilecek?
- Noktalama ve büyük/küçük harf transkriptin parçası mı, ayrı sunum katmanı mı?
- Sayılar rakamla mı yazılacak, sözcükle mi; her iki biçim nasıl karşılaştırılacak?
- Özel adlar, kısaltmalar ve ek almış yabancı kelimeler nasıl normalize edilecek?
- Örtüşen konuşmada aynı zaman aralığında birden fazla konuşmacı metni nasıl gösterilecek?
- Zaman damgası kelime, ifade veya cümle seviyesinde mi tutulacak?

Bu kararlar ölçüm başladıktan sonra geriye dönük değiştirilmemelidir. Gerekirse yeni anotasyon sürümü açılır ve bütün motorlar aynı sürümle yeniden puanlanır.

### 4.3 Türkçe metin normalizasyonu

Tek bir normalizasyon kuralı bütün hataları görünmez hâle getirmemelidir. En az iki raporlama görünümü önerilir:

- **WER-A (yazım/kelime biçimi):** Unicode NFC, Türkçeye uygun küçük harf dönüşümü (I/İ kuralları), boşluk standardizasyonu ve önceden tanımlanmış noktalama politikası. Kelime içi kesme işareti kuralı sabitlenir.
- **WER-B (sayı normalizasyonu):** WER-A kurallarına ek olarak rakam ile sözcükle yazılmış sayıların tutarlı biçime dönüştürülmesi. Sayıların anlamı ve kritik unsur doğruluğu ayrıca ölçülür.
- **CER:** Aynı sabit Unicode/Türkçe normalizasyonuyla karakter düzeyinde hata oranı.
- **Ham metin saklama:** Normalizasyondan önceki referans ve model çıktısı her zaman korunur.

WER formülü:

\[
WER = \frac{S + D + I}{N}
\]

Burada S değiştirme, D silme/atlama, I ekleme, N referans kelime sayısıdır. WER tek bir kayıtta veya alt grupta yüzde 100'ü aşabilir; bu nedenle yalnız “yüzde doğruluk” gibi sunulmaz.

Rapor, toplam kelime havuzunda hesaplanan mikro WER/CER değerlerini, dosya bazında sonuçları ve konuşma türü bazında sonuçları birlikte göstermelidir. Dosya WER değerlerinin basit ortalaması, mikro WER ile aynı değildir.

## 5. Test matrisi

Her test örneği birden fazla etiket taşıyabilir. Veri kümesinin temsil etmediği koşullar sentetik/izinli kontrollü kayıtlarla tamamlanır.

| Boyut | Test sınıfları |
|---|---|
| Konuşma biçimi | Okunmuş metin, doğal monolog, karşılıklı diyalog, hızlı konuşma, yavaş konuşma, kesintili/tereddütlü konuşma |
| Kayıt ortamı | Sessiz oda, yankılı oda, telefon/VoIP, uzak mikrofon, hareketli ortam, yayın kaydı |
| Sinyal kalitesi | Düşük seviye, clipping/distorsiyon, dar bant, kodek sıkıştırması, arka plan müziği/gürültüsü |
| Konuşmacı | Tek kişi, iki kişi, çoklu konuşmacı, kısa araya girme, üst üste konuşma |
| Dilsel zorluk | Özel ad, yer adı, sayı, tarih, saat, kısaltma, olumsuzluk, yabancı terim, ekli kelime, nadir sözcük |
| Konuşma olayı | Fısıltı, bağırma, gülme/ağlama, nefes, sessizlik, yarım kalan ifade |
| Dosya/teknik | Mono/stereo, çok kanal, farklı örnekleme hızları, farklı codec/kapsayıcı, uzun kayıt, bozuk/kesik dosya |
| İş akışı | Tek dosya, çoklu dosya, kuyruk, iptal, çökme sonrası devam, disk alanı dolması |

Test raporu yalnız toplam skoru değil, bu alt gruplardaki hata dağılımını da sunmalıdır. Bir model temiz okuma konuşmasında iyi sonuç verip doğal konuşmada başarısız olabilir; gruplar tek ortalama altında gizlenmemelidir.

## 6. ASR karşılaştırma protokolü

ASR model/runtime uyumluluğu ve ayrı motor görevleri için [56.12 motor/runtime uyumluluk araştırması](56-12-motor-runtime-uyumluluk-arastirmasi.md) temel teknik başvuru belgesidir. whisper.cpp'nin GGML biçimi kullandığı, faster-whisper/CTranslate2'nin farklı model dönüştürme ve compute türleri istediği unutulmamalıdır; GGUF tüm ses modellerine uygulanabilen evrensel biçim değildir.

### 6.1 Adaylar ve çalışma zamanı

İlk aday listesi mevcut ASR araştırma belgesinden alınır:
- Whisper Large v3 ve Turbo.
- TurkMedSTT Whisper Large v3 Türkçe Genel M1.
- ufakzeka-kulak; sherpa-onnx ve Parakeet.cpp GGUF gibi model kartında doğrulanmış dışa aktarımları ayrı koşul olarak.
- Turkish STT 66M v2 (özel lisans metni doğrulanırsa; aksi halde test ENGELLENDİ).
- Uran STT Base (Apache 2.0; yayımlanan WER nedeniyle düşük öncelikli CPU taban çizgisi).
- Vosk Turkish Small (düşük öncelikli; ölçüm verisi sınırlı).

Model ve çalışma zamanı birbirinden ayrı test nesneleridir. Her model yalnız kendi mimarisi tarafından desteklenen, belgelenmiş çalışma zamanında çalıştırılır. TurkMedSTT M1'in Whisper ailesinden olması, doğrudan whisper.cpp ile çalışacağı anlamına gelmez. Uyumlu model biçimi, dönüştürme ve çıktı eşdeğerliği test edilmeden bu varsayım yapılmaz.

GGUF, GGML, ONNX veya başka bir model paketi/çalışma zamanı biçimi genel olarak her model mimarisine uygulanabilir kabul edilmez. Özellikle GGUF dönüşümü, model mimarisi ve kullanılan çıkarım motoru bunu destekliyorsa ayrı bir uyumluluk testi olarak yapılır.

### 6.2 İki ayrı karşılaştırma

Aynı modelin runtime/quantization karşılaştırması ve test koşusu kayıt alanları için [yerel benchmark düzeneği tasarımı](56-12-yerel-benchmark-harness-tasarimi.md) ile [test koşusu JSON şablonu](56-12-test-kosu-kaydi-sablonu.json) referans alınır. RUN-001 senaryosu bu karşılaştırmanın tekrar üretilebilir olmasını kontrol eder.

**A. Model kalite karşılaştırması**
- Her model, belgelenmiş referans çalışma zamanında ve desteklenen önerilen ayarlarda çalıştırılır.
- Aynı kaynak sesler ve aynı insan referansı kullanılır.
- Motorun zorunlu kıldığı ön işleme farklıysa tüm adımlar kayda alınır.
- Model kalitesi ile runtime performansı birbirine karıştırılmaz.

**B. MİHENK dağıtım karşılaştırması**
- Uygulamada gerçekten paketlenebilecek runtime/model sürümü denenir.
- İşletim sistemi, CPU/GPU, bellek, model yükleme, yerel ağsız çalışma ve güncelleme/geri alma ölçülür.
- Nicemlenmiş varyantlar desteklenen temel modelle karşılaştırılır.
- Nicemlemenin WER/CER, kritik kelime hatası ve zaman damgası davranışına etkisi ayrıca raporlanır.

### 6.3 Sabitlenecek parametreler

- Model adı, kaynak deposu, sürüm/commit ve model dosyası checksum.
- Runtime ve kütüphane sürümleri, derleme seçenekleri.
- Dil, görev, beam/search, sıcaklık veya ilgili decoding ayarları.
- VAD, chunking, overlap/context, timestamp seçeneği.
- Ön işleme, kanal, yeniden örnekleme ve ses biçimi.
- CPU thread, batch size ve GPU hızlandırma ayarları.
- Quantization düzeyi ve dosya biçimi.

Ayar değişirse yeni test koşulu/kimliği oluşturulur; önceki sonuçların üstüne yazılmaz.

### 6.4 ASR metrikleri

| Metrik | Ne ölçer? | Raporlama |
|---|---|---|
| WER-A / WER-B | Kelime değiştirme, atlama ve ekleme | Toplam, dosya ve alt grup |
| CER | Karakter düzeyinde fark | Toplam ve alt grup |
| Kritik unsur hata sayısı | Özel ad, sayı, tarih, saat, olumsuzluk, kısaltma | Tür ve örnek bazında; ağırlıklar ayrıca tanımlanır |
| Hallüsinasyon/boşluk hatası | Sessizlikte veya anlaşılmayan bölümde olmayan metin üretimi | Olay sayısı ve süre |
| Atlanan konuşma | Referansta olup modelde bulunmayan bölüm | Kelime/segment ve süre |
| Segment/zaman doğruluğu | Metin segmentinin doğru ses aralığına bağlanması | Başlangıç/bitiş sapması, tolerans dilimleri |
| Düzeltme eforu | Model taslağını onaylı metne dönüştürmek için insan çalışması | Aktif inceleme süresi ve düzeltme sayısı |

Kritik unsur hatalarının tek bir ağırlıklı puanda gizlenmemesi gerekir. Örneğin bir olumsuzluk veya sayı hatası ile sıradan noktalama farkı aynı risk sınıfında değildir.

## 7. Konuşmacı ayrımı (diarization) test protokolü

Diarization ayrı bir test hattıdır; ASR WER'i ile tek metrikte birleştirilmez.

### 7.1 Referans anotasyon

- Her konuşmacıya kayıt içi anonim etiket verilir: Konuşmacı 1, Konuşmacı 2 vb.
- Her konuşma aralığının başlangıç/bitişi ve konuşmacı etiketi anotasyonlanır.
- Üst üste konuşmada aynı anda etkin birden fazla konuşmacı referansta korunur.
- Anlaşmazlıklar uzman incelemesiyle çözülür.
- Kaynakta ayrı kanal varsa kanal bilgisi korunur; mono diarization testine dönüştürüldüyse karışımın nasıl üretildiği kaydedilir.

### 7.2 Metrikler

**DER (Diarization Error Rate)** temel ölçüttür:

\[
DER = \frac{FA + Miss + Confusion}{Total}
\]

- FA: Konuşma olmayan yerde konuşma işaretleme.
- Miss: Gerçek konuşma aralığını kaçırma.
- Confusion: Konuşmacıyı yanlış kümeye atama.
- Total: Referans konuşma süresi.

DER tek başına verilmemeli; FA, Miss ve Confusion bileşenleri de ayrı raporlanmalıdır. pyannote.metrics dokümantasyonu DER'i diarization karşılaştırmasında yaygın temel metrik olarak açıklar; ayrıca sınır çevresinde collar kullanımı ve örtüşen konuşmayı değerlendirme seçeneklerini belirtir.

Önerilen raporlama:
- Ana sonuç: collar 0, örtüşme dahil.
- Duyarlılık karşılaştırması: referans konuşmacı sınırlarının her iki tarafında 250 ms (toplam 500 ms) collar ile.
- Örtüşen konuşma bölgeleri ayrıca dahil ve hariç hesaplanarak farkı görünür kılınır.
- İsteğe bağlı JER, konuşmacı sayısı doğruluğu ve segment bazında hata dökümü.

Bu değerler raporlama varyantlarıdır; MİHENK için evrensel bir kabul eşiği değildir. Farklı collar/overlap ayarıyla yayımlanmış DER değerleri doğrudan karşılaştırılmamalıdır.

### 7.3 Veri kümesi sınırlaması

Real-TurnTurk'te iki katılımcı ayrı kanal kaydettiği için konuşmacı ataması kanal bilgisinden anlaşılabilir; bu, mikrofonların aynı kanalda karıştığı gerçek diarization problemini doğrudan test etmez. İki kanalı birleştirerek sentetik karışım üretilecekse sonuçlar “sentetik karışım” olarak etiketlenir; doğal tek mikrofon/oda kaydıyla eşdeğer kabul edilmez.

Konuşmacı ayrımı hiçbir aşamada gerçek kişi kimliğini, yaşını, cinsiyetini veya biyometrik özelliklerini belirleme testi değildir.

### 7.4 Türkçe kanıt durumu ve kabul ön koşulu

İncelenen açık model kartları ve benchmark açıklamalarında, Türkçe doğal/karışık mono konuşma ve örtüşme için bağımsız insan anotasyonlu diarization başarımı doğrulanamamıştır. pyannote.audio ve sherpa-onnx teknik aday olarak test edilebilir; fakat başka dilde veya ayrı kanallı veride yayımlanan DER sonuçları Türkçe tek-kanal karışık konuşma başarımı olarak sunulamaz.

- Diarization pilot girdisi kontrollü ses protokolündeki ortak miks/mono kayıt olmalıdır; ayrı referans mikrofonları yalnızca insan anotasyonuna yardım eder.
- Referans etiketleri kayıt içinde anonim olmalı; kayıtlar arası kişi eşleştirmesi yapılmamalıdır.
- ECAPA speaker embedding modeli tek başına diarization sistemi sayılmaz; VAD, segmentasyon, clustering ve speaker assignment hattı birlikte sınanmalıdır.
- Türkçe için bağımsız test sonuçları toplanmadan üretim modeli, kabul eşiği veya kullanıcıya güven puanı kararı verilmez.

## 8. VAD ve forced alignment testleri

VAD ve forced alignment ASR'nin kendisi değildir:
- VAD konuşma aralıklarını tahmin eder. Kısa, kısık, fısıltı veya gürültü içindeki konuşmayı dışarıda bırakıp bırakmadığı test edilir. Her çıkarılan kesit kaynak ses ofsetine, padding bilgisine ve türev işlem kaydına bağlanır.
- Forced alignment önceden verilmiş metni sese hizalar. Yanlış metni de hizalayabilir; bu nedenle doğruluk kapısı değildir. Yalnızca uzman tarafından incelenmiş metne zaman önerisi vermek için kullanılabilir.
- Hizalanamayan Türkçe sayı, kısaltma, özel ad ve sözlük dışı karakterler görünür istisna olarak kalır; zorla zaman damgası üretilmez.

Bu işlevlere ait senaryolar [test senaryoları kataloğunda](56-12-test-senaryolari.md) VAD-001, ALIGN-001 ve ALIGN-002 olarak tanımlanmıştır.

## 9. Ses ön işleme ve iyileştirme testleri

Filtreleme, gürültü azaltma, de-reverberation, kanal ayırma, source separation veya time-stretch ASR'nin zorunlu varsayılan adımları yapılmamalıdır. Her yöntem ayrı kontrollü deney olarak ele alınır.

Her deneyde:
1. Orijinal dosya korunur.
2. İşlem çalışma kopyasına uygulanır.
3. Araç/model/sürüm, ayar, işlenen zaman aralığı ve çıktı hash'i kaydedilir.
4. İşlemli çıktı kaynak sesle karşılaştırılarak dinlenir.
5. ASR başarımına etkisi aynı referans ve aynı motorla ölçülür.
6. İstenmeyen artefakt ve dilsel bilgi kaybı ayrıca değerlendirilir.

Sadece WER iyileşti diye işlem kabul edilmez; iyileştirme bir konuşma sesini veya önemli fonetik ayrıntıyı silebilir. Kör dinleme ve orijinalle karşılaştırma uzman değerlendirmesinin parçasıdır. SWGDE'nin dijital ses iyileştirme rehberi, işlemlerin tekrarlanabilir belgelenmesini, girdi/çıktı karşılaştırmasını ve aşırı işlemeden kaçınmayı vurgular.

## 10. Performans, bellek ve kararlılık testleri

### 10.1 Donanım/ortam manifesti

Her koşuda kaydedilecekler:
- İşletim sistemi ve sürüm.
- CPU modeli, çekirdek/thread sayısı.
- Fiziksel RAM.
- GPU modeli, VRAM, sürücü ve hızlandırma arayüzü.
- Güç/performans modu ve test sırasında sıcaklık kısıtlaması varsa bilgi.
- Model dosyası biçimi, boyutu ve checksum.
- Runtime, derleyici/derleme ayarı, thread ve batch ayarları.
- Ses dosyasının süresi, codec'i, kanal sayısı ve örnekleme hızı.

### 10.2 Ölçülecek performans

| Ölçüt | Tanım |
|---|---|
| Model yükleme süresi | Sürecin başlatılmasından ilk işleme hazır olmasına kadar |
| İlk çıktı gecikmesi | İlk segment/metin çıktısına kadar geçen süre |
| Toplam işlem süresi | Dosya veya görev kuyruğunun tamamlanması |
| RTF | İşlem süresi / ses süresi; 1'in altı gerçek zamandan hızlıdır |
| Tepe RAM | İşlem boyunca en yüksek sistem belleği |
| Tepe VRAM | GPU kullanıldığında en yüksek ekran kartı belleği |
| Disk alanı | Model, runtime, cache ve geçici dosyalar |
| Kararlılık | Hata, çökme, kilitlenme, çıktı kaybı ve yeniden başlatma |
| Devam edebilme | Kesinti sonrası tamamlanan işin yeniden işlenmeden korunması |

Soğuk başlatma ve model bellekteyken sıcak çalıştırma ayrı ölçülür. Tek koşu yerine tekrarlı koşular yapılır; medyan ve yüksek yüzdelik (ör. P95) raporlanır. Bir modelin GPU VRAM'i ile sistem RAM'i birbirinin yerine yazılmaz.

### 10.3 Uzun kayıt ve kuyruk testi

- Kısa klip ve uzun tek kayıt ayrı test edilir.
- Yaklaşık 20 dakikalık kayıt testi, B-01'in anlattığı örnek dosya süresini kapsamak amacıyla yer alır; tüm görevler için varsayılan dosya süresi değildir.
- Yaklaşık 160 dakikalık toplam kuyruk testi de B-01'in tek örneğindeki toplam süreyi yeniden üretmek içindir; genel dosya sayısı/süre standardı değildir.
- Gerçek test senaryoları görevlerin ölçülen materyal envanterine göre genişletilir.
- Chunk sınırında kelime atlama/tekrar, timestamp offset, bağlam kopması, sıranın bozulması ve kısmi dosya hatası ayrıca incelenir.
- İşlem iptali, uygulama kapanması, sistem yeniden başlatma ve disk alanı dolması sonrası kurtarma sınanır.

## 11. Güvenlik ve mahremiyet testleri

- Test sırasında ağ erişimi kapatıldığında ASR ve tüm yerel yardımcı işlemler çalışmaya devam edebilmeli.
- Dosyanın dış ağa gönderilmediği ağ/işlem izleme ile doğrulanmalı.
- Model dosyası ve güncelleme paketi checksum/imza doğrulaması olmadan yüklenmemeli.
- Decoder bozuk veya kötü amaçlı medya girdisine karşı sınırlandırılmış süreçte çalışmalı.
- Path traversal, aşırı büyük dosya, metadata/codec saldırıları, geçici dosya sızıntısı ve log içine kişisel veri yazılması test edilmeli.
- Bir görevdeki ses/transkript başka görevde görünmemeli; cache, arama indeksi, geçici klasör ve rapor üretimi dahil kontrol edilmeli.
- Test bittiğinde geçici kopyaların saklama/imha politikası uygulanmalı.
- Kullanım koşulu konuşmacı kimliği tespitini yasaklayan veri kümelerinde, kimliklendirme veya kişi eşleştirme deneyi yapılmamalı.

## 12. Uzman iş akışı ve kullanılabilirlik testi

Test, yalnız motor puanını değil gerçek iş yükünü ölçmelidir.

Aynı görev materyali için mümkünse iki yöntem karşılaştırılır:
- Mevcut manuel yöntem.
- MİHENK'in yerel ASR, zaman bağlantılı metin ve inceleme kuyruğu kullanan yöntemi.

Kaydedilecek ölçümler:
- İlk dosya açılışından transkript taslağına kadar süre.
- Uzman tarafından kontrol edilen toplam ses süresi.
- Aktif dinleme, tekrar dinleme ve düzeltme süresi.
- Düzeltilen kelime/segment sayısı ve hata türü.
- Belirsiz/örtüşen bölümün doğru işaretlenmesi.
- Görevde unutulan/atlanan materyal sayısı.
- Rapor taslağı hazırlama ve son kontrol süresi.
- Uzmanın sistemi kullanırken yaptığı geri alma, tekrar çalıştırma ve manuel iş sayısı.

B-01 tek kullanıcı gözlemidir; ilk kullanılabilirlik geri bildirimi olarak değerlendirilir, genel kullanıcı kabulü veya istatistiksel temsil olarak sunulmaz. Eşikler ve kullanılabilirlik sonucu başka bilirkişilerle doğrulanmalıdır.

## 13. Deney aşamaları

| Aşama | İçerik | Çıkış ölçütü |
|---|---|---|
| 0 – Test düzeneği | Manifest, hash, normalizasyon, puanlayıcı ve log doğrulaması | Aynı girdiyle aynı ölçüm tekrar üretilebiliyor |
| 1 – Temel ASR | Common Voice/FLEURS gibi temiz/okunmuş konuşma kaynakları | İlk model karşılaştırma tablosu |
| 2 – Gerçek konuşma çeşitliliği | Lisansı doğrulanmış diyalog, yayın, telefon/gürültü ve kontrollü sentetik ses | Hata türü ve koşul analizi |
| 3 – Diarization | Anotasyonlu konuşmacı segmentleri, örtüşme ve kanal testleri | DER bileşenleri ve sınırlamalar |
| 4 – Uzun kayıt/performance | 20 dk tek kayıt ve 160 dk çoklu iş kuyruğu gibi B-01 örneğini kapsayan senaryolar | RAM/VRAM/RTF/kararlılık |
| 5 – İş akışı kabulü | Görev açma, inceleme, rapor taslağı, kalite kapısı | Uzman tarafından gözden geçirilmiş kabul raporu |

Bu aşamalar veri kaynaklarının uygunluğu ve test altyapısı hazır oldukça yürütülür. Aşamaların tamamlanması, otomatik transkripsiyonu tek başına nihai rapor üretmeye yetkili kılmaz.

## 14. Kabul kapıları ve karar yöntemi

Aday model/runtime ancak aşağıdaki kapıların tümünden geçerse pilot dağıtım adayı olabilir:

1. **Lisans/veri kökeni:** Kod, model ağırlığı, çalışma zamanı ve test verisi kullanım koşulları belgelenmiş.
2. **Güvenlik:** Ağsız çalışma, dosya erişim sınırı, model checksum ve görev yalıtımı doğrulanmış.
3. **Doğruluk:** WER/CER ve kritik unsur hataları konuşma türü bazında ölçülmüş; referans hataları denetlenmiş.
4. **Belirsizlik:** Sessizlikte uydurma metin, anlaşılmayan bölümü doldurma ve örtüşen konuşma davranışı test edilmiş.
5. **Performans:** Hedef donanımda RAM/VRAM, RTF, uzun kayıt ve kurtarma sonuçları kayıtlı.
6. **Uzman denetimi:** Metni kaynak sesten kontrol etme ve düzeltme iş akışı kullanılabilir bulunmuş.
7. **Rapor/teslim:** Makine taslağı ile uzman onaylı metin ayrılmış; rapor ve ek eşleşmesi kontrol edilmiş.

Şimdilik sayısal WER/DER/RTF veya RAM kabul eşiği belirlenmemiştir. Eşikler; test seti, donanım hedefi, kritik hata riski ve uzman görüşü ortaya çıktıktan sonra karar kaydıyla belirlenecektir. Model sıralaması tek bir ortalama puana indirgenmeyecek; doğruluk, kritik hata, hız, bellek, kararlılık ve lisans ayrı sütunlarda değerlendirilecektir.

## 15. Test raporu şablonu

Her test koşusu şu alanları içermelidir:

- Test kimliği, tarih, sorumlu ve amaç.
- Veri kümesi/sürümü, kaynak lisansı, örnek kimliği ve split.
- Ses hash'i ve referans transkript sürümü/hash'i.
- Anotasyon politikası ve normalizasyon sürümü.
- Model, runtime, ağırlık checksum, quantization ve parametreler.
- Donanım/işletim sistemi manifesti.
- WER-A, WER-B, CER ve kritik unsur hataları.
- Diarization kullanıldıysa DER bileşenleri, collar/overlap ayarları ve JER.
- Zaman damgası sapmaları.
- RTF, yükleme süresi, RAM, VRAM, disk ve hata/kurtarma kayıtları.
- İnsan düzeltme süresi ve uzman değerlendirmesi.
- Bilinen kısıtlar, beklenmeyen durumlar ve karar önerisi.

## 16. Açık kararlar

1. 56.12 için sözcüğü sözcüğüne transkripsiyon ve okunabilir rapor biçimi arasındaki kural.
2. Anotasyon ve belirsiz bölüm gösterim standardı.
3. Hedef minimum/önerilen bilgisayar donanımı.
4. Her veri kümesinin ticari/araştırma/yeniden dağıtım koşullarının hukukî incelemesi.
5. TurkASR-Bench alt kümelerinin kaynak lisansı uyuşmazlıklarının çözümü.
6. Diarization'ın pilot için gerçekten gerekli olup olmadığı ve hangi veriyle sınanacağı.
7. Uzman kabul ölçütleri ve kritik unsur hata toleransları.
8. Whisper.cpp dışındaki model runtime'larının MİHENK paketine dahil edilme koşulları.
9. GGUF/ONNX gibi dönüştürülmüş model biçimlerinin doğruluk ve dağıtım test gereksinimleri.

## 17. Kaynaklar

- [Mozilla Common Voice veri kümesi kataloğu](https://commonvoice.mozilla.org/bas/datasets) – güncel Türkçe veri sürümü ve CC0-1.0 bilgisi.
- [Google FLEURS veri kümesi](https://huggingface.co/datasets/google/fleurs) – tr_tr bölümü ve CC BY 4.0.
- [MediaSpeech veri kartı](https://huggingface.co/datasets/ymoslem/MediaSpeech) – Türkçe medya konuşması, veri tanımı ve CC BY 4.0.
- [Real-TurnTurk veri kartı](https://huggingface.co/datasets/tugrulbayrak/Real-TurnTurk) – iki kanallı doğal diyalog, zaman hizalı transkript ve Apache 2.0.
- [TurkASR-Bench](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench) ve [kaynak lisans dosyası](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench/blob/main/LICENSE.md) – karışık kaynak/lisans, anotasyon normalizasyonu ve veri sınırlamaları.
- [pyannote.metrics – değerlendirme metrikleri](https://pyannote.github.io/pyannote-metrics/reference.html) – DER, konuşma etkinliği, collar ve örtüşme değerlendirmesi.
- [SWGDE 20-A-001 v2.0 – Best Practices for Enhancement of Digital Audio](https://www.swgde.org/documents/published-complete-listing/20-a-001-2/) – 21.08.2025 tarihli nihai onaylı sürüm; tekrarlanabilir işlem belgeleme ve aşırı işlemden kaçınma.

Bu kaynaklar teknik test yöntemini besler; Türkiye'deki bilirkişilik mevzuatının veya Adalet Bakanlığının 56.12 için verdiği resmî onayın yerine geçmez.
