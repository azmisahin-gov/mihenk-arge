# 56.12 – Ses Kayıtlarının Metin Hâline Dönüştürülmesi: Uçtan Uca Teknik İş Akışı

> **Durum:** İlk ürün/teknik iş akışı taslağı; uzman ve hukuk incelemesi bekliyor  
> **Tarih:** 13 Kasım 2026  
> **Kapsam:** 56.12 ses kayıtlarının metin hâline dönüştürülmesi  
> **Kapsam dışı:** Ses kaydının özgünlüğü/manipülasyonu, adli ses karşılaştırması, konuşmacı kimliklendirmesi ve görüntü incelemesi

## 1. Amaç ve sınırlar

Bu belge, MİHENK 56.12 modülünün görevlendirmeden rapor ve teslim hazırlığına kadar izleyeceği teknik iş akışını tanımlar. Belge bir ürün tasarımı ve araştırma çıktısıdır; bilirkişinin mesleki yönteminin, mevzuatın veya yetkili makam talimatının yerine geçmez.

Adalet Bakanlığının 22 Ocak 2026 tarihli Bilirkişilik Temel ve Alt Uzmanlık Alanları belgesinde 56.12, “Ses Kayıtlarının Metin Hâline Dönüştürülmesi” olarak tanımlanır ve yargı mercilerince Ses ve Görüntü Bilişim Sisteminin kullanılması istisna tutulur. 56.11 “Adli Ses ve Görüntü İnceleme ve Çözümlemeleri” ayrı bir alt uzmanlık alanıdır. MİHENK bu sınırı ürün içinde görünür tutmalıdır.

### 1.1 Tasarım ilkeleri

1. **Önce delil, sonra kolaylık:** Orijinal materyal değiştirilemez; bütün işlemler türev çalışma kopyalarında yapılır.
2. **İzlenebilirlik:** Her çıktı kaynak materyale, işleme, araç/model sürümüne ve parametrelere bağlanır.
3. **Uzman denetimi:** ASR ve diarization çıktıları taslaktır; doğrulanmış bilirkişi bulgusu olarak sunulamaz.
4. **Belirsizliği koruma:** Duyulmayan veya ayırt edilemeyen bölüm tahminle tamamlanmaz.
5. **Göreve özgülük:** Süre, nüsha, format, rapor soruları, teslim ve iade koşulları her Görev Profilinden alınır; örnek dosyadan genellenmez.
6. **Yerel/çevrimdışı çalışma:** Vaka materyali varsayılan olarak cihaz dışına çıkarılmaz. Bulut servisine gönderim bu tasarımın parçası değildir.
7. **Tek uygulama deneyimi:** Kullanıcı ayrı ses araçlarını kurup yönetmez; MİHENK içindeki yetkili işlevleri kullanır.
8. **Ayrı uzmanlık sınırları:** Konuşmacı etiketi, kişinin kimliğini göstermez. Kimlik tespiti, ses karşılaştırması veya özgünlük incelemesi otomatik 56.12 işlevi değildir.

## 2. Aktörler ve sistem bileşenleri

| Aktör/bileşen | Sorumluluk |
|---|---|
| Bilirkişi | Materyali teslim alma, dinleme, metni doğrulama/düzeltme, belirsizlikleri değerlendirme, raporu onaylama ve resmî teslim |
| MİHENK ortak çekirdeği | Görev, dosya, izin, sürüm, işlem günlüğü, güvenli depolama, rapor ve paket yönetimi |
| 56.12 modülü | Ses envanteri, oynatma, ASR iş akışı, zaman bağlantılı transkript, inceleme kuyruğu ve rapor girdileri |
| Ses çözümleme motorları | Dosya okuma, codec çözme, kanal/süre/örnekleme bilgisi çıkarma ve kontrollü türev üretme |
| ASR motoru | Konuşma metni taslağı ve destekliyorsa zaman hizası üretme |
| Diarization motoru | İsteğe bağlı konuşmacı segmentleri/anonim konuşmacı etiketleri üretme |
| Belge/rapor motoru | Görev verileri ve uzman tarafından onaylanan sonuçlardan yeni rapor taslağı üretme |
| Resmî UYAP araçları | Yetkili kullanıcı tarafından resmî belge açma, imzalama ve portal işlemleri |

