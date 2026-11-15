# MİHENK — Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0

> **Durum:** Sistem mimarisi referansı v1.0. Görsel/ürün tasarımı olarak Wireframe v0.5, proje sahibi tarafından 15.11.2026'da kabul edilmiştir; uygulama ve pilot kabul testleri sürer.  
> **Tarih:** 15 Kasım 2026  
> **İlk teslimat:** 56.12 — Ses Kayıtlarının Metne Dönüştürülmesi kontrollü bilirkişi pilotu  
> **Uzun vadeli hedef:** Ortak çekirdek ve birbirinden ayrılmış uzmanlık modülleriyle MİHENK platformu.

## 0. Bu belgenin rolü

Bu belge, MİHENK'in yalnızca ekranlarını değil, kullanıcının gördüğü işlevler ile arka planda çalışan sistemlerin tamamının sorumluluk sınırlarını tanımlar. Wireframe v0.5 ve uygulama eşlemesi için ana ürün/sistem referansıdır.

Bu belge:
- Bilirkişinin yapmaya çalıştığı işi, MİHENK'in otomatik yaptığı işleri ve bilirkişinin karar vermesi gereken noktaları ayırır.
- Profil, uzmanlık alanı, uzmanlık modülü, görevlendirme, yerel kasa ve uygulama ayarlarını birbirinden ayırır.
- Yerel ASR'nin nerede yönetileceğini ve görev içinde nasıl kullanılacağını tanımlar.
- Bir görevlendirmeden tek, bütünlüklü ve önizlenebilir rapora giden akışı tanımlar.
- Normal, boş, hata, çevrimdışı, kurtarma ve istisna durumlarını ekran tasarımının parçası kabul eder.
- Mevzuatla sabit olan gereklilikleri, teknik en iyi uygulamaları ve MİHENK ürün önerilerini birbirinden ayırır.

Bu belge bir hukuk görüşü, bilirkişi meslekî yöntem talimatı veya uzman kabul raporu değildir. Rapor içeriği ve teknik kanaat her zaman görevlendirmenin kapsamı ve bilirkişinin meslekî değerlendirmesiyle sınırlıdır.

## 1. Sabit ürün yönü ve temel ilkeler

### 1.1 İlk teslimat ve platform hedefi

- İlk kullanılabilir ürün teslimatı 56.12 kontrollü bilirkişi pilotudur.
- MİHENK yalnızca transkript üreten küçük bir araç değildir. Görevlendirme belgesinden başlayıp materyal envanteri, ses incelemesi, soru-cevap, bulgu ve tek rapora uzanan çalışma ortamıdır.
- Uzun vadede başka uzmanlık modülleri aynı ortak çekirdeğe eklenebilir. İlk sürümde hazır olmayan uzmanlık modülleri varmış gibi gösterilmez.
- İlk sürüm varsayımı bir yerel kasa ve bir gerçek kişi bilirkişi profilidir. Çok kullanıcılı/çok profilli yerel oturum bu sürümde vaat edilmez.

### 1.2 Kullanıcı açısından ana ilke

**Kullanıcının ana işi görevlendirmedir; motor, dosya dönüştürücü veya model yönetimi değildir.**

Bilirkişi:
1. MİHENK'i açar ve yerel kasasını kullanıma hazırlar.
2. Bilirkişi profilini ve kendi uzmanlık alanlarını bir kez tanımlar.
3. Yeni görevlendirme belgesini ekler.
4. MİHENK'in çıkardığı görev profilinde yalnız belirsiz, çelişkili veya eksik alanları çözer.
5. Aynı göreve ait materyalleri inceler.
6. Soruları yanıtlar ve bulgularını kaynaklara bağlar.
7. Tek raporu oluşturur, tamamını sayfa sayfa kontrol eder ve kendi onayını verir.
8. Resmî editör, imza ve teslim işlemlerini kendisi yapar.

### 1.3 Otomasyon ilkesi

- Güvenli, tekrarlı, deterministik ve geri alınabilir işler varsayılan olarak otomatik çalışır.
- Kullanıcıdan her dosya, her ASR işlemi veya her biçim kontrolü için tekrar onay istenmez.
- Yalnızca belirsizlik, çelişki, bozuk materyal, güvenlik riski, kapsam/uzmanlık kararı veya meslekî kanaat gerektiğinde ilgili adım kullanıcıya çıkar.
- Bir materyaldeki hata, diğer materyallerin güvenli biçimde işlenmesini gereksiz yere durdurmaz.
- MİHENK'in otomatik kontrolü yalnızca tanımlı kontrolün sonucudur; raporun hukuken veya meslekî olarak doğru/eksiksiz olduğuna dair garanti değildir.

### 1.4 İnsan kontrolü ve yasak sınırlar

MİHENK:
- Bilirkişinin yerine görevi kabul/ret veya çekinme kararı vermez.
- Belirsiz görevlendirme talimatını hukukî olarak yorumlamaz.
- Konuşulmayan kelimeyi tahmin ederek transkripte eklemez.
- Konuşmacının gerçek kimliğini, yaşını, cinsiyetini veya kimlik eşleşmesini iddia etmez.
- Sesin özgünlüğü/manipülasyonu, kişi kimliklendirmesi veya 56.11 incelemesi yapmış gibi davranmaz.
- Bilirkişinin teknik kanaatini veya hukukî değerlendirmeyi üretmez.
- UYAP'a otomatik giriş, portal ekran otomasyonu, resmî teslim, e-imza veya PIN/özel anahtar işlemi yapmaz.

Nihai transkript, bulgular, soru yanıtları, teknik kanaat, raporun meslekî onayı, imza ve resmî teslim bilirkişinin kontrolündedir.

## 2. Kavram sözlüğü ve sahiplik sınırları

| Kavram | Ne anlama gelir? | Nerede yönetilir? |
|---|---|---|
| Yerel kasa | Profil, görevlendirme ve materyalleri cihazda şifreli tutan veri alanı | İlk kurulum; Kasa ve Güvenlik |
| Bilirkişi profili | Kullanıcının raporda kullanılabilecek meslekî kimlik bilgileri | Avatar > Bilirkişi Profilim |
| Uzmanlık alanı | Bilirkişinin kendisine ait temel/alt uzmanlık beyanı | Avatar > Uzmanlık Alanlarım |
| Uzmanlık modülü | MİHENK'in belirli uzmanlık için sağladığı yazılım iş akışı ve araçları | Uzmanlık Modülleri |
| Görevlendirme | Mahkeme/merci tarafından verilen tek iş | Görevlerim |
| Görev Profili | Görevlendirme ve ek belgelerden çıkarılan göreve özel yapılandırma | Görevlendirme adımı ve görev alanı |
| Materyal | Görev kapsamında teslim alınan bir veya çok belge/ses/dijital öğe | Görev > Materyaller |
| ASR | Sesi makineyle metin taslağına dönüştüren yerel yardımcı motor | 56.12 modül yönetimi; görev içinde yürütme |
| Transkript | Kaynak ses zamanlarına bağlı makine taslağı, uzman düzeltmesi ve onay durumu | Görev > Ses ve Transkript |
| Bulgu | Bilirkişinin materyalden yaptığı, kaynağı gösterilen teknik tespit | Görev > Sorular ve Bulgular |
| Tek Rapor | O göreve ait doğrulanmış içerikleri bir araya getiren tek ana belge | Görev > Tek Rapor |

Bir kullanıcının profilindeki uzmanlık alanı ile MİHENK'te kurulu yazılım modülü aynı şey değildir. Profilde bir alan bulunması, o alanın modülünün hazır olduğu veya bilirkişinin yetkinliğinin MİHENK tarafından resmî olarak doğrulandığı anlamına gelmez.

## 3. Ana bilgi mimarisi ve gezinme

### 3.1 Uygulama genel gezinmesi

Sol menü daraltılabilir/genişletilebilir; son tercih hatırlanır. Dar görünümde simgeler kalır, erişilebilir ad/tooltip görünür. Dar/geniş görünümde aynı sayfa ve seçim korunur.

| Ana bölüm | Amacı | Alt içerik |
|---|---|---|
| Genel Bakış | İş durumunu özetlemek; görev çalışma ekranı değildir | Devam eden işler, işlem bekleyenler, rapor kontrolü, doğrulanmış tarihler, son açılan görevler, Yeni görevlendirme |
| Görevlerim | Bütün bağımsız görevlendirmeleri listelemek | Aktif, tamamlanan, arşivlenen; arama ve filtre |
| Uzmanlık Modülleri | MİHENK'in kurulu/kullanılabilir modüllerini yönetmek | Modül kataloğu, modül durumu, sürüm, yerel motor ve model yönetimi |
| Kasa ve Güvenlik | Yerel verinin korunmasını yönetmek | Kilit durumu, otomatik kilit, yedek, geri yükleme, parola/kurtarma, güvenlik bilgisi |
| Uygulama Ayarları | Uygulamanın genel davranışını yönetmek | Görünüm, erişilebilirlik, dil, bildirim, açılış, güncelleme, kısayol |
| Yardım ve Tanılama | Kullanım ve teknik sorunları desteklemek | Kullanım rehberi, sürüm, tanı kayıtları, destek paketi, hata bildirimi |

