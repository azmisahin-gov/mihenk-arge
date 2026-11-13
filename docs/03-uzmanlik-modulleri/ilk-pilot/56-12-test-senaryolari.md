# 56.12 – Test Senaryoları Kataloğu

> **Durum:** İlk test senaryosu kataloğu; çalıştırma sonucu içermez  
> **Tarih:** 13 Kasım 2026  
> **İlişkili belgeler:** [Uçtan uca teknik iş akışı](56-12-teknik-is-akisi.md), [Test Planı ve Başarı Ölçütleri](56-12-test-plani-ve-basari-olcutleri.md), [Motor/runtime uyumluluk araştırması](56-12-motor-runtime-uyumluluk-arastirmasi.md)

## 1. Amaç ve kullanım

Bu katalog, 56.12 test planındaki genel ölçütleri tekrarlanabilir test senaryolarına dönüştürür. Senaryolar tasarlanmıştır; henüz ASR, diarization veya ses iyileştirme motoru üzerinde çalıştırılmış değildir.

Her senaryonun çalıştırma kaydı ayrı tutulmalıdır. Bir senaryonun “geçti” sayılması için yalnızca işlem tamamlanması yeterli değildir; beklenen güvenlik, izlenebilirlik ve uzman denetimi davranışları da doğrulanmalıdır.

## 2. Öncelik ve veri sınıfları

> **Minimum pilot notu:** Bu katalog geniş regresyon ve ileri araştırma senaryolarını da içerir; 48 senaryonun tamamı ilk sürüm şartı değildir. İlk pilot için yalnızca 12 gruplanmış kabul kapısı zorunludur. Kapsam ve senaryo eşlemesi [56.12 Minimum Sürüm Kapsamı](56-12-minimum-surum-kapsami.md) belgesinde tek kaynak olarak tutulur.

### Öncelik

- **P0 – Kritik:** Orijinal materyal, görev yalıtımı, ağsız çalışma, izlenebilirlik ve uzman onayı.
- **P1 – İlk pilot:** Temel ASR, zaman bağlantılı transkript, uzun kayıt ve rapor akışı.
- **P2 – Koşula bağlı:** Diarization, ses iyileştirme, source separation ve ileri yardımcı modeller.

Bu öncelikler geliştirme sırasını gösterir; bir testin hukuki/mesleki yeterliliğini tanımlamaz.

### İzin verilen test veri sınıfları

- **SENTETİK:** Önceden yazılmış metinlerin, izinli gönüllüler tarafından okunması veya kurgusal diyalogların kaydedilmesi.
- **AÇIK-LİSANSLI:** Kaynağı, sürümü, lisansı ve kullanım koşulları doğrulanmış kamuya açık veri.
- **KONTROLLÜ-PİLOT:** Yalnızca gerekli izin ve veri işleme protokolüyle, yetkili yerel cihazda kullanılan gerçek çalışma materyali. Bu sınıf public CI veya GitHub fixture'ı değildir.

Gerçek dosya, dava bilgisi veya kişi verisi senaryo açıklamasına, test günlüğüne, ekran görüntüsüne veya hata raporuna yazılmaz.

## 3. Senaryo kataloğu

### 3.1 Materyal kabulü ve bütünlük

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| MAT-001 | P0 | Dosya envanteri oluşturma | İçinde farklı uzantı, boyut ve sürelerde sentetik sesler bulunan teslim klasörü | Her dosya ayrı kimlik kazanır; ad, boyut, tür ve teknik metadata kaydedilir; toplamlar kaynakla karşılaştırılabilir. |
| MAT-002 | P0 | Aynı içeriğe sahip yinelenen dosyalar | Farklı adlarla kopyalanmış, hash'i aynı iki sentetik dosya | Yinelenme işaretlenir; dosyalardan hiçbiri otomatik silinmez veya diğerinin yerine geçirilmez. |
| MAT-003 | P0 | Aynı ad, farklı içerik | Aynı dosya adına sahip fakat hash ve içerikleri farklı iki dosya | İki materyal ayrı kimlik alır; ad çakışması görünür uyarı olur. |
| MAT-004 | P0 | Kopyalama doğrulaması | Kontrollü test kaynağı ve hedef klasör | Kaynak/hedef hash eşleşirse kopya doğrulanır; uyuşmazlık varsa dosya doğrulanmış statüsüne geçmez. |
| MAT-005 | P0 | Bozuk veya okunamayan ses | Bilerek bozulmuş sentetik medya dosyası | Decoder hatayı kontrollü biçimde bildirir; işlem günlüğü oluşur; uygulama kapanmaz ve ASR otomatik başlatılmaz. |
| MAT-006 | P1 | Beklenen materyal eksik | Sentetik Görev Profili envanterinde olup teslim klasöründe bulunmayan dosya | Eksik materyal listelenir; görev tamamlandı durumuna geçmez. |