Motorlar uygulamanın içinde yönetilen yerel kütüphane veya izole worker olabilir. Bu iç uygulama kararı kullanıcıya ayrı uygulama/kurulum yükü getirmemelidir.

## 3. Uçtan uca iş akışı

### Aşama 0 – Görevlendirmeyi alma

**Girdi**
- Görevlendirme belgesi ve varsa ek talimatlar.
- Görevlendirme/tebliğ tarihleri ve teslim koşulları.
- Mahkeme/merci, dosya referansı, taraf/kişi bilgileri ve sorular.

**İşlem**
- Belgeyi güvenli alana kaydet.
- Metin çıkarımı/OCR ile alanları öneri olarak belirle.
- Her alanı kaynak belgedeki sayfa ve konumuna bağla.
- Belirsiz, çelişkili veya okunamayan alanları istisna kuyruğuna al.

**Çıktı**
- Kaynak belge kaydı.
- Görev Profili taslağı.
- Alan bazında kaynak izi ve güven/inceleme durumu.

**Kontrol kapısı**
- Bilirkişi kapsamı, soruları, süre başlangıcı, teslim biçimi ve özel talimatları onaylamadan iş akışı materyal işleme aşamasına geçmez.

### Aşama 1 – Görev Profilini kesinleştirme

Görev Profili en az şu bilgileri taşımalıdır:
- Görevlendirme mercii ve görev referansı.
- İnceleme kapsamı ve açıkça kapsam dışı tutulan hususlar.
- Cevaplanacak sorular ve beklenen çıktı.
- Materyal türleri ve beklenen materyal listesi.
- Süre, başlangıç tetikleyicisi ve son tarih.
- Rapor şablonu, çıktı biçimi, nüsha ve teslim yöntemi.
- İade edilecek fiziksel/dijital materyaller ve iade koşulları.
- İmza ve resmî portal adımları.
- Özel güvenlik veya erişim kısıtları.

**Kural:** Eksik alanlar otomatik varsayımla doldurulmaz. Görev belgesinde yer almayan kural, başka bir dosyadan kopyalanmaz.

### Aşama 2 – Materyali teslim alma ve güvenli içe aktarma

**Girdi**
- USB/disk veya izin verilen dijital teslim kaynağı.
- Teslim tutanağı ve varsa materyal listesi.

**İşlem**
1. Teslim anını, teslim eden/alan rolünü ve fiziksel paket durumunu kaydet.
2. Mümkün olduğunda yazma korumalı okuyucu veya uygun yazma engelleme kullan.
3. Kaynağın dosya sistemini değiştirmeden envanter al.
4. Dosyaları MİHENK'in görev alanına kopyala.
5. Kaynak ve alınan kopya için SHA-256 gibi güçlü hash değerleri hesapla; kopya doğrulamasını kaydet.
6. Kaynak medya, klasör yapısı, dosya adları, boyutlar, zaman damgaları ve kopyalama hatalarını kaydet.
7. Kaynak medyayı ve dijital kopyayı birbirinden ayrı varlıklar olarak ilişkilendir.

**Çıktı**
- Materyal kabul kaydı.
- Dosya envanteri.
- Hash ve kopyalama doğrulama raporu.
- Kaynak medya ile çalışma kopyası arasındaki ilişki.

**Kontrol kapısı**
- Okunamayan, beklenmeyen, şifreli, bozuk veya zararlı olabilecek dosya otomatik çalıştırılmaz; karantinaya alınır veya uzman incelemesine yönlendirilir.

**Önemli sınır:** Hash, MİHENK'in teslim aldığı andaki dosya durumunun bütünlüğünü ve sonraki kopya ilişkisini kontrol etmeye yarar. Dosyanın teslimden önceki kökenini veya içeriğinin gerçekliğini tek başına kanıtlamaz.

### Aşama 3 – Ses dosyası envanteri ve teknik ön inceleme

Her ses dosyası için mümkün olduğunda:
- Dosya adı, boyutu, kapsayıcı ve codec.
- Süre, kanal sayısı ve kanal düzeni.
- Örnekleme hızı ve bit derinliği.
- Kodlama/bit hızı.
- Metadata ve zaman damgaları.
- Okunabilirlik, bozuk başlık, beklenmeyen sonlanma ve sessizlik.
- Dosyanın hash değeri ve kaynak medya ilişkisi.