Avatar/hesap alanı:
- Bilirkişi Profilim
- Uzmanlık Alanlarım
- Profil menüsünden hızlı “Kasayı kilitle” eylemi
- Uygulama sürümü / uygulama bilgisine kısayol (asıl yönetim Uygulama Ayarları > Güncelleme)

Kasa, profil ve uygulama ayarları aynı formda birleştirilmez. Avatar menüsü profil bilgileri içindir; kasa güvenliği ayrı sayfadır; uygulama ayarları ayrı sayfadır.

### 3.2 Genel Bakış ve Görevlerim ayrımı

**Genel Bakış bir dashboard'dur.** Burada görevler tam yönetilmez; kullanıcıya neyin dikkat gerektirdiği gösterilir. Özetler tıklanınca ilgili filtrelenmiş görev/iş listesine gider.

Önerilen dashboard bileşenleri:
- Devam eden görevlendirme adedi.
- Kullanıcı doğrulaması bekleyen görev adedi.
- Materyal/ASR işlemi devam eden görev adedi.
- Rapor kontrolü bekleyen görev adedi.
- Yalnızca görevlendirme belgesinden güvenle çıkarılmış yaklaşan süreler.
- Son açılan görevler (kısa liste).
- Birincil eylem: Yeni görevlendirme.

**Görevlerim tam listedir.** Her görev tek satır/karttır; merci, kullanıcının verdiği kısa ad, dosya referansı (gizlilik için tercihe bağlı maskeli), doğrulanmışsa son tarih, materyal sayısı, soru sayısı, rapor durumu ve görev durumu gösterilir. Dosya içeriği dashboard'da veya görev listesinde açığa dökülmez.

Görev filtreleri: Aktif, doğrulama bekleyen, işlemde, rapor kontrolü, tamamlanan, arşivlenen. Arama varsayılan olarak görev metaverisinde yapılır; görevler arası tam metin arama ayrıca izin/erişim sınırlarıyla tasarlanır.

### 3.3 Görev içi gezinme

Bir görev açıldığında görev başlığı ve görev kimliği sabit kalır; görev içi sekmeler uygulama genel menüsünden farklı bir görsel dil ve konumla gösterilir.

Görev sekmeleri:
1. Görev Özeti
2. Görevlendirme
3. Materyaller
4. Ses ve Transkript
5. Sorular ve Bulgular
6. Tek Rapor

Her sekme yalnızca aktif görevin verisini gösterir. Görev değiştirildiğinde önceki görevin arama, seçili ses, aktif segment, soru yanıtı ve rapor bağlamı yeni göreve taşınmaz.

## 4. İlk kullanım, sonraki açılış ve profil

### 4.1 İlk kullanım akışı

1. Uygulama ilk açılışında çevrimiçi kullanıcı hesabı veya UYAP girişi istemez.
2. Kullanıcı yerel kasa oluşturur ve kasa parolası belirler.
3. Kasa şifreleme/kurtarma uyarılarını ve yedek oluşturma adımını tamamlar. Kasa parolası UYAP parolası veya e-imza PIN'i değildir.
4. Kullanıcı bilirkişi profilini tanımlar.
5. Kullanıcı temel/alt uzmanlık alanlarını seçer.
6. MİHENK kullanılabilir modülleri gösterir; ilk aktif modül 56.12'dir.
7. 56.12 yerel işleme altyapısı hazır değilse, kullanıcıyı görev açmadan önce modülün kurulum/uyumluluk durumuna yönlendirir. Modeli zorunlu olarak ilk açılışta indirmek yerine, modülün ilk kullanımı öncesinde kontrollü kurulum sunulur.
8. Kurulum bitince Genel Bakış açılır; ilk görev oluşturma eylemi belirgin biçimde sunulur.

İlk kurulumda görev belgesi veya rapor için gerekmeyen uzun meslekî form alanları zorunlu tutulmaz.

### 4.2 Bilirkişi profili alanları

Raporun mevzuatta belirtilen kimlik alanları temel alınır; diğer alanlar isteğe bağlı veya göreve bağlıdır.

| Alan | Önerilen davranış | Rapor kullanımı |
|---|---|---|
| Ad | Zorunlu | Soyad ile birlikte gerçek kişi bilirkişi adı |
| Soyad | Zorunlu | Gerçek kişi bilirkişi adı |
| Bilirkişi sicil numarası | Zorunlu/rapor oluşturma öncesi eksikse istisna | Mevzuatın rapor kimlik unsuru |
| Meslekî unvan/sıfat | Zorunlu/rapor oluşturma öncesi doğrulanmalı | Mevzuatın rapor kimlik unsuru |
| Temel uzmanlık alanı | En az bir seçim | Profil ve modül eşleştirmesi |
| Alt uzmanlık alanları | İhtiyaca göre çoklu | Görev kapsamıyla eşleştirme |
| Bölge kurulu | İsteğe bağlı profil bilgisi | Yalnız gerektiği yerde |
| Meslek/kurum bilgisi | İsteğe bağlı | Görev/şablon gerektiriyorsa |
| İletişim bilgileri | İsteğe bağlı, asgari veri | Raporun zorunlu alanı değilse rapora eklenmez |

Profil, kullanıcının beyan ettiği bilgidir; MİHENK resmî sicil doğrulaması yaptığını iddia etmez. Kullanıcı profil verisini güncellediğinde geçmiş raporlar sessizce değişmez; oluşturulmuş rapor sürümü kendi kullandığı profil anlık görüntüsünü korur.

İlk ürün bir gerçek kişi profiline odaklanır. Heyet/tüzel kişi görevlendirmesi görülürse MİHENK bu durumu görevde işaretler; tek kişi profilini heyet raporu gibi genişletmez. Gerekirse sonraki ürün kapsamına alınır.

### 4.3 Uzmanlık alanları

- Temel/alt uzmanlık alanları, Bakanlığın güncel yayımlanmış uzmanlık listesi sürümüyle eşleştirilir.
- Kullanıcı birden fazla alan ekleyebilir.
- Alanın listede bulunması, MİHENK modülünün bu uzmanlığı desteklediği anlamına gelmez.
- Kullanıcı beyanı resmî sicil veya yetkinlik doğrulaması sayılmaz.
- Liste sürümü ve kullanıcı seçimi profil geçmişinde saklanır.
- Güncel liste değişirse eski profil alanları sessizce yeniden sınıflandırılmaz; kullanıcıya fark gösterilir.

## 5. Yerel kasa, güvenlik ve veri yaşam döngüsü

### 5.1 Kasa işlevleri

Kasa ve Güvenlik bölümü:
- Kasanın kilit/açık durumunu gösterir.
- Parola değiştirme akışını sunar.
- Otomatik kilit süresi tercihini yönetir.
- Şifreli yedek oluşturma, yedeği doğrulama ve geri yükleme sunar.
- En son başarılı yedek ve yerel veri durumu hakkında bilgi verir.
- Kasa, geçici çalışma alanı ve yedek dosyası arasındaki farkı açıklar.
- Kasa kilidini manuel olarak kapatır.

**Ürün varsayılanı:** Etkinlik olmadığında 10 dakika sonra otomatik kilit önerilir; kullanıcı 1, 5, 10, 15 veya 30 dakika seçeneklerinden birini seçebilir. Bu süre uygulama güvenlik testiyle kesinleştirilmelidir. Kullanıcı rapor düzenlerken, ses çalarken veya uzun işlem sürerken ekranda hassas veri açık kalması riski ayrıca ele alınır; ASR arka planda ilerleyebilir fakat kilitli arayüz görev metnini göstermez.

### 5.2 Kasa parola ve kurtarma ilkeleri

- Parola UYAP veya e-imza bilgisi değildir; MİHENK'e özel yerel koruma anahtarıdır.
- Parola kasayı açamaz hâle gelirse MİHENK'in gizli bir arka kapısı veya destek personelinin veriyi çözme yetkisi bulunmaz.
- Yedek, ana kasadan bağımsız olarak şifrelenir ve geri yükleme gerçekten sınanmadan “yedek hazır” sayılmaz.
- Parola unutma, yedek parola kaybı, bozuk yedek ve eksik depolama durumları ilk kurulumda anlaşılır biçimde açıklanır.
- Kriptografik algoritma, anahtar türetme, bellek temizleme ve kurtarma anahtarı kararı güvenlik mimarisi ve bağımsız test konusudur; UI metni teknik doğrulama tamamlanmadan algoritma garantisi vermez.

### 5.3 Görev arşivleme, silme ve saklama

- Görev kapatmak, görevi arşivlemek ve görevi silmek farklı işlemlerdir.
- Tamamlanan görev varsayılan olarak arşivlenebilir; bu işlem kaynak veriyi silmez.
- Silme açık onay, etkilenecek materyal/yedek bilgisi ve geri alınamazlık uyarısı gerektirir.
- Kasa dışındaki yedeklerdeki kopyalar, dışa aktarımlar ve fizikî materyaller ayrıca değerlendirilir.
- MİHENK kendi başına bilirkişinin hukukî saklama/iade yükümlülüğünü belirlemez; görev bazında belirlenmiş saklama/imha talimatı bulunmuyorsa otomatik veri imhası yapmaz.
- Kullanıcı fizikî/dijital materyal iadesini kayıt altına alabilir; MİHENK kaydı resmî teslim/tesellüm tutanağı yerine geçmez.

