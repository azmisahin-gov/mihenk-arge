# MİHENK — Kullanıcı Deneyimi ve Ekran Tasarımı v0.4

> **Durum:** Sistem haritası v1.0 temelinde hazırlanmış, sekiz görsel panolu wireframe taslağı. Kullanıcı kabulü ve alan uzmanı değerlendirmesi bekleniyor.  
> **Tarih:** 15 Kasım 2026  
> **Önemli:** Bu belge ve SVG'ler ürün tasarım taslağıdır; tamamlanmış görsel tasarım veya uygulama UI kodlama onayı değildir.

## 1. Tasarımın amacı

Wireframe v0.4, MİHENK'in yalnızca ana ekranlarını değil, bilirkişinin ilk kurulumdan görevlendirme, materyal, ses incelemesi, soru/kanıt, tek rapor, güvenlik, güncelleme ve hata kurtarmaya kadar karşılaşacağı temel ekranları ve durumları görünür kılar.

Bu tasarım, [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](mihenk-sistem-ve-kullanici-akisi-v1.0.md) belgesini ana bilgi mimarisi olarak kullanır. v1.0'da karara bağlanmış sahiplik sınırlarını yeniden tartışmaya açmaz; onları masaüstü arayüzüne dönüştürür.

### Tasarım ilkeleri

1. Ana iş birimi görevlendirmedir; kullanıcı görev açar, MİHENK o görevin materyallerini, sorularını ve raporunu aynı çalışma alanında tutar.
2. İlk kurulumda ana sol menü gösterilmez. Önce kasa, ardından profil ve uzmanlık alanları tamamlanır; sonra uygulama kabuğu açılır.
3. Sonraki açılışta profil/uzmanlık kurulumu tekrarlanmaz; kullanıcı yerel kasanın kilidini açar.
4. Profil, uzmanlık alanı, yazılım modülü, kasa ve uygulama ayarları farklı sahiplik alanlarıdır.
5. Yerel ASR, 56.12 modül yönetiminde ayarlanır; görev içinde yalnızca kuyruk, ilerleme ve sonuç gösterilir.
6. Görevlendirme belgesini önce MİHENK okur. Kullanıcı yalnızca belirsiz/çelişkili/eksik alanları çözer.
7. Bir görevin çoklu materyali ve çoklu sorusu açıkça görünür; dayanaklar aynı görevdeki kaynaklara bağlıdır.
8. Her görevin tek ana raporu vardır. Raporun tamamı sayfa sayfa önizlenir; rapor biçimi seçtirilmez.
9. Makine taslakları ve otomatik kontroller bilirkişinin meslekî kararının yerine geçmez.
10. Boş, hata, çevrimdışı ve kurtarma durumları normal ekranların eşit derecede önemli parçalarıdır.

## 2. Wireframe panoları

SVG'ler vektörel çizimdir; büyütülebilir, tarayıcıda açılabilir ve gerektiğinde tasarım aracıyla içe aktarılabilir.

### 01 — Kurulum ve ana gezinme

[SVG panosunu aç](wireframe-v0.4-01-kurulum-ve-ana-gezinme.svg)

İçerik:
- İlk karşılama: yeni yerel kasa veya şifreli yedekten devam et.
- Kasa oluşturma ve sonraki açılışta kasa kilidini açma.
- İlk profil ve uzmanlık alanı sihirbazı.
- Kasa/profil tamamlandıktan sonra görünen Genel Bakış ve ana gezinme.

**Önemli düzenleme:** İlk kurulum ekranlarında ana sol menü yoktur. Kasa oluşturma ve profil tanımı yapılırken henüz açılmamış çalışma alanının menüsü gösterilmez.

### 02 — Gezinme, modül ve ayarlar

[SVG panosunu aç](wireframe-v0.4-02-goz-atma-modul-ve-ayarlar.svg)

İçerik:
- Görevlerim: arama, filtre ve görev satırları.
- Uzmanlık Modülleri: 56.12 ilk aktif modül; desteklenmeyen modüller.
- 56.12 Yerel İşleme Altyapısı: motor/model durumu, lisans, checksum, donanım ve çevrimdışı hazırlık.
- Uygulama Ayarları: görünüm, erişilebilirlik, dil/bölge, bildirim, açılış, kısayol ve güncelleme tercihleri.
- Kasa ve Güvenlik ayrı ana bölüm olarak açılır; yedek/geri yükleme panosu 05 ve 06'dadır.

### 03 — Görevlendirme ve materyal kabulü