**İşlem**
- Dosyayı güvenli, sınırlandırılmış decoder sürecinde aç.
- Desteklenen biçimlerde metadata çıkar.
- Oynatma/çözme hatalarını kaydet.
- Dosya süresi ve görev materyal listesi arasında fark varsa uyarı üret.
- Aynı adlı veya aynı hash değerli dosyaları işaretle; otomatik silme/birleştirme yapma.

**Çıktı**
- Ses envanteri ve teknik özellikler.
- İşlenebilir/istisna durumları.
- Eksik veya beklenmeyen materyal listesi.

### Aşama 4 – Orijinal ve çalışma kopyası yönetimi

- Orijinal alınan dosya salt okunur saklanır.
- Oynatma ve ASR için gerekiyorsa türev çalışma kopyası üretilir.
- Kanal ayırma, yeniden örnekleme, biçim dönüştürme, ses düzeyi değişimi veya filtreleme gibi işlemler yalnızca türevde yapılır.
- Her türev; kaynak hash, işlem kimliği, araç/sürüm, ayarlar, tarih ve çıktı hash değerine bağlanır.
- Orijinal ve türev arayüzde açıkça ayırt edilir.
- Dönüştürme gerekiyorsa mümkün olduğunca gereksiz yeniden kodlama/örnekleme değişikliğinden kaçınılır; zorunlu dönüşümün parametreleri belgelenir.

### Aşama 5 – Ses çalışma alanı

Tek MİHENK arayüzünde şu işlevler sağlanır:
- Oynat/duraklat, ileri/geri sarma ve zaman konumuna gitme.
- Dalga biçimi ve zaman çizgisi.
- Kanal seçimi ve kanalları ayrı dinleme.
- Bölüm/olay işaretleme ve not ekleme.
- Seçili aralığı tekrar dinleme.
- Kontrollü oynatma hızı; hız değişimi ve pitch koruma davranışı görünür olmalı.
- Transkript satırından ses konumuna, ses konumundan transkript satırına geçiş.
- Klavye kısayolları ve erişilebilir oynatma kontrolleri.

**Kural:** Oynatma hızı değişimi, filtreleme veya başka ses işleme işlemi orijinal dosyayı değiştirmez. İşlemli ses çıktısı gerekiyorsa ayrı türev olarak kaydedilir.

### Aşama 6 – ASR ile ilk metin taslağı

**Girdi**
- Uzman tarafından seçilen ses kaydı veya bölüm.
- Model, runtime ve parametre sürümü.

**İşlem**
1. Yerel ASR motoru başlatılır.
2. Model/runtime checksum ve konfigürasyonu doğrulanır.
3. Kayıt, motorun desteklediği biçim ve örnekleme koşullarında işlenir.
4. Metin, segmentler ve destekleniyorsa zaman damgaları üretilir.
5. Sessizlikte metin üretimi, anormal tekrar, kesilme ve işleme hataları işaretlenir.
6. Ham model çıktısı değiştirilemez biçimde saklanır; insan düzeltmesi ayrı sürüm olarak tutulur.

**Çıktı**
- ASR ham taslağı.
- Segment/zaman bilgileri.
- Model ve işlem kaydı.
- İnceleme gerektiren segmentler.

**Kontrol kapısı**
- ASR çıktısı hiçbir zaman otomatik olarak “doğrulanmış transkript” statüsüne yükselmez.
- Model güven puanı veya birden çok modelin aynı kelimeyi üretmesi, insan dinlemesinin yerine geçmez.

### Aşama 7 – Konuşmacı ayrımı (isteğe bağlı)

Diarization yalnızca görev için yararlıysa ve kayıt niteliği elveriyorsa çalıştırılır.

**İşlem**
- Konuşma segmentleri anonim etiketlerle ayrılır: “Konuşmacı 1”, “Konuşmacı 2” vb.
- Etiketlerin kayıt boyunca tutarlılığı kontrol edilir.
- Üst üste konuşma, kısa söz, gürültü veya düşük kalite nedeniyle belirsiz kalan aralıklar işaretlenir.
- Bilirkişi gerektiğinde segmentleri elle düzeltir.

