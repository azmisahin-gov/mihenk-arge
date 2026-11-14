# MİHENK — Kullanıcı Deneyimi ve Ekran Tasarımı v0.5

> **Durum:** Kullanıcı geri bildirimi üzerine hazırlanmış yeni tasarım adayı. v0.4'ün yerine değerlendirilmek üzere sunulur; henüz kabul edilmedi.  
> **Tarih:** 15 Kasım 2026  
> **Sınır:** Bu doküman ve SVG panoları ürün tasarımıdır. Uygulama UI kodlama onayı, ASR motoru seçimi veya UYAP uyumluluk kabulü değildir.

## 1. Bu sürümde neyi değiştirdik?

v0.4'te sistemin çok sayıda alanını aynı anda göstermeye çalışırken bazı alt alanların nerede başladığı, bir işlemden sonra nereye geçildiği ve bilirkişinin asıl işine nasıl odaklandığı yeterince açık değildi. v0.5 bu nedenle ekran sayısını çoğaltmak yerine altı pano ile ana akış ve gezinme davranışı sadeleştirilip netleştirildi:

1. Profildeki meslekî uzmanlık, MİHENK modülü ve modülün motor/model ayarı birbirinden ayrıldı.
2. Yeni görevlendirme sabit adımlı, geri dönüşü zor bir wizard olmaktan çıkarıldı. Belge alındığında taslak görev kaydı oluşur; otomasyon başlar; materyaller aynı anda veya daha sonra eklenebilir.
3. Görev ana ekranı, kullanıcının bir sonraki işini gösteren bir çalışma özeti oldu.
4. Ses ve transkript ekranı birincil çalışma alanı olarak tasarlandı: çoklu kayıt listesi, kontrol önceliği, dalga biçimi, ses dinleme araçları ve tam transkript tek yerde.
5. Tek rapor ekranı, merciye göre oluşturulmuş rapor iskeletinin gerçek A4 önizlemesini ve rapor kalite kontrolünü birlikte gösterir.

Bu tasarımın hedefi bilirkişinin motor/altyapı yönetmesi değil; ASR'nin kontrol işaretlerine göre önce dinlenecek bölümleri hızlıca düzeltmesi, kendisinden istenen soruları cevaplaması ve tam biçimlendirilmiş tek raporu kontrol etmesidir.

## 2. Altı görsel pano

SVG'ler vektörel çizimdir; büyütülebilir ve tarayıcıda açılabilir.

### 01 — Modül ve motor hiyerarşisi

[01 Modül ve motor hiyerarşisi panosunu aç](wireframe-v0.5-01-modul-ve-motor-hiyerarsisi.svg)

- **Bilirkişi Profilim → Uzmanlık Alanlarım:** kişinin meslekî alanı, sicil ve yetkinlik bilgileridir.
- **Uzmanlık Modülleri:** MİHENK'in sunduğu yazılım iş akışlarıdır. İlk aktif modül 56.12'dir.
- **56.12 → Motorlar ve Modeller:** Whisper ailesi, SEDA ve diğer aday motorların test/kurulum/sürüm/lisans/donanım yönetimidir.
- **Ses Araçları:** dinleme, kanal seçimi, ses iyileştirme ve teknik görünüm ayarları.
- **Dil ve Metin:** konuşma algılama, noktalama ve isteğe bağlı konuşmacı ayrımı gibi yardımcı bileşenler.

Bunlar aynı menü öğesi değildir. Bilirkişi profilde meslekî uzmanlık alanlarını tanımlar; modül kataloğunda 56.12 iş akışına girer; ASR motorlarını da bu modülün altındaki altyapı alanında yönetir.

**Görev içinde motor seçtirilmez.** Testi geçip etkinleştirilmiş bir yerel çalışma profili varsa sistem yeni görevlendirmelerde onu otomatik kullanır. Motor/model ve sürüm her gerçek çalışma kaydına otomatik yazılır. Testi geçmemiş Whisper, SEDA veya başka adaylar üretim motoru gibi gösterilmez. SEDA'nın mevcut prototipte bulunması onun en iyi motor olduğunun kanıtı değildir.

### 02 — Yeni görevlendirme: wizard değil, otomatik kabul akışı

[02 Yeni görevlendirme akışı panosunu aç](wireframe-v0.5-02-yeni-gorevlendirme-akisi.svg)

Önerilen akış:

1. Bilirkişi **Görevlerim → Yeni görevlendirme** yolunu açar.
2. Görevlendirme yazısını ve varsa ek talimat belgelerini bırakır.
3. İlk belge eklendiğinde MİHENK bir taslak görev kaydı oluşturur ve otomatik metin çıkarımı/OCR başlar.
4. Sistem merci, dosya numarası, tarih/süre, inceleme konusu, sorular ve talep edilen materyalleri kaynağıyla çıkarır.
5. Uzman yalnızca okunamayan, eksik, çelişkili veya belirsiz alanları doğrular. Sistem bu alanları tahminle doldurmaz.
6. Belge bir ses kaydını veya ek materyali tarif ediyorsa beklenen materyal listesi oluşturulur.
7. Ses/video/diğer materyaller ilk ekranda yüklenebilir; yüklenmemiş olanlar daha sonra görev içindeki **Materyaller** alanına eklenebilir.
8. Taslak her aşamada saklanır. Kullanıcı görevler listesine dönebilir, başka göreve geçebilir ve daha sonra bu taslağa geri gelebilir.

**Bu bir zorunlu ileri-geri sihirbaz değildir.** Dört başlık ilerleme durumunu gösterir; kullanıcıyı tüm materyalleri ilk ekranda bulmaya veya sıradaki adım bitmeden devam etmemeye zorlamaz. Görev kaydı oluşturulması, bütün materyallerin teslim alındığı anlamına gelmez. Beklenen/teslim alınan materyaller farkı görev alanında açıkça görünür.

### 03 — Görev çalışma alanı

[03 Görev çalışma alanı panosunu aç](wireframe-v0.5-03-gorev-calisma-alani.svg)

Her görevlendirmenin kendi çalışma alanı ve kendi materyal/soru/rapor bağlamı vardır. Görev içi sekmeler:

- Görev Özeti
- Görevlendirme
- Materyaller
- Ses ve Transkript
- Sorular ve Bulgular
- Tek Rapor

Görev Özeti kullanıcıya sıradaki işleri gösterir: örneğin kontrol bekleyen ses parçaları, görevlendirme alanı istisnaları, yanıtsız sorular ve rapor durumu. Kullanıcıyı ayar ekranına göndermek yerine doğrudan ilgili işe götürür.

Görevlerim ana menüden her zaman erişilebilir. Bir göreve girildiğinde yalnız o göreve ait sesler, transkriptler, dayanaklar, sorular ve rapor gösterilir.

### 04 — Ana ses inceleme tezgâhı

[04 Ana ses inceleme tezgâhı panosunu aç](wireframe-v0.5-04-ana-ses-inceleme-tezgahi.svg)

Bu, 56.12'nin en yoğun ve en önemli çalışma ekranıdır. Bir görevde tek bir ses de çok sayıda ses kaydı da olabilir. Ekran bu nedenle üç ana bölgeden oluşur:

**Sol — kayıtlar ve kontrol sırası**
- Görevdeki bütün ses kayıtları listelenir; süreleri ve işleme/kontrol durumları görünür.
- Varsayılan görünüm, kontrol edilmesi gereken bölümleri öncelik sırasına dizer.
- Kullanıcı tüm segmentlere, kontrol edilmiş segmentlere, belirsizlere ve konuşmacı işaretlerine filtre uygulayabilir.
- Kuyruk, diğer kayıtları gizlemez. Her zaman bir kaydın başından sonuna dinleme ve tam transkript görünümüne geçiş vardır.

**Orta — ses ve metin**
- Dalga biçimi üzerinde yakınlaştırma, kaydırma ve seçili zaman aralığı bulunur.
- Ses oynatıcıda oynat/duraklat, birkaç saniye geri/ileri, hız ayarı, A–B aralığı döngüsü ve seçili parçayı tekrar dinleme bulunur.
- Transkript satırı/paragrafı seçildiğinde ilgili ses aralığına gidilir; ses oynatıldığında ilgili transkript bölümü takip edilir.
- Uzman metni doğrudan düzeltebilir; özgün ASR taslağı ve uzman düzeltme geçmişi ayrı tutulur.
- Tüm transkript görüntülenebilir ve aranabilir; yalnızca sorun işaretlenmiş parçalar gösterilmez.