### 3.2 Teknik ses kontrolü ve çalışma kopyaları

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| SES-001 | P0 | Orijinal dosyanın değişmezliği | Hash'i önceden alınmış örnek ses | Oynatma, metadata okuma ve ASR boyunca orijinal hash değişmez; değişim algılanırsa işlem durdurulur/uyarı verilir. |
| SES-002 | P1 | Stereo kanal incelemesi | İki kanalda farklı sentetik konuşma bulunan izinli örnek | Sol/sağ kanal ayrı dinlenebilir; kanal seçimi ve kanal bazlı işlem kayda alınır; orijinal stereo korunur. |
| SES-003 | P1 | Örnekleme/biçim dönüşümü | Motorun gerektirdiği biçimden farklı örnekleme hızında ses | Dönüşüm yalnızca çalışma kopyasında yapılır; giriş/çıkış formatı, parametre ve hash saklanır. |
| SES-004 | P1 | Çok uzun sessizlik | Konuşma öncesi/sonrası sessizlik içeren sentetik kayıt | Süre doğru korunur; sessizlik yanlışlıkla kayıttan atılmaz; zaman damgaları kaymaz. |
| SES-005 | P2 | Gürültü azaltma karşılaştırması | Gürültülü sentetik ses ve kontrollü temiz referans | İşlenmiş sürüm orijinalin yerine geçmez; A/B dinleme ve ASR etkisi raporlanır; artefaktlar not edilir. |
| SES-006 | P2 | Hız değişimi ve pitch davranışı | Konuşma içeren sentetik örnek | Oynatma hızı değişimi özgün dosyayı değiştirmez; pitch koruma seçeneği ve kullanılan yöntem görünür olur. |

### 3.3 ASR ve transkript

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| ASR-001 | P1 | Temiz Türkçe tek konuşmacı | İnsan referansı hazırlanmış, açık lisanslı veya sentetik konuşma | ASR taslak üretir; model/runtime/parametre kaydedilir; metin doğrulanmış olarak işaretlenmez. |
| ASR-002 | P1 | Doğal ve hazırlıksız konuşma | İzinli doğal diyalog veya kontrollü gönüllü kaydı | Dolgu, tekrar ve yarım ifadeler anotasyon politikasına göre korunur; modelin metni kendiliğinden temizlemesi hata olarak raporlanabilir. |
| ASR-003 | P1 | Türkçe özel ad ve ekler | Önceden belirlenmiş sentetik isim/yer adları listesi ve referans | Özel ad ve ek hataları ayrı sınıfta sayılır; sözlük desteği varsa hangi sözlüğün kullanıldığı kaydedilir. |
| ASR-004 | P1 | Sayı, tarih, saat ve olumsuzluk | Kurgusal tarih/saat/sayı ve olumlu-olumsuz cümleler | Ham model metni korunur; WER-A/WER-B ve kritik unsur karşılaştırması ayrı raporlanır. |
| ASR-005 | P0 | Sessizlikte metin üretimi | Konuşmasız, sessizlik ve düşük seviyeli ortam sesi içeren kayıt | Olmayan konuşma üretilmesi tespit edilir; olay süre ve metniyle raporlanır; sessizlik bölümü uzman kontrolüne açılır. |
| ASR-006 | P1 | Fısıltı ve düşük ses | İzinli kontrollü düşük ses/fısıltı kaydı | Çıktı güvenilir varsayılmaz; belirsiz segmentler inceleme kuyruğuna alınır; tahminle kelime tamamlanmaz. |
| ASR-007 | P1 | Gürültü ve yankı | Sentetik veya izinli kontrollü arka plan gürültüsü/yankı | Hata, gürültü sınıfına göre raporlanır; motor başarımı temiz kayıt sonucu ile karıştırılmaz. |
| ASR-008 | P1 | Chunk sınırında konuşma | Uzun konuşma; kesme noktasına yakın kelime ve cümleler | Parçalar arasında kelime atlama/tekrar ve zaman kayması ölçülür; kaynak sesle atlama yapılabilir. |
| ASR-009 | P1 | Uzman düzeltmesi ve sürümleme | ASR taslağı ve referans ses | Düzeltme ham ASR çıktısının üzerine yazılmaz; eski/yeni metin, kullanıcı, zaman ve ses aralığı bağı korunur. |
| ASR-010 | P0 | Model uyuşmazlığı | Aynı kaydı işleyen iki bağımsız aday motor | Sonuçlar ayrı gösterilir; otomatik oy çokluğu veya birleştirme yapılmaz; farklar inceleme listesine girer. |
| ASR-013 | P1 | Qwen3-ASR aile karşılaştırması | Qwen3-ASR-0.6B ve 1.7B'nin ayrı model/runtime koşuları; aynı sabitlenmiş test split'i | WER/CER, kritik hata, yükleme, RAM/VRAM, RTF ve çevrimdışı davranış ayrı raporlanır; Qwen3 ForcedAligner Türkçe desteği olmadığı için zaman hizalaması yaptığı varsayılmaz. |