**Çıktı**
- Anonim konuşmacı etiketleri ve zaman aralıkları.
- Belirsiz/örtüşen konuşma işaretleri.
- Model ve parametre kaydı.

**Sınırlar**
- Diarization, konuşmacının gerçek kimliğini belirlemez.
- Yaş, cinsiyet, kimlik veya biyometrik özellik çıkarımı yapılmaz.
- Kaynakları birbirinden ayırma (source separation) diarization ile aynı işlem değildir; ayrı bir ihtiyaç ve doğrulama gerektirir.
- Konuşmacı karşılaştırması/kimliklendirmesi bu modülün otomatik işlevi değildir.

### Aşama 8 – Bilirkişi dinleme, düzeltme ve doğrulama

Bu, 56.12 iş akışının temel insan denetimi aşamasıdır.

**Arayüz**
- Bir tarafta ses oynatma ve dalga biçimi, diğer tarafta zaman bağlantılı transkript.
- Seçili kelime/segment için tekrar dinleme.
- Metin düzeltme, konuşmacı etiketi düzenleme ve not.
- Belirsizlik, anlaşılmayan bölüm, üst üste konuşma ve ses dışı olay için açık işaretler.
- Her düzeltmenin önceki metin ve kaynak zaman aralığıyla ilişkisi.

**Önerilen durumlar**
- Makine taslağı.
- İnceleme bekliyor.
- Uzman tarafından kontrol edildi.
- Belirsiz/anlaşılamadı.
- Yeniden dinleme gerekli.
- Uzman tarafından dışlandı (gerekçe zorunlu).

**Kural**
- Anlaşılmayan kelime tahmin edilerek yazılmaz.
- Noktalama ve yazım normalizasyonu, duyulan kelimenin içeriğini değiştirmemelidir.
- Önemli düzeltmeler ve belirsizlik kararları işlem günlüğünde izlenebilir olmalıdır.
- Uzman, transkriptin tamamını ve kritik bölümleri kaynak sesle karşılaştırabilmelidir.

### Aşama 9 – Kalite kontrol ve görev sorularına bağlama

MİHENK otomatik kontrolleri:
- Görevdeki her ses dosyası için bir sonuç veya gerekçeli istisna var mı?
- Transkript segmentleri kaynak ses zaman aralığına bağlı mı?
- Boş zaman aralıkları, çakışan segmentler ve süre dışı zaman damgaları var mı?
- Konuşmacı etiketleri tutarlı mı?
- “Anlaşılamadı” ve örtüşen konuşma işaretleri korunmuş mu?
- ASR ham çıktısı ve uzman tarafından onaylanmış metin ayrı mı?
- Rapor sorularının her biri için uzman tarafından hazırlanmış yanıt/sonuç alanı var mı?
- Rapor ekleri ve materyal listesi görevle tutarlı mı?

Otomatik kontrol, bilirkişinin teknik kanaatini üretmez. Çelişkiyi gösterir ve karar için uzmana sunar.

### Aşama 10 – Rapor taslağı ve ekler

Rapor yeni görev verisi ve onaylı şablondan oluşturulur; eski dosyanın raporu kopyalanıp alanları değiştirilmez.

Görev koşullarına göre rapor taslağında bulunabilecek bölümler:
- Görevlendirme ve inceleme konusu.
- İnceleme kapsamı ve cevaplanacak sorular.
- Teslim alınan materyal ve dosya envanteri.
- Kullanılan araçlar, sürümler ve yöntemler.
- Dosya biçimi ve gerekli teknik özellikler.
- Yapılan transkripsiyon ve kontrol yöntemi.
- Belirsiz/anlaşılamayan/örtüşen bölümler.
- Görev sorularına ilişkin bilirkişi açıklamaları ve sonuçları.
- Sınırlılıklar.
- Ekler ve materyal listesi.

**Kural:** LLM kullanılırsa yalnızca uzman tarafından onaylanmış verilerden biçimlendirme, alan eşleme, eksik alan uyarısı veya dil kontrolü gibi sınırlı görevlerde yararlanabilir. Duyulmayan konuşmayı tamamlama, delilden sonuç çıkarma veya bilirkişi kanaati üretme yetkisi verilmez. LLM çıktısı da insan incelemesinden geçmeden rapora kesin bulgu olarak giremez.