**Sağ — dinleme ve teknik araçlar**
- Orijinal ve işlenmiş dinleme kopyası arasında karşılaştırma yapılabilir.
- Gürültü azaltma, kanal seçme, spektrogram ve benzeri araçlar ayrı/geri alınabilir çalışma kopyası üzerinde çalışır.
- Orijinal kanıt dosyası değiştirilmez. İşlenmiş her kopyanın aracı, sürümü ve ayarları kayıt altına alınır.
- Ses iyileştirme, duyulmayan kelimeyi üretmek veya kayıtta olmayan bilgiyi eklemek için kullanılmaz. İşlem konuşmayı daha anlaşılır kılmıyorsa uzman orijinal kayda dönebilir.

**Kontrol kuyruğu sadece ASR'nin boş bıraktığı bölümlerden oluşmaz.** Aşağıdaki işaretler birlikte kullanılır:
- düşük model güveni,
- sesin çok düşük veya gürültülü olması,
- üst üste konuşma,
- konuşma algılama ile metin arasında olası boşluk,
- kesilme/bozulma,
- dil veya kelime belirsizliği,
- bilirkişinin elle işaretlediği bölüm.

Bu işaretler **gerçek doğruluk yüzdesi değildir**. Yalnızca nereden başlanmasının daha yararlı olacağına dair kontrol önceliğidir. Bilirkişi isterse bütün kaydı baştan sona inceleyebilir.

**Konuşmacı ayrımı**
- Çoklu konuşmacı olduğu düşünülen kayıtlarda sistem isteğe bağlı diarization/konuşmacı gruplama yapabilir.
- Başlangıçta kimlik değil, “Konuşmacı A”, “Konuşmacı B” gibi kayıt içi etiketler kullanılır.
- Bilirkişi etiketleri birleştirebilir, ayırabilir veya belirsiz olarak işaretleyebilir.
- Ses yeterli değilse ya da konuşmalar örtüşüyorsa sistem zorla bir konuşmacı atamaz.
- Konuşmacı etiketi gerçek kişinin kimliğini belirlediği anlamına gelmez. Ses karşılaştırma/kimliklendirme 56.12'nin otomatik işlevi değildir.

**Segment ile rapor paragrafı farklı amaçlara sahiptir**
- ASR segmentleri çalışma tezgâhında saniye hassasiyetli düzenleme, arama ve sese atlama içindir.
- Her küçük ASR segmentinin raporda ayrı satır olması gerekmez.
- Nihai döküm, konuşmacı sırası ve zaman ilişkisi korunarak okunabilir paragraflara birleştirilir. Zaman damgası, her paragraf/konuşma aralığı başında ya da gerekli aralıklarda gösterilir.
- Uzun dökümler, tek raporun eki olarak kayıt bazında düzenlenir; kısa dökümler rapor içindeki ilgili bölümde yer alabilir. Görevlendirmenin talebi belirleyicidir. Hiçbir durumda metnin tamamı kaybolmaz ve segment-zaman bağlantısı teknik kayıtta korunur.

### 05 — Tek rapor ve gerçek A4 önizleme

[05 Tek rapor A4 panosunu aç](wireframe-v0.5-05-tek-rapor-a4.svg)

Her görev için tek ana rapor vardır. Ana rapor, ilgili görevlendirme ve doğrulanmış çalışma verilerinden oluşturulur; ekler aynı rapor paketinin parçasıdır. Kullanıcı farklı rapor türleri arasında dolaşmak zorunda kalmaz.

Raporun temel veri başlıkları:
1. Görevlendirmeyi yapan merci ve dosya bilgileri.
2. Bilirkişi bilgileri.
3. Görev tanımı, incelemenin kapsamı ve sorulan sorular.
4. İncelenen materyaller ve kayıt bazında teknik tanımlama.
5. İnceleme yöntemi, bilimsel/teknik dayanaklar ve gerçekten kullanılan araçlar.
6. Bulgular ve gözlemler.
7. Görevlendirmedeki sırayı izleyen, gerekçeli soru yanıtları.
8. Sonuç.
9. Gerekli dökümler, teknik kayıtlar ve ilgili belgelerden oluşan ekler.
10. Tarih ve bilirkişi imza alanı.

Bu başlıklar rapor verisinin tasarım temelidir; merci ve görev türüne göre başlıkların sırası/adı, sayfa düzeni ve ek yerleşimi uyarlanır. Otomatik oluşturma bilirkişinin meslekî kanaatini, eksik sorunun yanıtını veya kayıtta duyulmayan kelimeyi üretmez.

**“Resmî format” konusu için önemli ayrım**