### 3.4 Konuşmacı ayrımı

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| DIA-001 | P2 | İki konuşmacılı dönüşümlü konuşma | İki anonim konuşmacılı referans anotasyon | Konuşmacı segmentleri anonim etiketlerle üretilir; DER ve bileşenleri hesaplanır. |
| DIA-002 | P2 | Kısa araya girme ve geri bildirim | “Evet”, “hı hı” gibi kısa dönüşlerin bulunduğu kurgusal diyalog | Kısa segmentler ve backchannel hataları ayrıca raporlanır; segmentler otomatik kaybolmaz. |
| DIA-003 | P2 | Üst üste konuşma | Zaman açısından örtüşen iki konuşmacı içeren kontrollü kayıt | Referans ve çıktı örtüşmeyi korur; yanlış tek konuşmacıya indirgeme görünür hata olur. |
| DIA-004 | P2 | Kanalı ayrı kaydedilmiş konuşma | Her konuşmacının ayrı kanalda olduğu veri | Kanal etiketi konuşmacı atamasından ayrıştırılır; bu test mono diarization başarısı olarak raporlanmaz. |
| DIA-005 | P2 | Konuşma boyunca etiket kararlılığı | Aynı iki konuşmacının birçok kez söz aldığı kayıt | Aynı anonim konuşmacı kümesi tutarlı tutulur; etiket değişimi/confusion ölçülür. |
| DIA-006 | P2 | Türkçe karışık mono kayıt üzerinde aday motor doğrulaması | Kontrollü protokole göre iki veya daha fazla gönüllünün aynı miks/mono kayıtta konuştuğu, insan anotasyonlu referans ses; pyannote/sherpa-onnx/NeMo adapter'ı | Modelin Türkçe başarımı varsayılmaz; DER, FA/Miss/Confusion, örtüşme dilimleri, RAM/VRAM ve RTF raporlanır. Lisans/izin eksikse test ENGELLENDİ olur; kayıtlar arası kimlik eşleştirmesi yapılmaz. |

### 3.5 Zaman bağlantısı ve kullanıcı incelemesi

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| ZAM-001 | P1 | Transkript satırından sese gitme | Zaman damgalı transkript | Satıra tıklanınca ilgili ses aralığı açılır; ses konumu ile metin segmenti aynı kaynağa bağlıdır. |
| ZAM-002 | P1 | Ses konumundan transkripte gitme | Oynatma konumu ve segment haritası | Geçerli zaman aralığındaki metin görünür; segment dışı konumda yanlış kelime seçilmez. |
| ZAM-003 | P1 | Segment başlangıç/bitiş sapması | İnsan tarafından zamanlanmış referans anotasyon | Başlangıç/bitiş farkı milisaniye/saniye cinsinden raporlanır; seçilen tolerans dilimleriyle sayılır. |
| ZAM-004 | P0 | Belirsiz aralık gösterimi | İnsan tarafından belirsiz olarak anotasyonlanmış aralık | Belirsizlik açıkça görünür; otomatik tahmin veya sessizce tamamlanmış kelimeye dönüşmez. |