### Aşama 11 – Son kontrol, teslim paketi ve resmî işlem

**Son kontrol**
- Görev Profili ile rapor başlıkları ve soruları karşılaştırılır.
- Dosya adları, tarih, dosya referansı, ek listesi ve nüsha koşulları kontrol edilir.
- Görev için gerekli çıktı biçimi ve sayfa düzeni doğrulanır.
- Raporun son sürümü ve ekleri hash ile kayıt altına alınır.
- İmzalı belge değişikliğinin imzayı geçersiz kılabileceği dikkate alınır.

**Teslim paketi**
- Görev için gerekli rapor biçimi.
- Görevde istenen ekler ve transkript.
- Materyal/çıktı listesi.
- Gerekli işlem ve bütünlük kayıtları.
- İade edilecek fiziksel/dijital materyal listesi.

UYAP Doküman Editörü, Adalet e-İmza ve Bilirkişi Portalı gibi resmî araçlarla yapılacak imza ve portal işlemleri yetkili bilirkişi tarafından yürütülür. MİHENK yetkisiz API, scraping veya portal otomasyonu yapmaz; resmî dağıtım/lisans izni doğrulanmadan bu yazılımları kendi kurulum paketine dahil etmez.

**Kapanış**
- Uzman nihai raporu onaylar.
- Resmî imza ve gönderim adımlarını kendisi tamamlar.
- Teslim tarihi, kanal, alındı bilgisi ve varsa iade işlemi görev kaydına işlenir.
- Görev arşivleme ve saklama politikası uygulanır.

## 4. İstisna ve durdurma koşulları

| Durum | MİHENK davranışı |
|---|---|
| Dosya okunamıyor/bozuk | ASR başlatma; hata ve dosya kimliğini kaydet; uzman incelemesine al |
| Beklenen materyal eksik | Görev kontrolünü durdur; eksik materyali bildir |
| Hash/kopya doğrulaması başarısız | Dosyayı doğrulanmış kabul etme; yeniden alma veya uzman kararı iste |
| Bilinmeyen codec/şifreleme | Otomatik dönüştürme denemelerini sınırla; uzman onayı olmadan haricî codec indirme |
| Çok düşük ses/yoğun gürültü | ASR sonucunu düşük güvenli taslak olarak işaretle; uzman dinlemesine yönlendir |
| Üst üste konuşma | Segmentleri örtüşme olarak işaretle; otomatik kaynak ayrımını kesin sonuç gibi sunma |
| Modeller farklı metin üretiyor | Oy çokluğu ile karar verme; farklılıkları dinleme kuyruğuna al |
| Süre/format/teslim şartı çelişkili | Görev Profilini kesinleştirme; uzman açıklaması iste |
| LLM servis/modeli kullanılamıyor | LLM olmadan temel iş akışına devam et |
| İşlem yarıda kesiliyor | Son güvenli noktayı kaydet; orijinali koru; tekrar başlatılabilir görev oluştur |

## 5. Temel veri nesneleri

- **Görev:** Görevlendirme, kapsam, tarihler, sorular ve teslim koşulları.
- **Materyal:** Fiziksel kaynak veya dijital teslim nesnesi.
- **Dosya:** Materyalin içindeki her dosyanın kimliği, hash'i ve metadata'sı.
- **Türev:** Kaynak dosyadan belirli işlemle üretilen çalışma kopyası.
- **İşlem:** Araç/model sürümü, parametre, zaman ve çıktı ilişkisi.
- **Transkript:** Ham ASR, uzman taslağı ve onaylı sürümler.
- **Segment:** Başlangıç/bitiş zamanı, metin, kanal, anonim konuşmacı ve inceleme durumu.
- **Düzeltme olayı:** Önceki değer, yeni değer, kaynak zaman aralığı, kullanıcı ve tarih.
- **Rapor sürümü:** Görev verileri ve onaylı bulgularla üretilmiş rapor.
- **Teslim paketi:** Rapor, ekler, çıktı hash'leri ve teslim kayıtları.