### 5.4 Tanılama verisi

- Hata ayıklama varsayılan olarak yerel tutulur.
- Destek paketi oluşturulursa kullanıcı içeriğini önceden görebilir.
- Gerçek ses, transkript, dosya adı, dosya numarası, taraf bilgisi, kasa anahtarı veya gizli görev metni destek paketine otomatik eklenmez.
- Kullanıcı açıkça seçmeden dosya veya log haricî bir yere gönderilmez.
- Public GitHub issue/PR/test verisine gerçek vaka materyali eklenmez.

## 6. Uygulama ayarları

Uygulama Ayarları yalnızca genel program davranışını yönetir. Profil alanları, kasa parolası ve uzmanlık modülünün model ayarları burada toplanmaz.

| Ayar grubu | İçerik | Sahiplik |
|---|---|---|
| Görünüm | Açık/koyu/sistem teması, yoğunluk, yazı boyutu, sol menü tercihi | Uygulama Ayarları |
| Erişilebilirlik | Klavye ile gezinme, odak göstergesi, kontrast, hareket azaltma | Uygulama Ayarları |
| Dil ve bölge | Arayüz dili, tarih/saat/gösterim biçimi | Uygulama Ayarları |
| Bildirimler | Yerel hatırlatmalar, işlem tamamlandı/hata uyarıları | Uygulama Ayarları |
| Açılış | Son açık sayfa veya Genel Bakış, açılışta kasa davranışı | Uygulama Ayarları |
| Kısayollar | Oynatma, sarma, segment, arama ve gezinme kısayolları | Uygulama Ayarları; modül/ekran bağlamına göre |
| Güncellemeler | Güncelleme kanalı, kontrol, indirme/kurulum durumu, hata geçmişi | Uygulama Ayarları |
| Uygulama bilgisi | Sürüm, lisanslar, bileşen envanteri | Uygulama Ayarları |
| Tanılama | Yerel tanı günlüğü, destek paketi | Yardım ve Tanılama |

Bir ayarın nerede yaşadığı konusunda kural: **Kullanıcı ayarı yaptığı şeyin sahibine gider.** Meslekî veri profilde, şifreli veri kasada, 56.12 motoru modülde, pencere/tema ayarı uygulama ayarlarında, dosya/soru/rapor içeriği görevde yönetilir.

## 7. Uzmanlık Modülleri ve yerel ASR yönetimi

### 7.1 Modül kataloğu

Modül kataloğunda her modül için:
- Ad, kısa açıklama ve uzmanlık kapsamı.
- Kullanılabilirlik ve kurulum durumu.
- Sürüm ve çekirdek uyumluluğu.
- Gerekli yerel motor/model bileşenleri.
- Lisans, kaynak ve bütünlük doğrulama bilgisi.
- İşletim sistemi/donanım uygunluğu.
- Güncelleme ve geri alma durumu.
- Kapsam içi ve kapsam dışı işlemler bulunur.

İlk aktif modül 56.12'dir. Modül katalogda görünür; desteklenmeyen modüller “yakında” gibi belirsiz bir butonla değil, “bu sürümde kullanılamıyor” açıklamasıyla gösterilir.

### 7.2 ASR ayarının yeri

**ASR, Uygulama Ayarları'na konulmaz.** ASR, 56.12 modülünün yerel çalışma altyapısıdır.

Konum:
- Genel gezinme: Uzmanlık Modülleri
- Modül: 56.12
- Modül yönetimi: Yerel İşleme Altyapısı / Motor ve Model

Bu sayfada:
- Aktif motorun hazır/kurulu/uyumsuz/hatalı durumu.
- Model ve runtime adı/sürümü.
- Model kaynağı, lisansı, checksum doğrulaması.
- İndirilen modelin boyutu ve gereken disk alanı.
- Yerel donanım uyumluluğu ve kaynak tahmini.
- İşleme izinleri ve çevrimdışı çalışma durumu.
- Model güncelleme, doğrulama, onarım ve geri alma.
- Gelişmiş kullanıcı için doğrulanmış motor profili seçimi bulunur.

### 7.3 Normal kullanıcı ve gelişmiş kullanıcı davranışı

Normal bilirkişiye her görevde “SEDA mı, Whisper mı, başka model mi?” sorulmaz. MİHENK, cihazla ve modül sürümüyle uyumlu, lisans/bütünlük/test koşulları doğrulanmış motor profilini kendisi seçer.

- Kullanıcı modülü ilk kez kullanırken gerekli model paketini kurar veya daha önce kurulu paketi doğrular.
- Model indirme internet gerektiriyorsa yalnızca model paketi indirilir; vaka sesleri yerel makineden çıkmaz.
- Kurum ağı/çevrimdışı ortam için doğrulanmış paket içe aktarma yolu sağlanır.
- Varsayılan ayar değişikliği yalnız yeni ASR çalıştırmalarına uygulanır; eski kayıtların kullandığı model geriye dönük değişmez.
- Gelişmiş kullanıcı, yalnız MİHENK'in doğruladığı motor profilleri arasından geçici seçim yapabilir. Seçim, gerekçe ve sürüm işlem kaydına girer.
- Kullanıcı teknik gerekçe olmadan motor değiştirmeye yönlendirilmez.

SEDA şu an yerel ASR denemesidir; varsayılan/nihai en iyi motor olarak sabitlenmiş değildir. Motor seçimi aynı izinli insan referanslarıyla, aynı koşullarda ve görevdeki gerçek uzman düzeltme yükü de ölçülerek yapılır.

### 7.4 Görev içindeki ASR

Görev > Ses ve Transkript ekranında kullanıcı motor yönetimi yapmaz. Şunları görür:
- Her sesin ASR durumu ve kuyruk sırası.
- Hazırlanıyor, sırada, çalışıyor, duraklatıldı, tamamlandı, hata veya yeniden deneme durumu.
- İlerleme ve tahmini kalan süre (güvenilir tahmin üretilebiliyorsa).
- Hangi model/işlem profilinin o kayıt üzerinde kullanıldığına ilişkin kısa provenance bilgisi.
- Hata nedeni ve güvenli yeniden deneme.
- Belirsiz segmentler ve uzman inceleme durumu.

Materyal kabul/bütünlük ve teknik okuma kontrolleri geçtikten sonra ASR kuyruğu otomatik hazırlanır. Görev bazında kullanıcı kuyruğu başlatabilir/duraklatabilir; her dosya için ayrı motor seçmez. Bozuk bir dosya, diğer geçerli kayıtların işlemesini engellemez. İşlem kesilirse güvenli kontrol noktası üzerinden devam eder; yinelenmiş segment veya çift rapor girdisi oluşmaz.

### 7.5 ASR çalışmasının kayıt altına alınması

Her transkripsiyon çalışması için en az:
- Görev ve ses materyali kimliği.
- Kaynak ses hash'i ve çalışma kopyası kimliği.
- Motor/engine adı ve sürümü.
- Model adı, model sürümü ve checksum.
- Runtime/build ve decoder sürümü.
- Parametreler, dil ayarı ve ön işleme/dönüştürme bilgisi.
- Başlangıç/bitiş, tamamlanan parçalar ve işlem sonucu.
- Makine çıktısının kimliği ve onu izleyen uzman revizyonları
saklanır.

Bu işlem kaydı tarihsel gerçeği temsil eder. Motor değiştirildiğinde önceki run kaydı güncellenmez veya silinmez.

## 8. Yeni görevlendirme ve Görev Profili

### 8.1 Görev oluşturmanın girişi

Görevlerim > Yeni görevlendirme. Kullanıcı önce görevlendirme yazısı/kararı, ek talimat, teslim tutanağı ve varsa dizi pusulasını ekler. Dosya henüz yoksa veya yalnız fizikî teslim yapıldıysa uygulama kullanıcıya belgeyi sonradan ekleme ve materyal envanterini başlatma yolu sunar; tüm alanları elle doldurmaya zorlamaz.

### 8.2 Belge okuma akışı

1. Kaynak belgeler görev içine alınır, özgün dosya korunur ve bütünlük bilgisi oluşturulur.
2. Metin tabakası olan belgelerden yerel metin çıkarılır.
3. Taranmış belgelerde yerel OCR/okuma denenir.
4. Her çıkarılmış alan kaynak belge, sayfa ve mümkünse paragraf/alan konumuna bağlanır.
5. Sistem merci, dosya referansı, tarih, süre ve başlangıç olayı, inceleme konusu, kapsam/sınırlar, sorular, beklenen materyaller ve açık teslim koşullarını aday olarak çıkarır.
6. Açık ve tutarlı alanlar Görev Profili'ne alınır.
7. Eksik, belirsiz, çelişkili veya düşük okunabilirlikteki alanlar ayrı istisna listesine alınır.
8. Kullanıcı yalnız ilgili istisnayı, kaynak metnin yanında görerek doğrular veya düzeltir.

**Kullanıcı baştan uzun bir form doldurmaz.** Kullanıcıya “7 alan bulundu, 1 alan doğrulama bekliyor” gibi özet gösterilir. İsteyen tüm alanları ve kaynaklarını açıp inceleyebilir; her alanı zorunlu olarak tek tek onaylamaz.

### 8.3 Görev Profili alanları