[SVG panosunu aç](wireframe-v0.4-03-gorevlendirme-ve-materyaller.svg)

İçerik:
- Birden fazla görevlendirme/teslim belgesinin eklenmesi ve otomatik okunması.
- Kaynak sayfası gösterilen tekil istisna doğrulama paneli.
- Görev Özeti ve görev aşamaları.
- Beklenen, teslim alınan, işlenen ve iade edilen materyallerin karşılaştırıldığı envanter.

### 04 — Ses inceleme, bulgu ve tek rapor

[SVG panosunu aç](wireframe-v0.4-04-inceleme-ve-tek-rapor.svg)

İçerik:
- Çoklu ses listesi, gerçek ses dalga biçimi, zaman çizgisi, oynatma, sarma ve tekrar.
- Aynı görevdeki transkript segmentlerinin kontrol durumu.
- Ham ASR ile uzman düzeltmesinin ayrılması ve revizyon kaydı.
- Çoklu görev sorusu, yanıt durumu ve dayanak bağlantısı.
- Tek ana rapor: bölüm listesi, A4 sayfa görünümü ve kalite kontrol paneli.

### 05 — Dayanak, güvenlik ve istisna durumları

[SVG panosunu aç](wireframe-v0.4-05-dayanak-ve-isletim-durumlari.svg)

İçerik:
- Dar kutu yerine geniş ve aranabilir dayanak seçici.
- Şifreli yedek oluşturma/geri yükleme.
- Yerel yardım ve tanılama.
- Boş, belge hatası, çelişki, model doğrulama hatası, ses geri yükleme hatası ve rapor engeli galerisi.

### 06 — Yaşam döngüsü ve kurtarma

[SVG panosunu aç](wireframe-v0.4-06-yasam-dongusu-ve-kurtarma.svg)

İçerik:
- Görev kapatma, arşivleme ve silme arasındaki fark.
- Tek raporun revizyon geçmişi.
- Çevrimdışı durumda yerel model paketi hazır değilse davranış.
- Başarısız uygulama güncellemesi ve kullanıcı kontrollü tanılama.

### 07 — Gezinme, profil ve materyal ayrıntıları

[SVG panosunu aç](wireframe-v0.4-07-gezinme-profil-materyal-guvenlik.svg)

İçerik:
- Daraltılmış sol menü, ikon ipuçları ve avatar menüsü.
- İlk kurulumdan sonra profil/uzmanlık alanı düzenleme.
- Tek materyalin dosya kimliği, orijinal/kopya, hash, teknik metadata ve işlem geçmişi.
- Kasa parolası, otomatik kilit, yedek ve geri yükleme yönetimi.

### 08 — Uygulama ayarları ve güncellemeler

[SVG panosunu aç](wireframe-v0.4-08-uygulama-ayarlari-ve-guncellemeler.svg)

İçerik:
- Tema, yazı boyutu, erişilebilirlik, kontrast ve hareket tercihi.
- Dil/bölge, tarih/saat, yerel bildirim ve açılış davranışı.
- Uygulama güncelleme kanalı ve doğrulama.
- Uygulama sürümü, lisanslar, yardım ve tanılama.
- Uygulama güncellemesi ile 56.12 modül/model güncellemesinin ayrılması.

## 3. Ekran kataloğu ve görsel eşlemesi

Sistem tasarımı v1.0'daki S-01–S-30 kimlikleri korunur. Bir kimlik bağımsız tam ekran, bir sayfa içi panel, modal veya durum görünümü olabilir; her kimliğin ayrı bir menü öğesi olması gerekmez.