## 6. İşlem günlüğü için asgari alanlar

Her önemli olayda:
- Görev ve materyal kimliği.
- Kaynak dosya hash'i ve varsa türev hash'i.
- İşlem türü ve işlem kimliği.
- Araç/model/runtime adı ve sürümü.
- Model dosyası checksum ve lisans envanteri referansı.
- Parametreler ve ön işleme adımları.
- Başlangıç/bitiş zamanı ve işlem sonucu.
- Hata/uyarı kodu.
- İnsan müdahalesi, karar ve gerekçe.
- Olay öncesi/sonrası nesne sürümü.

Günlük, sonradan sessizce değiştirilebilir bir metin dosyası olarak tasarlanmamalı; erişim denetimi, bütünlük koruması ve yedekleme politikası olmalıdır.

## 7. İlk sürüm için kapsam önceliği

### İlk sürümde gerekli
- Görev Profili ve materyal envanteri.
- Güvenli dosya kabulü, hash ve orijinal/türev ayrımı.
- Yaygın ses biçimlerini yerel oynatma ve teknik metadata.
- Dalga biçimi, zaman çizgisi ve bölüm tekrar dinleme.
- Yerel ASR çalıştırma ve ham çıktıyı saklama.
- Zaman bağlantılı transkript düzeltme ve uzman kontrolü.
- İşlem günlüğü ve rapor taslağı.
- Görev bazlı son kontrol ve teslim paketi.

### Test sonucuna göre eklenecek
- Diarization.
- Otomatik kanal seçimi.
- Gürültü azaltma ve de-reverberation.
- Pitch korumalı time-stretch.
- Üst üste konuşma için source separation.
- LLM ile sınırlı rapor alan eşleme/kalite yardımı.
- Embedding tabanlı arama.

### Bu modülün dışında
- Ses kaydı özgünlük/manipülasyon incelemesi.
- Konuşmacı kimlik tespiti veya biyometrik ses karşılaştırması.
- Ses kaydından kişinin yaşı, cinsiyeti veya kimliğini çıkarma.
- Bilirkişi yerine nihai kanaat üretme.
- Yetkisiz UYAP/portal otomasyonu.

## 8. Açık kararlar

1. B-01 ve başka 56.12 uzmanlarıyla gerçek iş akışı doğrulaması.
2. Desteklenecek ses kapsayıcı/codec listesi ve lisans/güvenlik incelemesi.
3. ASR runtime/model kombinasyonlarının donanım testleri.
4. Zaman damgası hassasiyeti ve transkript segmentleme yaklaşımı.
5. Diarization'ın 56.12 görevlerinde hangi koşullarda gerekli olduğu.
6. Raporun standart bölümleri ve görev bazında değişen alanları.
7. Saklama, imha, yedekleme ve erişim politikalarının hukuk/güvenlik incelemesi.
8. UDF ve diğer çıktı biçimlerinin güncel UYAP Editörü ile uyumluluk testi.

## 9. Kaynaklar ve yorum sınırı

- [Adalet Bakanlığı – Bilirkişilik Temel ve Alt Uzmanlık Alanları (22.01.2026)](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirki%C5%9Filik%20Temel%20ve%20Alt%20Uzmanl%C4%B1k%20Alanlar%C4%B1%20ile%20Bilirki%C5%9Filerde%20Aranan%20Nitelikler.pdf)
- [SWGDE 08-A-001 v2.5 – Best Practices for Forensic Audio (09.06.2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE 20-A-001 v2.0 – Best Practices for Enhancement of Digital Audio (21.08.2025)](https://www.swgde.org/documents/published-complete-listing/20-a-001-2/)

SWGDE belgeleri ABD merkezli teknik iyi uygulama rehberleridir; Türkiye mevzuatı veya 56.12 için bağlayıcı usul olarak sunulmaz. Burada delil kabulü, materyal koruma, işlem belgeleme, dönüşüm sınırlaması ve ses iyileştirmenin sınırlılıkları gibi teknik tasarım ilkelerini değerlendirmek için kullanılır. Nihai iş akışı Türk mevzuatı, mahkeme talimatları ve alan uzmanlarının görüşüyle doğrulanmalıdır.