- Merci ve yargı/merci türü.
- Dosya referansı ve görevlendirme tarihi.
- İnceleme konusu, kapsamı, sınırları ve açıkça kapsam dışı bırakılan hususlar.
- Her biri ayrı ve sıralı görev sorusu.
- Ücret/gider bilgisi (belgede yer alıyorsa).
- Süre miktarı, birimi, başlangıç olayı, başlangıç tarihi ve son tarih (yalnız kaynakta yeterli bilgi varsa).
- Beklenen materyaller ve teslim yöntemi.
- Teslim alınan materyallerle beklenen listenin farkları.
- Rapor/ek/çıktı talimatı, suret ve fizikî iade koşulları.
- Uzmanlık ve modül eşleşmesi.
- Rapor profilinin dayanağı ve sürümü.

### 8.4 Belirsizlik ve çelişki yönetimi

- Bir belgede 30 gün, diğerinde 45 gün yazıyorsa MİHENK kendi kendine üstün kaynak seçmez; iki kaynak ve ilgili alanı gösterir.
- Süre başlangıç olayı açık değilse kesin son tarih oluşturmaz.
- Görev kapsamı/uzmanlık uygunluğu yoruma açıksa bilirkişiye veya görevlendirmeyi yapan merciye çözülmesi gereken soruyu gösterir.
- Kullanıcı metin okuma hatasını düzeltebilir; bu düzeltme kaynakta ne yazdığını değiştirmez, çıkarılan alanın kullanıcı düzeltmesi olarak kaydedilir.
- Hukukî talimatın anlamı belirsizse MİHENK karar vermez; merciye açıklama isteme süreci için dışarıda yapılacak işlemi hatırlatabilir.
- Belge okunamadığında ham belge korunur, sayfa/alan hatası gösterilir, alternatif dosya veya manuel alan ekleme yolu sunulur.

### 8.5 Belge biçimi ve UDF sınırı

- Belge kabul biçimleri sürümlü bir destek matrisiyle yönetilir.
- İlk tasarımda metin tabanlı PDF ve taranmış PDF temel giriş biçimleri kabul hedefidir; resim/ek türleri ayrıca doğrulanmış listeye alınır.
- DOCX/RTF/TXT gibi ek türler ancak yerel çıkarım ve koruma testleri geçtiğinde desteklenen biçim sayılır.
- UDF orijinal kaynak belge olarak saklanabilir; doğrudan UDF metin çıkarımının güvenilirliği doğrulanmadan “tam destekleniyor” etiketi verilmez.
- Doğrudan okuma desteklenmeyen UDF için kullanıcı, resmî UYAP Editör'de açıp izinli bir okuma kopyası (örneğin PDF) üreterek MİHENK'e ekleyebilir; orijinal UDF ayrıca görev kaynağı olarak korunur.
- OCR sonucunun güveni düşükse otomatik görev profili tamamlanmış sayılmaz.

## 9. Materyal envanteri ve bütünlük

Her görevin Materyaller sayfasında üç ayrı liste/karşılaştırma bulunur:
1. Görevlendirmede beklenen.
2. Teslim alınan / MİHENK'e aktarılan.
3. İncelenen / işleme alınan / iade edilen.

Her materyal:
- Görev içinde benzersiz kimlik alır.
- Dosya adı, boyut, format/kapsayıcı, codec (uygunsa), süre, kanal, örnekleme ve bit derinliği gibi teknik bilgileri taşır.
- Kaynak hash'i ve korunan orijinal ile çalışma kopyası arasındaki bütünlük bilgisini saklar.
- Desteklenen dosya için zararlı dosya tarama ve decoder güvenlik sınırlarına tabi olur.
- Hangi işlemde kullanıldığını ve hangi rapor/ek/dayanakla ilişkili olduğunu tutar.

Aynı hash'e sahip dosyalar olası kopya olarak işaretlenebilir; kullanıcıya göstermeden silinmez veya birleştirilmez. Aynı ada sahip ama içeriği farklı iki materyal ayrı kimlik alır.

Fizikî dosya, USB veya kâğıt evrak için MİHENK yardımcı envanter ve teslim notu tutabilir; resmî teslim/tesellüm, zincir-i muhafaza veya tutanak yerine geçmez. Kopyalama sonrası hash eşleşmesi, teslimden önceki kaynağın özgünlüğünü tek başına kanıtlamaz.

## 10. 56.12 Ses ve Transkript çalışma alanı

### 10.1 Çalışma tezgâhı

Masaüstü genişliği elverdiğinde:
- Sol panel: göreve ait ses listesi, her kaydın teknik ve ASR durumu.
- Orta panel: oynatıcı, gerçek kaynaktan hesaplanan dalga biçimi, zaman çizgisi, kanal seçimi, hız, tekrar aralığı ve oynatma konumu.
- Sağ panel: aktif kayda ait zaman kodlu transkript, segment durumu ve uzman düzenleme alanı.

Dar pencere genişliğinde paneller dikey istiflenebilir veya görev içi sekmeye dönüşebilir; metin dar alanda dikey harf/sıkışmış yatay scroll hâline gelmez. Dayanak seçicisi küçük, dar, yatay kaydırılan kutu olmayacak; arama yapılabilir geniş diyalog/yan panel olacaktır.

### 10.2 Transkript veri katmanları

- Ham ASR çıktısı değiştirilemez tarihsel başlangıç kaydıdır.
- Görünen uzman metni ayrı sürümlenir.
- Uzman düzeltme olayları önce/sonra metin, zaman aralığı, olay zamanı ve yerel uzman bağlamıyla tutulur.
- Onay durumu metin kaynağından ayrıdır. ASR tarafından üretilen metin, uzman düzeltti diye kaynağı “insan yazdı” hâline dönüştürülmez.
- ASR tekrar çalıştırılırsa uzman düzeltmesi bulunan segmentlerin üzerine sessizce yazılmaz; yeni makine çıktısı ayrı run olarak saklanır.
- Belirsiz bölüm tahminle doldurulmaz; “anlaşılmayan”, “kısmen anlaşılmayan”, vokalizasyon ve çevresel olay anotasyonları ayrı türdür.
- Konuşmacı etiketi nötr ve manuel olabilir (Konuşmacı 1, Konuşmacı 2). Kanal kimliği, gerçek kişi kimliği olarak yorumlanmaz.

### 10.3 İnceleme kuyruğu

Filtreler:
- Tümü
- Kontrol bekliyor
- Belirsiz / yeniden dinle
- Uzman onaylı

Filtre sayacı sadece görünüm filtresidir; metni değiştirmez, otomatik onay veya silme yapmaz. İnceleme kuyruğu daha sonra görevler arası listeye dönüşürse görev erişim izolasyonu ve kaynağa geri dönüş korunur.

### 10.4 Ses / transkript hata davranışları

- Kaydı listede göstermek tek başına seçili ve oynatmaya hazır sayılmaz.
- Kasa açılışında seçili ses geri yüklenirken kaynak çözülür, decoder açılır, süre ve oynatılabilirlik doğrulanır; ancak bundan sonra hazır görünür.
- Kaynak açılamazsa süre 00:00 gibi yanıltıcı bir değerle normal ses gibi gösterilmez; “kaynak açılamadı” ve hata nedeni gösterilir.
- Dalga biçimi üretilemezse oynatma çalışabiliyorsa oynatıcı kalır; dalga biçimi ayrı hata durumudur.
- ASR hatasında dosya, hata ve tekrar deneme gösterilir; başarılı kayıtlar engellenmez.
- Uzun kayıt kuyruğu kesintiden sonra devam edebilir; tamamlanmış parçalar yinelenmez.
- Transkript segmentine tıklamak ilgili ses aralığına gider; ses konumu değişince aktif segment vurgulanır.

## 11. Sorular ve Bulgular

Görev Profili'nden çıkarılan her soru ayrı, sırası korunmuş kayıttır. Soru metni kaynak belgeyle ilişkili kalır; kullanıcı değiştirdiğinde özgün alıntı ve kullanıcı düzeltmesi ayrılır.

Her soru çalışma kartında:
- Sorunun özgün metni.
- Yanıt/durum (başlanmadı, çalışılıyor, kaynak bekliyor, bilirkişi kontrolünde, rapora hazır).
- Bilirkişinin yazdığı yanıt/teknik açıklama.
- Bir veya daha fazla dayanak materyal.
- Dayanağa ait zaman aralığı/transkript segmenti/belge sayfası.
- Gerekli olduğunda görsel, tablo veya başka ek referansı.

Bir yanıt başka görevin materyaline bağlanamaz. Eksik veya geçersiz dayanak rapor kalite kontrolünde gösterilir.

MİHENK:
- Bilirkişinin yerine yanıt yazmaz.
- Birden fazla kaynaktan otomatik hukukî/meslekî kanaat sentezlemez.
- Soruyu veya yanıtı sırf rapor dolsun diye tamamlamaz.
- Kaynak referansını ve destekleyici veriyi düzenler, rapora taşır ve eksikliği denetler.

## 12. Tek ana rapor: oluşturma, içerik ve ASR açıklaması

### 12.1 Ürün kararı

Her görevlendirme için **tek ana rapor** bulunur. Kullanıcı DOCX/ODT/JSON/PDF rapor çeşitleri arasında seçim yapmaz. MİHENK görev profilinden, merci türünden, teslim talimatından ve doğrulanmış çıktı desteğinden uygun belge düzenini belirler.