### 3.6 Performans, devam ve güvenlik

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| PERF-001 | P1 | Uzun tek kayıt | Yaklaşık 20 dakikalık sentetik/açık kayıt | RTF, model yükleme, tepe RAM/VRAM ve chunk sınırı hataları ölçülür; 20 dakika genel dosya standardı sayılmaz. |
| PERF-002 | P1 | Çoklu kayıt kuyruğu | B-01 örneğini kapsayan yaklaşık 160 dakikalık toplam sentetik/açık ses | Kuyruk sırası, görev ilerlemesi ve kaynak tüketimi izlenir; 160 dakika genel görev varsayımı değildir. |
| PERF-003 | P1 | Soğuk/sıcak çalışma | Aynı donanımda model kapalıyken ve bellekteyken tekrar | Model yükleme ve inference süreleri ayrı raporlanır; ortalama/medyan ve P95 gösterilir. |
| KUR-001 | P0 | İşlem ortasında uygulama kapanması | Uzun bir test görevi; kapanma kontrollü tetiklenir | Son güvenli kontrol noktası saklanır; tekrar başlatmada tamamlanan segmentler bozulmaz veya iki kez yazılmaz. |
| KUR-002 | P0 | Disk alanı dolması | Kontrollü sınırlı disk alanı | Orijinal dosya korunur; kısmi çıktı tamamlanmış gibi işaretlenmez; hata ve kurtarma talimatı gösterilir. |
| GUV-001 | P0 | Ağ bağlantısı kapalı çalışma | Ağ erişimi engellenmiş test ortamı | Yerel işlem sürer; beklenmedik ağ isteği veya dışa veri aktarımı tespit edilirse test başarısız olur. |
| GUV-002 | P0 | Model checksum uyuşmazlığı | Bilerek değiştirilmiş test model dosyası | Model yüklenmez; hata ve beklenen checksum kaydı gösterilir. |
| GUV-003 | P0 | Bozuk/kötü amaçlı medya girdisi | Test için hazırlanmış geçersiz veya sınır durumundaki dosya | Decoder sınırlandırılmış süreçte hata verir; ana uygulama ve diğer görevler etkilenmez. |
| GUV-004 | P0 | Görevler arası veri yalıtımı | A ve B adlı iki sentetik görev; A'ya özgü işaretleyiciler | A'ya ait ad/metin/dosya/metadata B'nin araması, raporu, cache'i ve çıktısında görünmez. |


### 3.7 VAD, zaman hizalama ve runtime uyumluluğu

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| VAD-001 | P1 | Kısa ve düşük sesli konuşmada VAD sınırı | Uzun sessizlik, fısıltı/kısık ses ve kısa sözler içeren sentetik/kontrollü kayıt | VAD'nin çıkardığı aralıklar kaynak zaman ofseti ve padding ile saklanır; kesilmiş olabilecek konuşma açıkça işaretlenir; VAD çıktısı transkript veya konuşmacı ayrımı sayılmaz. |
| ALIGN-001 | P0 | Yanlış metne forced alignment uygulama | Bilerek hatalı kelime içeren ASR taslağı ve aynı ses | Hizalama motoru zaman önerisi üretse bile metin doğrulanmış sayılmaz; uzman onayı olmadan zaman önerisi rapora kesin delil gibi taşınmaz. |
| ALIGN-002 | P1 | Türkçe sayı/kısaltma/özel ad hizalaması | Sayı, kısaltma, ekli özel ad ve sözlükte olmayan karakterler içeren referans | Hizalanamayan token ve eksik zaman aralığı görünür kalır; MİHENK yanlış bir zaman damgasını zorla üretmez; ham metin korunur. |
| RUN-001 | P1 | Aynı Whisper modelinde runtime/quantization karşılaştırması | Aynı temel model sürümünün desteklenen whisper.cpp GGML ve faster-whisper/CTranslate2 varyantları; aynı sabit test split'i | Model/runtime/build/checksum, compute türü ve parametreler kaydedilir; WER/CER, kritik hata, RAM/VRAM ve RTF karşılaştırılır; whisper.cpp için GGUF uyumluluğu varsayılmaz. |