| Kimlik | Ekran | v0.4 görseli / durum |
|---|---|---|
| S-01 | İlk karşılama | 01 / Karşılama |
| S-02 | Kasa oluştur | 01 / Kasa oluşturma bölümü |
| S-03 | Bilirkişi profili | 01 / Kurulum sihirbazı; 07 / Profil düzenleme |
| S-04 | Uzmanlık alanlarım | 01 / Kurulum sihirbazı; 07 / Profil düzenleme |
| S-05 | Kasa aç | 01 / Mevcut kasayı aç bölümü |
| S-06 | Genel Bakış | 01 / Ana uygulama kabuğu |
| S-07 | Görevlerim | 02 / Görev listesi |
| S-08 | Yeni görevlendirme / belge yükle | 03 / Belge yükleme |
| S-09 | Belge okuma durumu | 03 / Belge işleme ve istisna |
| S-10 | Görev Profili istisna paneli | 03 / Kaynak sayfalı istisna |
| S-11 | Görev Özeti | 03 / Görev aşamaları |
| S-12 | Görevlendirme | 03 / Görev Profili doğrulama |
| S-13 | Materyal envanteri | 03 / Envanter |
| S-14 | Materyal ayrıntısı | 07 / Teknik ayrıntı ve bütünlük |
| S-15 | Ses ve Transkript | 04 / Ses çalışma tezgâhı |
| S-16 | ASR kuyruk durumu | 04 / Kayıt listesi ve işlem durumları |
| S-17 | Dayanak seçici | 05 / Geniş arama/seçim |
| S-18 | Transkript revizyon geçmişi | 04 / Ham ve uzman metni |
| S-19 | Sorular ve Bulgular | 04 / Soru listesi |
| S-20 | Tek Rapor / A4 önizleme | 04 / Tek rapor |
| S-21 | Rapor revizyon geçmişi | 06 / Rapor v1-v3 |
| S-22 | Uzmanlık Modülleri | 02 / Modül kataloğu |
| S-23 | 56.12 modül yönetimi | 02 / Modül kataloğu ve yönetim |
| S-24 | Yerel motor/model yönetimi | 02 / 56.12 motor yönetimi |
| S-25 | Uygulama Ayarları | 02 / Kategori listesi; 08 / Alt ekranlar ve güncellemeler |
| S-26 | Kasa ve Güvenlik | 05 / Yedek; 07 / parola ve otomatik kilit; 06 / kurtarma |
| S-27 | Yardım ve Tanılama | 05 / Yardım; 08 / uygulama bilgisi ve tanılama |
| S-28 | Görev kapat/arşivle/sil | 06 / Görev yaşam döngüsü |
| S-29 | Çevrimdışı ve bağlantı durumu | 02 / Model yönetimi; 06 / çevrimdışı durumu |
| S-30 | Genel hata/boş durum sistemi | 05 / Durum galerisi; 06 / güncelleme hatası |

## 4. Ana gezinme ve ekran sahipliği

### 4.1 Ana sol menü

Geniş ve dar görünümde aynı hiyerarşi korunur:
- Genel Bakış
- Görevlerim
- Uzmanlık Modülleri
- Kasa ve Güvenlik
- Uygulama Ayarları
- Yardım ve Tanılama (yardımcı bağlantı veya alt gezinme)

Profil menüsü:
- Bilirkişi Profilim
- Uzmanlık Alanlarım
- Kasayı kilitle (hızlı eylem)

Profil menüsü kasa ayarlarını içine almaz. Kasa ve Güvenlik ayrı, Uygulama Ayarları ayrı kalır.

### 4.2 Görev içi gezinme

Görevin üst başlığında merci/görev referansı ve görev durumu görülür. Görev içi sekmeler:
- Görev Özeti
- Görevlendirme
- Materyaller
- Ses ve Transkript
- Sorular ve Bulgular
- Tek Rapor

Görev değiştirildiğinde önceki görevden seçili ses, segment, soru, dayanak araması veya rapor bağlamı yeni göreve taşınmaz.

## 5. ASR ekranının kesin yerleşimi

ASR genel uygulama ayarı değildir.

**Yönetim yeri:** Uzmanlık Modülleri → 56.12 → Yerel İşleme Altyapısı → Motor ve Model.

Burada motorun/modelin kurulumu, sürümü, lisansı, checksum, donanım uyumluluğu, çevrimdışı hazır olma, güncelleme, onarım ve geri alma yönetilir.

**Görev içi yer:** Görev → Ses ve Transkript. Kullanıcı burada sadece kayıt kuyruğunu, işlem durumunu, ilerlemeyi, hatayı ve yeniden denemeyi görür.

Normal kullanıcıya her görevde motor seçtirilmez. MİHENK doğrulanmış yerel profili yönetir. Gelişmiş motor profili seçimi yalnız doğrulanmış adaylar için ve gerekçe/run kaydıyla sağlanır. SEDA bir deneme motorudur; bu taslak onu üretim kazananı ilan etmez.

## 6. Tek rapor ekranı için etkileşim sözleşmesi