MİHENK raporun tamamını gerçek sayfa ölçüsü, sayfa numarası ve sayfa geçişleriyle gösteren önizleme sunar. Bölüm listesi, sayfa görünümü ve kalite kontrol paneli aynı Tek Rapor ekranında bulunur.

Rapor içeriğini otomatik birleştirmek ile uzman görüşü üretmek farklıdır:
- MİHENK, onaylanmış görev verileri ve bilirkişinin yazdığı yanıtları rapor bölümlerine yerleştirir.
- MİHENK eksik alanları, cevapsız soruları, dayanak kopukluklarını, kontrol bekleyen transkriptleri ve teslim biçimi belirsizliğini işaretler.
- MİHENK gerekçeli teknik sonuç, ses içeriğinin anlamı veya hukukî kanaat uydurmaz.
- Uzman kontrolü tamamlanmadan taslak, nihai rapor gibi gösterilmez.

### 12.2 Raporun görev-özel yapısı

Rapor iskeleti sabit tek bir bakanlık formu olarak dayatılmaz. Adalet Bakanlığının resmî sayfasında farklı merci/yargı türleri için ayrı şablon aileleri yayımlanmıştır. MİHENK bu şablonları ve görevlendirme talimatını görev özelinde değerlendirir; şablon sürümü/kaynağı kayıt altına alınır.

Görev türüne göre düzenlenen raporda uygun olduğu ölçüde:
1. Kapak ve görevlendiren merci.
2. Dosya numarası ve yargılamanın taraf bilgileri.
3. Görevlendirme tarihi ve süresi.
4. İncelemenin konusu, kapsamı ve sınırları.
5. İncelenmesi/gözlemlenmesi istenen maddi unsurlar.
6. İnceleme yöntemi.
7. Bilimsel ve teknik dayanaklar.
8. Materyal envanteri ve yapılan işlemler.
9. İnceleme/bulgular.
10. Görev sorularına, özgün sırası korunarak tek tek gerekçeli yanıtlar.
11. Sınırlılıklar ve varsa cevaplanamayan hususların nedeni.
12. Gerekçeli sonuç.
13. Rapor düzenlenme tarihi ve bilirkişi kimlik bilgileri.
14. İncelemeye esas maddi unsurları belgeleyen, sonucu açıklamaya yardımcı kayıtlar/tablolar ve ekler.

Bölümlerin başlık ve sırası merci türü, resmî şablon ve görevlendirme içeriğiyle uyumlu olabilir; tüm görevlerde aynı sabit başlık sırası zorlanmaz.

### 12.3 ASR/model bilgisi raporda nasıl gösterilir?

Yönetmeliğin rapor içeriği maddesi inceleme yöntemi ile bilimsel/teknik dayanakları sayar; belirli bir ASR markası veya model adının mutlaka yazılmasını açıkça düzenlemez. Bu nedenle “model adı kanunen her durumda zorunludur” denemez.

Bununla birlikte, 56.12'de ASR'nin metin taslağını üretmesi inceleme yönteminin maddi bir parçasıdır. Kullanılan aracı saklamak, özellikle otomatik çıktının son transkripte etkisi olduğunda, yöntemin denetlenmesini zorlaştırır. MİHENK'in ürün politikası aşağıdaki olmalıdır:

**Ana rapor — okunabilir yöntem açıklaması**
- ASR'nin yalnızca ilk metin taslağı üretmekte kullanıldığı açıkça yazılır.
- Transkriptin bilirkişi tarafından nasıl dinlenerek kontrol edildiği, düzeltildiği ve belirsiz bölümlerin nasıl işaretlendiği açıklanır.
- İşlem yerel/çevrimdışı yürütüldüyse bu durum doğru biçimde belirtilir.
- Gerçekten kullanılmış motor/model ve sürümü, raporun “İnceleme yöntemi / kullanılan teknik araçlar” bölümünde kısa ve anlaşılır şekilde belirtilir. Bu bilgi raporda görünür olmalıdır; yalnız gizli uygulama loguna bırakılmaz.

**Teknik kayıt / uygun olduğunda rapor eki**
- Motor ve modelin tam kimliği/sürümü.
- Runtime/build, parametre ve dil ayarları.
- Model ağırlığı checksum'ı.
- Her materyalde hangi run'ın kullanıldığı.
- Varsa ön işleme, format dönüşümü, kanal işlemi ve bu işlemlerin parametreleri.
- Uzman kontrol durumu ve revizyon bağlantısı.

Model değişmiş veya aynı görevde farklı sesler farklı motorlarla işlenmişse, materyal-run eşlemesi açıkça tutulur; rapor bütün görevi tek modelle işlenmiş gibi göstermez.

**Örnek rapor metni (yalnız gerçek işleme uygunsa):**

> “Ses kayıtlarının ilk metin taslakları, MİHENK bünyesinde yerel olarak çalışan [motor/model adı ve sürümü] kullanılarak oluşturulmuştur. Otomatik tanıma çıktıları tek başına nihai metin olarak kabul edilmemiş; ilgili kayıt bölümleri dinlenerek bilirkişi tarafından kontrol edilmiş, gerekli düzeltmeler yapılmış ve anlaşılamayan bölümler ayrıca işaretlenmiştir. Kayıt bazındaki araç, sürüm ve işlem bilgileri teknik inceleme kayıtlarında gösterilmiştir.”

Bu metin sabit ve otomatik eklenmiş bir iddia değildir. MİHENK yalnız gerçekten yapılan işlemlerden ve tamamlanmış uzman kontrolünden bilgi doldurur. Kısmen kontrol edilmiş kayıt için tam kontrol yapılmış gibi cümle kurmaz. Model adı/sürümü yoksa uydurmaz; rapor kalite kontrolünde eksik teknik iz olarak gösterir.

Model bilgisi raporda bir reklam, kalite garantisi veya bilirkişi kanaati gibi sunulmaz. “En iyi model”, “kesin doğru transkript”, “%99 güvenilir” gibi kanıtsız iddialar üretilmez. Modelin varlığı, bilirkişinin bizzat inceleme yükümlülüğünü devretmez.

### 12.4 Tek raporun sürüm ve biçim davranışı

- Rapor ilk oluşturulduğunda görev verisinin ve bilirkişi profilinin o anki anlık görüntüsünü alır.
- Her yeniden oluşturma/yayımlama yeni bir rapor revizyonu üretir; önceki revizyon korunur.
- Kullanıcı aynı görevde birden çok paralel “ana rapor” yönetmez; bir güncel ana rapor ve onun geçmiş revizyonları bulunur.
- Büyük ses dosyaları rapor gövdesine gömülmez; envanter, kimlik, hash ve zaman kodlarıyla ilişkilendirilir.
- Transkript veya önemli alıntılar, görevin istediği kapsam ölçüsünde rapor bölümü/ek olarak dahil edilir.
- Format kullanıcıya seçenek listesi olarak sunulmaz. MİHENK doğrulanmış dışa aktarım yolunu görev talimatına göre seçer.
- UYAP Editör'ün güncel Windows sürümünde gerçek aç/kaydet/yeniden aç ve sayfa/karakter/ek testi geçmeden çıktı “UYAP'a hazır” olarak işaretlenmez.
- UDF üretimi ve portalda kabul, belge formatı ve evrak türü bazında ayrıca doğrulanır. UYAP otomatik teslim veya e-imza yapılmaz.

### 12.5 Rapor kalite kapıları

Rapor oluşturma öncesi/sonrası kontroller:
- Görevlendiren merci, dosya numarası ve raporun zorunlu kimlik alanları.
- Görev sorularının tamamının bulunması ve özgün sırada görünmesi.
- Her sorunun yanıt durumu.
- Yanıtların aynı görevin geçerli kaynaklarına bağlanması.
- Gerekli segmentlerin uzman kontrol durumu; belirsiz bölümlerin saklanmaması.
- Materyal envanteri ve rapor ekleri arasındaki eşleşme.
- Kullanılan araç/model/sürüm ve yöntem kayıtlarının bulunması.
- Sınırlılıklar, çözülemeyen hususlar ve desteklenmeyen işlemler.
- Başka görevden veri sızmaması.
- Raporun sayfa düzeni, Türkçe karakter, tablo, sayfa numarası ve ek bütünlüğü.
- Resmî editör/format testi durumu.

Kalite kapısı “GEÇTİ / UYARI / ENGELLENDİ” olabilir. Uyarı ile engel arasındaki fark açıkça açıklanır. Eksik zorunlu alan veya yanlış görev kaynağı varsa dışa aktarım/sonlandırma engellenir; kullanıcı eksikliği giderir veya “bu görevde bulunmuyor/uygulanamaz” gerekçesini kaydeder. Hukukî/meslekî değerlendirmenin doğruluğu otomatik puanlanmaz.

## 13. Yardım, güncelleme ve tanılama

### 13.1 Yardım ve kullanım

- İlk kullanımda bağlama duyarlı kısa yardım bulunur.
- Uzun eğitim zorunlu tutulmaz; her sayfada “bu ekran ne işe yarar?” açıklaması sunulur.
- Kullanım rehberi, sürüm notları ve resmî UYAP/Adalet yazılımlarına bağlantılar ayrı tutulur.
- MİHENK'in desteklemediği veya doğrulamadığı bir resmî işlev için kullanıcıya sahte tamamlandı durumu gösterilmez.