### 3.8 Düşük kaynak ASR ve model biçimi testleri

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| ASR-011 | P1 | Türkçe 66M streaming ONNX adayını değerlendirme | Turkish STT 66M v2; özel lisans metni ve yerel kullanım hakkı önceden doğrulanmış olmalı | Lisans doğrulanmadıysa test ENGELLENDİ olarak kalır; izin varsa FLEURS ve doğal konuşma alt kümelerinde WER/CER, RTF, tepe RAM ve streaming gecikmesi kaydedilir. |
| ASR-012 | P2 | Uran STT Base CPU taban çizgisi | Apache 2.0 model, CTranslate2 INT8 runtime ve sabit test split'i | Yayımlanmış geliştirici WER'i MİHENK sonucu sayılmaz; aynı referansla WER/CER ve kaynak tüketimi ölçülür; düşük başarı durumunda ana aday yapılmaz. |
| RUN-002 | P2 | Model-özel GGUF dışa aktarımı | ufakzeka-kulak GGUF f32/q8_0 ve Parakeet.cpp; aynı modelin sherpa-onnx INT8 dışa aktarımı | Her dosya yalnız destekleyen runtime'da çalıştırılır; WER/CER, token eşdeğerliği, bellek ve RTF raporlanır; GGUF dosyası whisper.cpp'ye verilmez. |
### 3.9 Rapor ve uçtan uca görev

| Kimlik | Öncelik | Senaryo | Girdi / ön koşul | Beklenen davranış |
|---|---|---|---|---|
| RPR-001 | P1 | Görevden yeni rapor oluşturma | Yalnızca sentetik Görev Profili ve onaylı transkript | Yeni rapor temiz veriden üretilir; eski rapor kopyalanmaz; görev alanları kendi görevine bağlanır. |
| RPR-002 | P0 | Cevaplanmamış soru kontrolü | Görev Profilinde birden fazla soru; bir soru cevapsız bırakılır | Kalite kapısı eksik soruyu gösterir; rapor nihai/tamamlandı durumuna geçmez. |
| RPR-003 | P1 | Ek ve kaynak eşleşmesi | Birden fazla sentetik ses ve transkript eki | Dosya adı, ek sıra numarası ve transkript kaynağı tutarlı olmalıdır; yanlış bağ eşleşme uyarısı üretir. |
| RPR-004 | P0 | Önceki görev verisi sızıntısı | Birbirinden farklı sentetik A ve B görevleri | A'ya özgü yer tutucu, özel isim, tarih ve dosya adı B'nin raporunda bulunmaz. |
| E2E-001 | P1 | Baştan sona sentetik görev | Sentetik görevlendirme, sentetik ses, referans metin ve rapor gereksinimi | Görev açılışı, materyal kabulü, ASR, düzeltme, kalite kontrol ve teslim paketi kesintisiz izlenir; insan onayı noktaları atlanmaz. |

## 4. Her test çalıştırmasında kaydedilecek alanlar

Her test senaryosu için ayrı sonuç kaydı oluşturulur:

- Senaryo kimliği ve sürümü.
- Çalıştırma kimliği, tarih, sorumlu ve ortam.
- Test verisi sınıfı (SENTETİK / AÇIK-LİSANSLI / KONTROLLÜ-PİLOT).
- Veri kümesi sürümü, örnek kimliği ve lisans referansı.
- Girdi dosyası hash'i ve varsa türev hash'leri.
- Model/runtime/parametre/quantization ve checksum bilgisi.
- Beklenen sonuç ve gerçek gözlem.
- Ölçülen metrikler.
- Başarılı/başarısız/engellendi/uygulanamaz durumu.
- Hata kaydı ve yeniden üretim adımları.
- Uzman yorumu ve karar.