- Rapor ekranında tek ana rapor vardır. Format seçici yoktur.
- Sol bölüm listesi, ortada gerçek A4 sayfası, sağda kalite kontrol paneli bulunur.
- A4 önizleme tüm sayfaları göstermeli; sayfa numarası, sayfalar arasında geçiş, yakınlaştırma ve tam genişlik görünümü desteklenmelidir.
- Raporun her bölümü görevlendirme, materyal, transkript veya bilirkişi yanıtı gibi kaynaklarına geri bağlanabilmelidir.
- Bölüm içeriği düzenlenecekse öncelik ilgili görev verisini düzeltmek ve rapor revizyonunu yeniden üretmektir; rapor görünümündeki metin düzenlemesi kaynak veriden kopuk ikinci bir gerçek oluşturmamalıdır.
- Rapor yeniden oluşturulursa eski sürüm silinmez; tek güncel rapor ve geçmiş revizyonlar bulunur.
- Kalite paneli GEÇTİ / UYARI / ENGELLENDİ ayrımını ve her maddenin nedenini gösterir.
- ASR kullanılmışsa gerçek motor/model adı ve sürümü yöntem bölümünde anlaşılır biçimde gösterilir. Tam runtime, build, parametre, checksum ve materyal-run eşlemesi teknik işlem kaydında/uygun teknik ekte kalır.
- Teknik ek, aynı ana raporun parçası olabilir; ikinci bir rapor veya kullanıcıya seçtirilen ayrı rapor formatı değildir.
- “Uzman onayı bekliyor” durumu, resmî teslim veya imza gerçekleşmiş gibi sunulmaz.

## 7. Ekranlar arası normal akış

1. İlk açılış: Karşılama → Yerel kasa oluştur → Profil → Uzmanlık alanları → Genel Bakış.
2. Sonraki açılış: Kasa kilidini aç → Genel Bakış.
3. Yeni görev: Görevlerim → Yeni görevlendirme → Belgeleri ekle → Otomatik okuma → Yalnız istisnaları doğrula → Görev alanı.
4. Materyal: Beklenen/alınan karşılaştır → Çoklu dosya içe al → hash/metadata/okunabilirlik → işleme kuyruğu.
5. Ses: Yerel ASR → taslak → dinleyerek düzeltme → belirsiz segment → uzman kontrolü.
6. Sorular: Her soruya yanıt → aynı görevin kaynaklarına bir veya çok dayanak.
7. Rapor: Tek raporu oluştur → kalite kontrolleri → sayfa sayfa önizleme → düzeltme → yeni rapor revizyonu → bilirkişi son kontrolü.
8. Resmî teslim: Bilirkişi kendi resmî araçlarıyla UYAP Editör/e-imza/Portal işlemini yürütür; MİHENK otomatik gönderim yapmaz.

## 8. Boş, hata ve kurtarma davranışları

Wireframe'de her işlem için yalnız başarılı durum gösterilmesi yeterli değildir. Aşağıdaki durumlar tasarımın zorunlu kapsamıdır:

| Durum | Ekran davranışı |
|---|---|
| Kasa yok | Karşılama ve kasa oluşturma |
| Kasa kilitli | Parola ekranı; görev içeriği kapalı |
| Yanlış parola | İçerik açılmaz; güvenli yeniden deneme |
| Boş görev listesi | İlk görevlendirmeyi başlatan açıklama |
| Belge biçimi desteklenmiyor | Orijinal korunur, izinli dönüştürme yolu anlatılır |
| OCR/okuma hatası | Belge ve sayfa düzeyinde hata gösterilir |
| Alan çelişkisi | İki kaynak yan yana; sistem kendi kendine seçim yapmaz |
| Eksik materyal | Beklenen/alınan farkı gösterilir |
| Hash uyumsuzluğu | Materyal doğrulanmış sayılmaz |
| Ses geri yükleme hatası | Kayıt hazır gibi gösterilmez; 00:00 yanıltıcı süre olarak kullanılmaz |
| Model eksik/uyumsuz | ASR başlamaz; modül yönetimine yönlendirme |
| ASR dosya hatası | Diğer başarılı kayıtlar devam eder |
| ASR kesintisi | Son güvenli noktadan devam; yinelenen sonuç yok |
| Belirsiz transkript | Tahminle doldurulmaz; tekrar dinleme/uzman işareti |
| Dayanak bulunamadı | Geniş arama, görev içi kaynak filtresi |
| Başka görevden kaynak | Bağlantı reddedilir |
| Yanıtsız soru | Rapor kalite kontrolünde açık uyarı/engel |
| Rapor biçimi doğrulanmamış | “UYAP'a hazır” etiketi verilmez |
| Güncelleme hatası | Son çalışan sürüm/kasa korunur; güvenli tekrar deneme |
| Çevrimdışı / model eksik | Yerel görevler görünür, ASR modeli hazır olana kadar bekler |
| Yedek bozuk | Geri yükleme tamamlanmaz; mevcut kasa korunur |
| Destek paketi | Kullanıcı içeriği inceler; hassas görev verisi varsayılan dışarıda |