### 13.2 Güncelleme yönetimi

- Güncelleme kontrolü Uygulama Ayarları > Güncellemeler içinde yönetilir.
- İndirme/kurulum aşaması ve yüzdesi, doğrulama sonucu, hata kimliği ve güvenli yeniden deneme durumu görünür.
- İmzalı paket/manifest doğrulaması geçmeden güncelleme kurulmuş sayılmaz.
- Başarısız kurulum mevcut uygulama ve kasa verisini korumalı; geri dönüş/yeniden deneme yönlendirmesi verilmelidir.
- Modül/model güncellemesi uygulama güncellemesinden ayrıdır ve 56.12 modül yönetiminde görünür.
- Güncelleme sırasında görev/kasa bütünlüğü kabul testleri çalıştırılmalıdır.

### 13.3 Tanılama ekranı

- Uygulama sürümü, platform, güvenli hata kimliği, son işlem adımı ve kullanıcı tarafından dışa aktarılan log paketi.
- Hata ayıklama ayrıntısı kullanıcıya sade dille açıklanır; teknik ayrıntı “ayrıntıları göster” altında bulunur.
- Tanılama paketi gerçek materyal içeriği taşımaz.
- Destek isteği için uygulamanın kendiliğinden UYAP, GitHub veya haricî hesaba bağlanması gerekmez.

## 14. Görev yaşam döngüsü

Bir görevin durumu tek bir “tamamlandı” etiketinden ibaret olmamalıdır. Önerilen durumlar:

1. **Yeni:** Görev kaydı açıldı, belge veya kaynak eklenmesi bekleniyor.
2. **Belge okunuyor:** Kaynaklar metin çıkarımı/OCR aşamasında.
3. **Doğrulama gerekiyor:** Yalnız istisna alanları kullanıcı kararını bekliyor.
4. **Görev profili hazır:** Kapsam, sorular ve materyal beklentisi yapılandırıldı.
5. **Materyal kontrolü:** Dosya kabulü, hash, metadata veya eksiklik kontrolü sürüyor.
6. **İnceleme sürüyor:** ASR, transkript kontrolü veya bulgu çalışması var.
7. **Bilirkişi yanıtı bekleniyor:** Bir veya daha fazla görev sorusu üzerinde uzman çalışması gerekli.
8. **Rapor taslağı:** Tek ana rapor oluşturuldu; kalite kontrolleri/uzman son incelemesi sürüyor.
9. **Uzman son kontrolü:** Raporun tüm sayfaları ve içerikleri kullanıcı tarafından inceleniyor.
10. **Tamamlandı:** Bilirkişi rapor hazırlama çalışmasını kendi kararıyla tamamladı. Bu durum UYAP'a gönderildi veya imzalandı anlamına gelmez.
11. **Arşivlendi:** Görev aktif listeden çıkarıldı, korumalı verisi saklanıyor.
12. **Silme için işaretlendi / silindi:** Kullanıcının açık veri yönetimi eylemi; yedek ve dış kopya etkisi gösterilir.

Süre ve uyarı sadece kaynak belgeden doğrulanmışsa takvimde kesin tarih olarak yer alır. Başlangıç tarihi belirsizse “doğrulama gerekiyor” olur; uygulama otomatik son tarih uydurmaz.

## 15. Uçtan uca kullanıcı akışları

### A. İlk kez kullanma
Kurulum → yerel kasa oluşturma → parola/kurtarma açıklaması → profil → uzmanlık alanları → modül kataloğu/56.12 hazırlığı → Genel Bakış.

### B. Sonraki açılış
Uygulama → kasa kilidini aç → son durum/Genel Bakış → seçilen göreve devam et. Profil yeniden istenmez. Kilitli kasada görev adı/içerik ifşa edilmez.

### C. Yeni görevlendirme
Görevlerim → Yeni görevlendirme → görevlendirme/ek belgeleri yükle → yerel okuma/OCR → Görev Profili otomatik çıkarımı → yalnız istisnaları doğrula → uzmanlık/modül kontrolü → görev alanını oluştur.

### D. Materyal kabulü
Görev → Materyaller → beklenen materyal listesini gör → bir veya çok dosyayı içe al → hash/metadata/decoder kontrolü → kaynak/kopya bütünlüğü sonucu → eksik/fazla/bozuk materyal istisnası → uygun materyali işleme kuyruğuna al.

### E. Ses ve transkript
Görev → Ses ve Transkript → kayıt seç → oynat/kanal/zaman çizgisi → yerel ASR kuyruğu → makine taslağı → uzman dinlemesi/düzeltmesi → belirsiz segment → revizyon geçmişi → uzman onaylı segmentler.

### F. Sorular ve bulgular
Görev → Sorular ve Bulgular → bir soruyu aç → uzman yanıtını yaz → aynı görevin ses segmentleri/belgelerine dayanak bağla → kontrol durumunu güncelle → kalan sorulara devam et.

### G. Tek rapor
Görev → Tek Rapor → raporu oluştur → dinamik görev/merci yapısı → içerik ve dayanak kontrolleri → A4 sayfa önizlemesi → tüm sayfaları incele → gerekli düzeltmeyi ilgili görev alanında yap → rapor revizyonunu yeniden oluştur → bilirkişi son kontrolü.

### H. Resmî teslim
Bilirkişi nihai raporu kendi kontrolünde dışa aktarır → uygun resmî UYAP Editör akışında açar/kaydeder → e-imzayı resmî Adalet aracında uygular → Bilirkişi Portal üzerinden resmî teslimi bizzat gerçekleştirir → isterse teslim bilgisini MİHENK'te kullanıcı tarafından doğrulanmış kayıt olarak not eder.

### I. Kasa ve veri kurtarma
Kasa ve Güvenlik → şifreli yedek oluştur → yedeği doğrula → geri yükleme hedefini seç → kasa bütünlüğü kontrolü → yanlış parola/bozuk yedek/eksik disk durumunda veri kaybı riskini açıkla. Başarı kanıtı gerçek geri yükleme testidir.

### J. Güncelleme ve arıza kurtarma
Güncelleme kontrolü → imza/doğrulama → kurulum → yeniden açma ve kasa kontrolü. Hata varsa paket kurulmuş gibi gösterilmez; son çalışan sürüm korunur ve kullanıcıya güvenli seçenek sunulur.

## 16. Ekran kataloğu — v0.4 için zorunlu kapsam

Aşağıdaki ekranlar v0.4'te görünür bir ekran, modal, sağ panel veya açık durum tasarımıyla temsil edilmelidir. Her satır ayrı rota olmak zorunda değildir; bilgi mimarisinde yeri ve kullanıcı girişi belli olmalıdır.

| ID | Ekran/katman | Kullanıcı amacı | Ana içerik/eylem |
|---|---|---|---|
| S-01 | İlk karşılama | MİHENK'in yerel çalışma yaklaşımını anlamak | İlk kurulum veya mevcut kasa ayrımı |
| S-02 | Kasa oluştur | Yerel şifreli alan kurmak | Parola, tekrar, kurtarma/yedek uyarısı |
| S-03 | Bilirkişi profili | Kimlik bilgilerini bir kez tanımlamak | Ad, soyad, sicil, unvan, isteğe bağlı bilgiler |
| S-04 | Uzmanlık alanlarım | Meslekî alan beyanını yönetmek | Temel/alt alan listesi ve sürüm |
| S-05 | Kasa aç | Sonraki kullanımda güvenli erişim | Parola, kilitli durum, hata |
| S-06 | Genel Bakış | İş durumunu görmek | Dashboard ve Yeni görevlendirme |
| S-07 | Görevlerim | Tüm görevlendirmeleri yönetmek | Filtre, arama, durum, boş liste |
| S-08 | Yeni görevlendirme / belge yükle | Kaynak belgeleri başlatmak | Çoklu belge ekleme, desteklenen tür, ilerleme |
| S-09 | Belge okuma durumu | Otomatik çıkarımı izlemek | İşlenen belge/sayfa, OCR hatası, tekrar deneme |
| S-10 | Görev Profili istisna paneli | Belirsiz alanları çözmek | Alan, kaynak sayfa, çelişkili kaynak, düzeltme |
| S-11 | Görev Özeti | Görev sağlığını ve aşamayı görmek | Durum, süre, sorular, materyaller, sonraki eylem |
| S-12 | Görevlendirme | Çıkarılan kapsam ve talimatları görmek | Kaynaklı görev profili, alan geçmişi |
| S-13 | Materyal envanteri | Beklenen/alınan dosyaları karşılaştırmak | Çoklu dosya, hash, metadata, eksik/fazla |
| S-14 | Materyal ayrıntısı | Tek dosyanın teknik kaydını incelemek | Orijinal/kopya, süre, codec, kanal, işlem geçmişi |
| S-15 | Ses ve Transkript | Kaydı dinleyip metni denetlemek | Ses tezgâhı, gerçek waveform, segment |
| S-16 | ASR kuyruk durumu | Yerel makine işlemini izlemek | Kuyruk, ilerleme, hata, yeniden deneme |
| S-17 | Dayanak seçici | Birden çok kaynaktan kanıt bağlamak | Arama, ses/segment gruplama, zaman kodu |
| S-18 | Revizyon geçmişi | Uzman düzeltmesini izlemek | Önce/sonra, olay, ses aralığı |
| S-19 | Sorular ve Bulgular | Soruları tek tek yanıtlamak | Her soruya ayrı yanıt ve dayanak |
| S-20 | Tek Rapor / A4 önizleme | Tek ana raporu okumak | Bölümler, sayfalar, kontrol özeti |
| S-21 | Rapor revizyon geçmişi | Önceki rapor sürümünü korumak | Sürüm, tarih, değişiklik özeti |
| S-22 | Uzmanlık Modülleri | Modül kataloğunu görmek | Hazır/kurulu/desteklenmiyor |
| S-23 | 56.12 modül yönetimi | Modülün durumunu yönetmek | Sürüm, kapsam, uyumluluk |
| S-24 | Yerel motor/model yönetimi | ASR paketlerini yönetmek | Kurulum, lisans, checksum, donanım, sürüm |
| S-25 | Uygulama Ayarları | Genel tercihleri değiştirmek | Görünüm, dil, erişilebilirlik, bildirim, güncelleme |
| S-26 | Kasa ve Güvenlik | Şifreli veriyi yönetmek | Kilitle, yedek, geri yükle, parola |
| S-27 | Yardım ve Tanılama | Kullanım/hata desteği | Rehber, sürüm, yerel log ve destek paketi |
| S-28 | Görev kapat/arşivle/sil | Görev yaşam döngüsünü yönetmek | Etki, geri alınabilirlik, yedek uyarısı |
| S-29 | Çevrimdışı ve bağlantı durumu | Yerel çalışmayı anlamak | Model hazır mı, yalnız indirme gereksinimi, ağ durumu |
| S-30 | Genel hata/boş durum sistemi | İşlemde çıkmazı anlamak | Belge, ses, ASR, kasa, rapor ve güncelleme hataları |