Gerçek vaka kimliği, kişi adı, dosya numarası, mahkeme adı veya gerçek dosya yolu test sonucuna yazılmaz. Kontrollü pilotta raporlanan kimlikler takma test kimlikleriyle değiştirilir; gerçek eşleştirme anahtarı ayrı ve korumalı tutulur.

## 5. Başarı durumu sözlüğü

- **GEÇTİ:** Beklenen davranış gözlemlendi ve kanıtı kaydedildi.
- **KALDI:** Beklenen davranış sağlanmadı veya güvenlik/izlenebilirlik ihlali oluştu.
- **ENGELLENDİ:** Lisans, izin, ortam veya veri eksikliği nedeniyle çalıştırılamadı.
- **UYGULANAMAZ:** Senaryo test edilen model/özellik için geçerli değil; gerekçesi kaydedildi.
- **UZMAN KARARI:** Otomatik metrikle sonuçlandırılamayan; bilirkişi değerlendirmesi gereken durum.

“ENGELLENDİ” veya “UYGULANAMAZ” sonuçları geçer sayılmaz; raporda ayrı gösterilir.

## 6. Test kanıtı ve hata raporu

- Ekran görüntüsü alınacaksa yalnızca sentetik/açık lisanslı örnek arayüzü kullanılır.
- Log ve crash dump içinde ses içeriği veya gerçek dosya yolu bulunmamalıdır.
- Hatanın yeniden üretimi için model, parametre ve girdi referansı saklanır; public raporda yalnız paylaşımına izin verilen sentetik girdiler kullanılır.
- Bir testte orijinal hash değişmişse, görevler arası sızıntı olmuşsa veya ağ dışına veri çıktığı gözlenmişse bu kritik olay olarak ele alınır.
- Aynı test tekrar çalıştırıldığında ölçümün hangi koşullarda değiştiği açıklanır; sonuçlar sessizce üzerine yazılmaz.

## 7. İlk yürütme sırası

1. MAT-001–MAT-006 ve SES-001: test alanı, envanter ve orijinal bütünlüğü doğrula.
2. GUV-001–GUV-004 ve KUR-001–KUR-002: güvenlik ve kurtarma zeminini doğrula.
3. ASR-001, ASR-003, ASR-004, ASR-005 ve ZAM-001: temel ASR ve inceleme döngüsünü dene.
4. PERF-001–PERF-003 ve ASR-008: uzun kayıt, chunk ve bellek davranışını değerlendir.
5. DIA-001–DIA-006: veri/anotasyon ve uzman ihtiyacı doğrulanırsa çalıştır.
6. SES-005–SES-006: ses iyileştirme ve oynatma yardımcılarını ayrı deney olarak değerlendir.
7. RPR-001–RPR-004 ve E2E-001: uçtan uca uzman kabulünü dene.

İlk yürütmede sayısal performans veya doğruluk eşiği icat edilmez; ölçümler toplanır ve karar kaydına girdi sağlar. Güvenlik ve orijinal bütünlük senaryoları için toleranssız beklenti uygulanır.

- [ ] Forced alignment'ın yalnızca zaman önerisi olduğu ve metni doğrulamadığı davranışı test et.
- [ ] VAD'nin kısa/düşük sesli konuşmayı kesme sınırlarını ölç.
- [ ] whisper.cpp GGML ile faster-whisper/CTranslate2 runtime karşılaştırmasını sabit model/test koşulunda yap.

## 8. Açık işler

- [ ] Türkçe transkripsiyon anotasyon kurallarını uzman değerlendirmesiyle kesinleştir.
- [ ] Açık veri kümelerinin güncel lisans ve erişim koşullarını kayda al.
- [ ] Test verisi/split manifest şemasını oluştur.
- [ ] Sentetik test metinlerini ve kayıt talimatlarını hazırla.
- [ ] İnsan referans anotasyon sürecini ve uzlaşma yöntemini doğrula.
- [ ] Test koşuları için donanım profillerini belirle.
- [ ] ASR ve diarization motorlarını yalnızca veri ve runtime koşulları netleşince çalıştır.

Bu katalog, testlerin kapsamını tanımlar; hiçbir motorun başarıyla test edildiği veya 56.12 için kabul edildiği anlamına gelmez.