Adalet Bakanlığı Bilirkişilik Daire Başkanlığının sitesinde hukuk/idare-vergi mahkemeleri, ceza mahkemeleri, Cumhuriyet başsavcılıkları ve icra müdürlükleri için ayrı örnek rapor şablonları yayımlanmıştır. Bununla birlikte Bakanlığın Bilirkişilik Temel Eğitimi Kaynak Kitabı, bilirkişi raporları için mevzuattan kaynaklanan tek ve özel bir zorunlu şablon bulunmadığını; örnek raporlara ihtiyatla yaklaşılması gerektiğini belirtir. Bu nedenle MİHENK'in tasarım kararı şudur:

- Sistem, görevlendirme belgesindeki merci ve dosya türünden uygun Bakanlık örneğini **referans iskelet** olarak otomatik eşleştirir.
- Bu eşleştirme, “Bakanlığın tek zorunlu resmî şablonu” iddiası değildir.
- Merci/tür belirsizse kullanıcıya yalnız bu belirsizlik sorulur; rastgele bir şablon seçilmez.
- Raporun biçim ve içeriği güncel mevzuat, rehber standartlar ve görevlendirme kapsamına göre doğrulanır.
- Rapor, tüm sayfaları ve ekleriyle A4 biçiminde önizlenir. Sayfa numarası, başlık, altbilgi, tablo bölünmesi, Türkçe karakterler, kenar boşlukları ve imza alanı gerçek çıktı üzerinde test edilir.
- UYAP Editör'de açma/kaydetme/yeniden açma testi geçmeyen bir çıktı “UYAP'a hazır” olarak etiketlenmez.
- UYAP Portal'a giriş, imza ve raporu gönderme bilirkişinin kontrolünde kalır.

### 06 — Ana menünün geniş ve dar hâli

[06 Daraltılabilir ana menü panosunu aç](wireframe-v0.5-06-daraltilebilir-ana-menu.svg)

Sol menü daraltıldığında aynı öğeler ve aynı sıralama korunur; yalnız metin etiketleri gizlenir. Aktif öğe renk/arka planla belirgin kalır, ikon üzerinde bekleme araç ipucu açar, klavye erişimi ve erişilebilir adlar korunur. Tercih sonraki açılışta hatırlanır. Böylece Görevlerim'e dar menüden de tek tıklamayla dönülür; yeni bir gezinme hiyerarşisi öğrenmek gerekmez.


## 3. Kullanıcının sorularına doğrudan tasarım cevabı

| Soru | v0.5 kararı |
|---|---|
| Uzmanlık alanım ile modül aynı mı? | Hayır. Uzmanlık alanı profil bilgisidir; 56.12 yazılım modülüdür. |
| Motor/model nereden seçilir? | Uzmanlık Modülleri → 56.12 → Motorlar ve Modeller. Her görevde yeniden seçilmez. |
| Yeni görev wizard mı? | Hayır. Taslak oluşturan, otomatik kaydeden ve her zaman geri dönülebilen kabul akışıdır. |
| Materyal en başta eklenmek zorunda mı? | Hayır. Şimdi veya daha sonra eklenebilir; sistem beklenen ve teslim alınanları izler. |
| ASR'nin yalnız yapamadıkları mı gösterilir? | Hayır. Tüm kayıt ve metin erişilebilir; kontrol kuyruğu ilk bakışta sorunlu bölümlere öncelik verir. |
| Konuşmacı ayrımı var mı? | İhtiyaç ve kalite uygunsa opsiyonel gruplama vardır; uzman kontrol eder; kimlik iddiası değildir. |
| Ses iyileştirme var mı? | Dinleme araçları ve geri alınabilir işlenmiş kopyalar tasarlanır; orijinal korunur, bütün işlemler kaydedilir. |
| Rapor segmente göre mi yazılır? | Hayır. Segment çalışma birimidir; rapor okunabilir, zaman damgalı konuşmacı paragrafları sunar. |
| Sol menüyü daraltınca ne olur? | Menü öğeleri kaybolmaz; aynı sıradaki ikonlar, aktif durum, araç ipucu ve klavye erişimi korunur. |
| Tek rapor ne anlama gelir? | Tek ana rapor ve aynı pakette gerekli ekler; görev başına bir güncel rapor ve revizyon geçmişi. |
| Resmî şablon nasıl seçilir? | Merci/türden otomatik referans şablon eşleştirme; belirsizlik varsa tek teyit. |

## 4. Rapor biçimi ve dayanak kaynakları

Bu tasarım aşağıdaki kamuya açık kaynakları dikkate alır:

- [Adalet Bakanlığı — Bilirkişi Rapor Şablonları](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisi-rapor-sablonlari14032022105509): farklı merci türleri için örnek rapor şablonları.
- [Adalet Bakanlığı — Bilirkişilik Temel Eğitimi Kaynak Kitabı](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20042022182631temel%20egitim%20kitab%C4%B1.pdf): raporun eksiksiz, anlaşılır ve inandırıcı olması; tüm soruların sırayla ve gerekçeli yanıtlanması; yöntem ve teknik dayanağın açıklanması; örnek raporların ihtiyatla ele alınması.
- [Bilirkişilerin Uyacağı Rehber İlkeler ve Rapor Standartları](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/18072025143049Bilirki%C5%9Filerin%20Uyaca%C4%9F%C4%B1%20Rehber%20%C4%B0lkeler%20ve%20Bilirki%C5%9Fi%20Raporlar%C4%B1nda%20Bulunmas%C4%B1%20Gereken%20Standartlar.pdf): bilimsel/teknik gerekçe, denetlenebilirlik, açık dil, görev sınırları.
- [SWGDE Best Practices for Forensic Audio v2.5 (9 Haziran 2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/): ses kanıtının işlenmesi, teknik özelliklerin ve işlemlerin belgelenmesi, sonuçların sunulması.
- [SWGDE Best Practices for Enhancement of Digital Audio v2.0 (27 Şubat 2025)](https://www.swgde.org/documents/published-complete-listing/20-a-001-2/): ses iyileştirme sürecinin değerlendirme ve tekrar üretilebilirlik ilkeleri.

SWGDE, Türkiye'de bağlayıcı hukuk kuralı değildir; ses inceleme sürecine ilişkin teknik iyi uygulama kaynağı olarak kullanılır.

## 5. v0.5 kabul kontrol listesi

### Anlaşılabilirlik
- [ ] Profildeki meslekî uzmanlık alanları, modül kataloğundan görsel ve işlevsel olarak ayrılıyor.
- [ ] 56.12 sayfasında motor/model ayarının hangi alt alanda olduğu açık.
- [ ] Görev ekranında normal kullanıcıya motor seçimi yaptırılmıyor.
- [ ] Sol menü daraltıldığında ikon, aktif durum, araç ipucu ve klavye erişimi korunuyor.

### Görevlendirme
- [ ] Yeni görev bir taslak olarak hemen kaydoluyor.
- [ ] Belge çıkarımı otomatik başlıyor ve kaynağa geri izlenebiliyor.
- [ ] Materyal ilk ekranda da, daha sonra da eklenebiliyor.
- [ ] Görev listesine dönme ve taslağı yeniden açma yolu sürekli görünür.

### Ses ve transkript
- [ ] Birden fazla kayıt aynı ekranda yönetilebiliyor.
- [ ] Kontrol kuyruğu nedenini açıklıyor ve tüm segmentlere erişimi engellemiyor.
- [ ] Ses ve transkript zaman bakımından eşleşiyor.
- [ ] Dinleme, yavaşlatma, tekrar, A–B, kanal ve spektrogram araçlarının davranışı test ediliyor.
- [ ] Orijinal kayıt değişmiyor; işlenmiş kopya ve işlem geçmişi ayrılıyor.
- [ ] Konuşmacı gruplama isteğe bağlı, düzenlenebilir ve kimlik iddiasından arındırılmış.
- [ ] Uzman düzeltmeleri, ham ASR metni ve revizyon geçmişi birbirinden ayrılıyor.

### Tek rapor
- [ ] Tek rapor görevlendirme merciine göre doğru referans iskeletle hazırlanıyor.
- [ ] Tüm sorular görevlendirmedeki sırayla ve kaynak bağlantısıyla rapora giriyor.
- [ ] Transkript okunabilir paragraflara dönüştürülüyor; zaman izleri kaybolmuyor.
- [ ] Uzun transkript ilgili rapor ekinde kayıt bazında yer alıyor.
- [ ] Tüm A4 sayfaları ve ekler uygulama içinde tam önizleniyor.
- [ ] UYAP Editör aç/kaydet/yeniden aç ve gerçek çıktı kabul testleri tamamlanmadan “UYAP'a hazır” denmiyor.

**Kabul durumu:** Bu liste kullanıcının ve mümkünse 56.12 alan uzmanının değerlendirmesi için hazırlanmıştır. Hiçbir kutu kullanıcı/uzman testi yapılmış gibi işaretlenmemiştir. Kullanıcı v0.5'i kabul etmeden uygulama arayüzü kodlamasına başlanmayacaktır.

---