### 16.1 Her ekran için tasarım sözleşmesi

Wireframe üretilirken S-01–S-30 ekranlarının her biri için şu bilgiler gösterilmelidir:
- Amaç ve kullanıcı sorusu.
- Giriş noktası ve bir önceki ekran.
- Birincil eylem ve ikincil eylemler.
- Gösterilen veri ve kaynağı.
- Arka planda otomatik yürüyen işlem.
- Kullanıcı doğrulaması gereken istisnalar.
- Başarılı tamamlanma ve çıkış yönü.
- Boş, yükleniyor, hata, çevrimdışı, izin yok ve kurtarma durumu.
- Kasa/görev/veri erişim sınırı.
- Klavye erişimi ve dar pencere davranışı.

## 17. Hata, istisna ve boş durum kataloğu

| Kod | Durum | Beklenen davranış |
|---|---|---|
| E-01 | İlk kullanım / henüz kasa yok | Kasa oluşturma yolunu göster |
| E-02 | Kasa kilitli / yanlış parola | İçerik gösterme; yeniden deneme ve parola sıfırlama sınırını açıkla |
| E-03 | Yedek yok | Yedek oluşturma ve geri yükleme riskini açıkla |
| E-04 | Boş görev listesi | Yeni görevlendirmeyle başlama rehberi |
| E-05 | Belge biçimi desteklenmiyor | Kaynağı koru; desteklenen dönüştürme yolunu açıkla |
| E-06 | PDF sayfası okunamıyor | Belge/sayfa bazlı hata, OCR tekrar/manuel düzeltme |
| E-07 | Görev alanları çelişkili | İki kaynağı göster; otomatik karar verme |
| E-08 | Görev kapsamı/uzmanlık uyumsuz | Analiz yapma; kullanıcı/merci kararına yönlendir |
| E-09 | Beklenen materyal teslim edilmemiş | Eksik materyal olarak işaretle; görevi sessizce tamamlatma |
| E-10 | Ses bozuk veya oynatılamıyor | Kaydı ayrı hata durumuna al; uygulama ve diğer sesler çalışsın |
| E-11 | Kasa açılışında ses geri yüklenemiyor | Hazır/00:00 taklidi yapma; kaynak açılma hatasını göster |
| E-12 | Hash uyuşmuyor | Materyali doğrulanmış sayma; işlem zincirini durdur |
| E-13 | ASR modeli kurulu değil | Modül model kurulumu ekranına yönlendir |
| E-14 | Model checksum/lisans/uyumluluk kontrolü başarısız | Motoru çalıştırma; paket doğrulama hatası |
| E-15 | ASR bir kayıtta başarısız | Diğer dosyaları engelleme; güvenli yeniden deneme |
| E-16 | ASR sırasında uygulama/disk kesintisi | Son güvenli noktadan devam; yinelenen segment oluşturma |
| E-17 | Transkriptte anlaşılmayan bölüm | Tahmin etme; belirsiz segmenti koru |
| E-18 | Dayanak seçici dar pencerede | Geniş modal/yan panel, arama ve filtre |
| E-19 | Soru yanıtsız/dayanak yok | Rapor kalite uyarısı veya gerekli alanda engel |
| E-20 | Başka göreve ait kaynak referansı | Kaynağı reddet; görev izolasyonunu koru |
| E-21 | Rapor biçimi/şablon uyumsuzluğu | Dışa aktarma yolunu “doğrulanmadı” işaretle |
| E-22 | Rapor sayfası/karakter hatası | Önizleme ve dışa aktarma engeli/uyarı |
| E-23 | Güncelleme başarısız | Son çalışan sürümü/kasayı koru; doğrulanmış hata ve kurtarma |
| E-24 | Çevrimdışı, model indirimi gerekiyor | Dosya işleme dışarı çıkmaz; gerekli modeli çevrimdışı aktarım için açıkla |
| E-25 | Kasa diski dolu/bozuk | Kısmi yazmayı tamamlanmış gösterme; kaynak orijinali koru |
| E-26 | Destek paketi hazırlanıyor | İçerik önizleme ve hassas veriyi dışarıda tutma |

Her hata; anlaşılır Türkçe özet, olay kimliği, etkilenen görev/materyal, güvenli sonraki eylem ve mümkün olduğunda teknik ayrıntıyı içermelidir. Kullanıcıya yalnızca “bir hata oluştu” gösterilmesi yeterli değildir.

## 18. Rapor, yöntem ve teknik izlenebilirlik için kaynaklardan çıkan kararlar

### 18.1 Türk mevzuatından gelen zorunluluk

16 Haziran 2025 tarihli konsolide Bilirkişilik Yönetmeliği m.55, bilirkişi raporunda görevlendiren merci, dosya numarası, taraf bilgileri, görevlendirme tarihi ve süresi, inceleme konusu, incelenecek maddi unsurlar, inceleme yöntemi, bilimsel ve teknik dayanaklar, gerekçeli sonuç, rapor tarihi ve bilirkişi kimlik/imza bilgilerini sayar. Aynı maddede incelemeye esas maddi unsurları belgeleyen ve sonucu açıklayan yardımcı kayıtların rapora eklenmesi düzenlenir. Hukukî nitelendirme/değerlendirme yasağı ayrıca korunur.

Bu madde belirli bir ASR marka/model adının her koşulda yazılmasını açıkça söylemez. MİHENK'in rapor politikası, ASR görevin yönteminde fiilen kullanılmışsa model/versiyon bilgisini denetlenebilir biçimde göstermektir; bu, açık mevzuat metninden daha ileri bir ürün şeffaflığı önerisidir.

### 18.2 Adalet Bakanlığı rehber ilkeleri

Bilirkişilerin Uyacağı Rehber İlkeler ve Bilirkişi Raporlarında Bulunması Gereken Standartlar belgesi (6 Nisan 2026 tarihli güncel yayımlanmış PDF):
- Görev kapsamı ve sınırlarına bağlı kalınmasını,
- Soruların tümünün cevaplanmasını,
- Somut nedenlerin/bilimsel verilerin gösterilmesini ve raporun denetime elverişli gerekçe içermesini,
- Açık, anlaşılır, Türkçe ağırlıklı ve gereksiz ayrıntıdan uzak anlatımı,
- Çok soru varsa bölümler ve başlıklar kullanılmasını,
- Sonucun gerekçesinin açıklanmasını
vurgular.

### 18.3 Resmî şablonlar ve tek rapor ilkesi

Bilirkişilik Daire Başkanlığının resmî sayfası hukuk/idare-vergi mahkemeleri, ceza mahkemeleri, Cumhuriyet başsavcılıkları ve icra müdürlükleri için ayrı şablonlar yayımlar. Bu nedenle MİHENK'in tek rapor yaklaşımı, bütün merci türleri için tek sabit form kullanmak anlamına gelmez. Kullanıcı yine tek ana rapor görür; MİHENK görev/merci türüne göre uygun belge yapısını seçer.

### 18.4 Ses incelemesinde teknik dokümantasyon

SWGDE Best Practices for Forensic Audio; materyal kimliği, hash ve teslim zinciri, dosya biçimi/kanal/örnekleme özellikleri, dönüştürme ve kullanılan ekipman/yazılım işlemlerinin kaydını, ayrıca benzer eğitimdeki uzmanın süreci açıklayabilmesine yetecek not tutulmasını önerir. Bu rehber Türk mevzuatı değildir; MİHENK için teknik iyi uygulama referansıdır.