## 9. Tasarımın henüz kesinleştirmediği teknik/saha konuları

Görsel tasarımda bir durumun gösterilmesi, alttaki teknik işlevin kabul testini geçtiği anlamına gelmez.

- Gerçek belge türlerinin kabul matrisi ve OCR başarısı.
- UDF doğrudan okuma ve UYAP Editör gerçek aç/kaydet/yeniden aç testi.
- ASR model/runtime/lisans/checksum/donanım karşılaştırması ve üretim adayı seçimi.
- Şifreleme, yedek, geri yükleme, kasa kilidi ve otomatik kilit süresi için güvenlik testi.
- Görev sonrası saklama/silme/iade yükümlülüklerinin görev türüne göre doğrulanması.
- Rapor şablonunun merci ve görev türüne göre doğru eşleşmesi.
- Bilirkişinin yöntem açıklaması, teknik ek ve nihai rapor yapısına meslekî onayı.
- Heyet görevlendirmesi ve çoklu profil desteğinin sonraki kapsamı.

Bu başlıklarda UI doğru belirsizliği göstermeli; test edilmemiş yetenek “hazır” gibi sunulmamalıdır.

## 10. Wireframe v0.4 kabul kontrol listesi

### Sistem ve gezinme
- [ ] İlk kurulum ana menüden ayrı.
- [ ] Sonraki açılış kasa kilidiyle başlıyor.
- [ ] Sol menü daraltılıp genişletilebiliyor.
- [ ] Avatar profil/uzmanlık bilgilerini yönetiyor.
- [ ] Kasa, profil, uzmanlık alanı, modül ve uygulama ayarları ayrılmış.
- [ ] Genel Bakış ile Görevlerim ayrı sayfalar.

### Görevlendirme ve çalışma alanı
- [ ] Belge önce MİHENK tarafından okunuyor.
- [ ] Kullanıcı yalnız istisnaları doğruluyor; kaynak sayfa gösteriliyor.
- [ ] Bir görev içinde çoklu materyal ve çoklu soru görünür.
- [ ] Beklenen/alınan/işlenen/iade edilen envanter ayrılmış.
- [ ] Ses, transkript ve inceleme kuyruğu aynı modülde bağlı.
- [ ] Dayanak seçici dar kutu değil; arama ve çoklu seçim destekli.

### Modül ve ASR
- [ ] ASR ayarları Uygulama Ayarları'nda değil, 56.12 modül yönetiminde.
- [ ] Görev içi ekran motor ayarı değil, kuyruk/işlem görünümü.
- [ ] Model adı/sürüm ve run geçmişi izlenebilir.
- [ ] SEDA kesin kazanan olarak gösterilmiyor.
- [ ] Çevrimdışı ve model eksik durumu tasarımlı.

### Tek rapor
- [ ] Her görevde tek ana rapor.
- [ ] Rapor biçimi seçtirilmiyor.
- [ ] Tüm A4 sayfaları önizlenebiliyor.
- [ ] Bölüm listesi, kalite kontrolü ve kaynak bağlantıları mevcut.
- [ ] ASR kullanımı yöntem bölümünde gerçeğe uygun açıklanıyor.
- [ ] Teknik provenance rapor/teknik kayıtla ilişkilendiriliyor.
- [ ] Önceki rapor revizyonları korunuyor.
- [ ] Bilirkişi onayı ve resmî teslim birbirinden ayrı.

### Hata ve güvenlik
- [ ] Boş/hata/çevrimdışı/kurtarma durumları gösteriliyor.
- [ ] Görev arşivleme ile veri silme birbirinden ayrılmış.
- [ ] Kasa yedek ve geri yükleme ekranı mevcut.
- [ ] Güncelleme başarısızlığı mevcut sürüm ve veriyi koruyor.
- [ ] Destek/diagnostic paketi hassas materyali otomatik dışarı çıkarmıyor.

**Kabul şartı:** Bu kontrol listesi kullanıcı ve gerektiğinde 56.12 alan uzmanıyla gözden geçirilmeden wireframe tamamlandı sayılmaz. Kullanıcı kabulü alınmadan uygulama UI kodlamasına geçilmez.

---