### 18.5 Kaynak bağlantıları

- [16.06.2025 konsolide Bilirkişilik Yönetmeliği — resmî PDF](https://rayp.adalet.gov.tr/resimler/494/dosya/bilirkisilik-yonetmeligi16-06-20254-49-pm.pdf)
- [Bilirkişilerin Uyacağı Rehber İlkeler ve Bilirkişi Raporlarında Bulunması Gereken Standartlar — Adalet Bakanlığı, 06.04.2026 PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260406170009026Bilirkişilerin%20Uyacağı%20Rehber%20İlkeler%20ve%20Bilirkişi%20Raporlarında%20Bulunması%20Gereken%20Standartlar.pdf)
- [Bilirkişi Rapor Şablonları — Bilirkişilik Daire Başkanlığı](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisi-rapor-sablonlari14032022105509)
- [Bilirkişiler İçin Kontrol Listesi — Bilirkişilik Daire Başkanlığı](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisiler-icin-kontrol-listesi14032022105444)
- [SWGDE Best Practices for Forensic Audio](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [Bilirkişilik Temel Eğitimi Kaynak Kitabı duyurusu — Adalet Bakanlığı, 15.05.2025](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisilik-temel-egitimi-kaynak-kitabina-iliskin-duyuru15052025083838)

## 19. Tasarım için karara bağlananlar ve pilotta kanıtlanacaklar

### 19.1 Sistem tasarımında karara bağlananlar

1. Kullanıcı deneyiminin ana birimi görevlendirmedir.
2. Genel Bakış dashboard, Görevlerim ayrı tam liste ekranıdır.
3. Sol gezinme daraltılıp genişletilir.
4. Profil ve uzmanlık alanı avatar/profil alanında; kasa güvenliği ve uygulama ayarları ayrı bölümlerdedir.
5. Uzmanlık alanı, yazılım modülünden ayrıdır.
6. ASR, genel uygulama ayarı değil 56.12 modül altyapısıdır.
7. Motor seçimi normal kullanıcıya her görevde yaptırılmaz; MİHENK doğrulanmış yerel profili yönetir.
8. Görev içinde motor/model adı ve işlem durumu izlenebilir; kullanıcı ses iş akışını teknik motor paneline çevirmek zorunda değildir.
9. Görevlendirme belgesi önce MİHENK tarafından okunur; yalnız istisnalar kullanıcıya sorulur.
10. Bir görevlendirme bir veya çok materyal ve bir veya çok soru taşıyabilir.
11. Her görev kendi izole çalışma alanına ve tek ana raporuna sahiptir.
12. Raporda görev için gerçekten kullanılmış yöntem/ASR aracı okunabilir biçimde açıklanır; tam teknik provenance kayıt altına alınır.
13. MİHENK rapor verisini otomatik birleştirir; bilirkişi kanaatini/yanıtını üretmez.
14. Rapor tek A4 önizleme ve revizyon geçmişiyle kullanıcıya sunulur.
15. UYAP/e-imza/teslim kullanıcının resmî işlemi olarak kalır.
16. Boş, hata, çevrimdışı ve kurtarma durumları ilk wireframe teslimatının zorunlu parçasıdır.

### 19.2 Gerçek pilot veya mühendislik doğrulaması gerektirenler

Bunlar sistem akışında tasarlanmıştır; fakat gerçek uygulama davranışı olarak kanıtlanmış sayılmaz:
- UDF doğrudan okuma ve UYAP Editör'ün güncel sürümünde dışa aktarma/yeniden açma kabulü.
- Hangi belge biçimlerinin metin çıkarım/OCR için güvenilir destekleneceği.
- Yerel ASR motorunun donanım bazında performansı, lisansı ve aynı insan referanslı testteki başarısı.
- Her ASR modeli/runtime/parametre birleşiminin tekrar üretilebilirliği.
- Şifreli kasa, kurtarma, yedekleme ve başarısız güncelleme güvenlik testleri.
- Kasa kilit süresinin hedef cihaz/kullanıcı davranışıyla kabulü.
- Bilirkişi uzmanının rapor içeriği ve teknik yöntem açıklamasını meslekî olarak onaylaması.
- Gerçek Windows UYAP Editör aç/kaydet/yeniden aç ve ilgili Bilirkişi Portal evrak türü kabulü.
- 56.12 uzmanının sentetik/izinli görevde uçtan uca pilot kabulü.

Bu doğrulamalar tamamlanmadan “56.12 kullanıma hazır”, “UYAP'a hazır”, “ASR en iyi motoru seçildi” veya “hukuken onaylı rapor” denmez.

## 20. v0.4 wireframe kabul kapsamı

Sistem tasarımı v1.0 temelinde [Wireframe v0.4](56-12-wireframe-v0.4.md) ve altı görsel pano oluşturuldu. Sistem tasarımı v1.0, v0.4 değerlendirmesi için bilgi mimarisi ve kullanıcı akışının ana kaynağıdır. Wireframe aşağıdaki aşamaları kesintisiz göstermelidir:

1. İlk açılış ve kasa oluşturma.
2. Profil ve uzmanlık alanı.
3. Genel Bakış / Görevlerim ayrımı.
4. Uzmanlık modülleri kataloğu ve 56.12 yönetimi.
5. Yerel ASR/motor yönetimi ile görev içi kuyruk ayrımı.
6. Görevlendirme belgelerini yükleme ve otomatik okuma.
7. Kaynaklı Görev Profili istisnalarını doğrulama.
8. Bir görevde çoklu materyal envanteri.
9. Ses/ASR/transkript ve uzman revizyonları.
10. Çoklu soru ve kaynak/dayanak bağlantıları.
11. Tek raporun tam A4 sayfa önizlemesi.
12. Kasa, yedek, geri yükleme ve kilitleme.
13. Uygulama ayarları, güncelleme, yardım/tanılama.
14. Boş/hata/çevrimdışı/başarısız işlem/kurtarma ekranları.

Wireframe v0.3 kabul edilmiş tasarım olarak kullanılamaz. v0.4 bu sistem sözleşmesine göre yeniden çizilecek; kullanıcı kabulü olmadan uygulama arayüzü kodlanmayacaktır.

---


## v0.5 tasarım düzeltmeleri — 15.11.2026

Kullanıcı değerlendirmesinde v0.4'ün bazı alt alanları ve görevler arası geçişleri yeterince açık göstermediği görüldü. v0.5 aşağıdaki akış sözleşmesini getirir:

- Profildeki **Uzmanlık Alanlarım**, **Uzmanlık Modülleri** ve seçili modülün **Motorlar ve Modeller** yönetimi ayrı yerlerdir.
- 56.12 motor/model seçimi görev içinde yapılmaz. Testi geçmiş etkin yerel çalışma profili modül ayarlarında yönetilir; görev işleme sırasında otomatik kullanılır ve her çalışmanın gerçek sürümü kaydedilir.
- Yeni görevlendirme, ilk belgeyle otomatik kaydolmuş taslak görevdir. Zorunlu wizard değildir. Belge okuma/alan çıkarma başlar; materyaller ilk adımda veya daha sonra eklenebilir. Görevlerim'e dönüş her zaman mümkündür.
- Ses çalışma alanı bütün kayıtları ve bütün transkripti erişilebilir tutar. Öncelik kuyruğu çoklu kalite işaretlerinden üretilir; güven işareti kesin doğruluk oranı değildir.
- Konuşmacı ayrımı opsiyonel, kayıt içi etiketli ve uzman kontrolündedir; kişi kimliği belirleme işlevi değildir.
- Orijinal ses değişmez. Gürültü azaltma/iyileştirme gibi işlemler yalnız türetilmiş kopyaya uygulanır ve teknik izi saklanır.
- ASR segmentleri editörün zamanlı çalışma birimleridir. Rapor dökümü okunabilir, zaman damgalı paragraflar hâlinde birleştirilir.
- Her görevde tek ana rapor + ekler vardır. Merciye göre ilgili yayımlanmış örnek rapor iskeleti otomatik eşleştirilir; mevzuatta tek ve evrensel zorunlu şablon varmış gibi sunulmaz. Tüm sorular sırayla, gerekçeli ve kaynak bağlantılı olmalıdır.

v0.5 görsel değerlendirme kaynağı: [Wireframe v0.5](56-12-wireframe-v0.5.md). v0.4 tarihsel taslak olarak korunur. Kullanıcı/uzman kabulü olmadan uygulama UI koduna başlanmaz.


## v0.5 kabulü ve kalite/denetim eki

Proje sahibi [Wireframe v0.5](56-12-wireframe-v0.5.md) tasarımını 15.11.2026 tarihinde kabul etti. Tasarım uygulama backlog'una dönüştürülebilir; bu durum mevcut prototipteki işlevlerin tamamlandığını göstermez. Uygulama geliştirmesi mevcut kodun dosya/branch/test denetimiyle başlayacaktır.

Bilirkişinin görev ve rapor öz denetimi, bağımsız dosya/rapor incelemesi ve MİHENK'in kendi ürün kalite denetimi için ayrı kanıt katmanları [Kalite Güvencesi ve Denetim Modeli v1.0](56-12-kalite-ve-denetim-modeli-v1.0.md) içinde tanımlanmıştır.
