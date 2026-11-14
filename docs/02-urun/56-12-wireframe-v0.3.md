# 56.12 — Kullanıcı Deneyimi ve Ekran Tasarımı v0.3

> **Durum:** v0.2'nin yerine geçen, ilk kullanımdan tek rapor önizlemesine kadar yeniden düzenlenmiş ürün taslağı.  
> **Tarih:** 15.11.2026  
> **Görsel:** [Wireframe v0.3 — tam ekran panosu](56-12-wireframe-v0.3.svg)

> **ÖNEMLİ:** Bu v0.3 taslağı proje sahibi tarafından kabul edilmiş nihai tasarım değildir. Kullanıcı, genel yönü önceki sürümlere göre daha anlaşılır buldu ancak görsel tasarım ve kullanım kolaylığı konusunda hâlâ tereddüt bildirdi. Yeni oturumda bu taslak yeniden gözden geçirilecek; profil, kasa, uzmanlık/modül ilişkisi, gezinme ve rapor önizlemesi netleşmeden uygulama UI'sı bu taslağa göre kesinleştirilmeyecektir.

## 1. Önce beş kavramı ayıralım

| Kavram | Anlamı | Nerede yönetilir? |
|---|---|---|
| **Yerel kasa** | Bilgisayardaki şifreli veri alanı; profil ve görevleri korur | İlk kurulum; Kasa ve Güvenlik |
| **Bilirkişi profili** | Kullanıcının ad, sicil, unvan ve meslekî bilgileri | Avatar → Bilirkişi Profilim |
| **Uzmanlık alanı** | Bilirkişinin kendi profilinde belirttiği temel/alt uzmanlıklar | Profil → Uzmanlık Alanlarım |
| **Uzmanlık modülü** | MİHENK'in o uzmanlık için sunduğu iş akışı ve araçlar | Sol menü → Uzmanlık Modülleri |
| **Görevlendirme** | Mahkeme/merci tarafından verilen tek inceleme işi | Görevlerim → Görevi Aç |

Profildeki uzmanlık alanı kullanıcının beyan ettiği meslekî bilgidir; MİHENK'in sicili veya yetkinliği resmî olarak doğruladığı anlamına gelmez. Yazılım modülü ise uygulama yeteneğidir. Kullanıcının bir uzmanlık alanına sahip olması, o alana ait MİHENK modülünün hazır olduğu anlamına gelmez.

**İlk ürün kapsamı:** İlk kullanılabilir uzmanlık modülü 56.12'dir. Kullanıcı profilinde birden fazla uzmanlık saklanabilir; görevlendirme belgesindeki uzmanlık ihtiyacı ile kurulu modül eşleştirilir. Desteklenmeyen uzmanlıkta sistem analiz yapmış gibi davranmaz, kapsam dışı olduğunu bildirir.

## 2. İlk kurulum ve sonraki açılış

### İlk kez kullanırken
1. Yerel kasayı oluşturur ve parola belirler.
2. Bilirkişi profilini bir kez doldurur.
3. Uzmanlık alanlarını tanımlar.
4. MİHENK'te kullanılabilir modül olan 56.12'yi görür/etkinleştirir.
5. Genel Bakış'a geçer.

### Sonraki açılışlarda
Kullanıcı çevrimiçi bir hesaba giriş yapmaz; yerel kasanın kilidini açar. Profilini tekrar oluşturmaz.

- **Yerel kasa:** şifreleme, kilitleme, yedekleme ve geri yükleme.
- **Bilirkişi profili:** sabit meslekî kimlik ve uzmanlık bilgileri.
- **Uygulama ayarları:** görünüm, dil, bildirim ve güncelleme tercihleri.

Kasa parolası UYAP parolası veya e-imza PIN'i değildir. Profil verisi şifreli kasada saklanır. İlk sürüm için bir kasa/bir bilirkişi profili varsayımı korunur; aynı Windows hesabında çoklu yerel profil desteği ayrıca tasarlanıp test edilmeden vaat edilmez.

## 3. Sol menü: daraltılabilir ve sade

Sol menü geniş durumda yaklaşık 230 px, dar durumda yaklaşık 68 px olur. Dar görünümde simgeler kalır; üzerine gelince metin ipucu gösterilir. Son görünüm tercihi saklanır.

**Genel menü:**
- Genel Bakış
- Görevlerim
- Uzmanlık Modülleri
  - 56.12 · Ses kayıtlarının metne dönüştürülmesi
- Ayarlar ve Kasa

Alt bölümdeki kullanıcı/avatar alanı şu seçenekleri açar:
- Bilirkişi Profilim
- Uzmanlık Alanlarım
- Kasa ve Güvenlik
- Güncelleme / uygulama bilgisi
- Kasayı Kilitle

Böylece profil, kasa ve uygulama ayarları tek bir genel formda toplanmaz. Profil avatar menüsünden açılır; kasa güvenliği ayrı sayfada yönetilir.

## 4. Genel Bakış ile Görevlerim birbirinden farklıdır

### Genel Bakış (Dashboard)
Yalnızca iş özeti gösterir: devam eden görevler, materyal işlemi bekleyenler, rapor kontrolü bekleyenler, doğrulanmış yaklaşan tarihler ve son açılan görevlendirmeler. Ana eylem **Yeni görevlendirme**. Bu ekranda görev adımları veya materyal düzenleme bulunmaz.

### Görevlerim
Her satır/kart birbirinden ayrı bir görevlendirmedir. Aynı bilirkişinin eşzamanlı birçok mahkeme/merci işi olabilir. Her görevde merci, yerel görev adı, dosya referansı, doğrulanmışsa son tarih, materyal sayısı ve iş durumu görünür. Kullanıcı bir görevi açtığında o görevin çalışma alanına geçer; başka görevlerin verisi karışmaz.

## 5. Yeni görevlendirme: önce belgeyi MİHENK okur

Kullanıcı görevlendirme yazısını/kararını, ek talimatı ve varsa teslim/dizi pusulasını ekler. Kullanıcıdan bütün alanları baştan elle doldurması beklenmez.

MİHENK:
1. Kaynak belgeleri özgün haliyle korur.
2. Desteklenen belge biçimlerinde metni çıkarır; taranmış belge için uygun OCR/okuma adımını yürütür.
3. Merci, dosya referansı, görevlendirme tarihi, süre ve başlangıç olayı, inceleme konusu/kapsam/sınırlar, sorular, istenen materyaller ve teslim koşulları için aday alanlar çıkarır.
4. Her alanı kaynak belge/sayfa/konum bilgisine bağlar.
5. Okunamayan, çelişen veya yorum gerektiren alanları istisnaya alır.
6. Kullanıcıya kısa sonuç gösterir: “9 alan bulundu; 1 alanı doğrulamanız gerekiyor.”

**Kullanıcı belgeyi baştan okuyup form doldurmaz.** Yalnızca belirsiz/çelişkili/okunamayan alanları doğrular. Süre başlangıç olayı açık değilse sistem kesin son tarih uydurmaz. Kaynak belge ve kullanıcının düzeltmesi alan geçmişinde tutulur.

## 6. Bir görevin içinde çoklu materyal ve çoklu soru

Görevlerim listesinden açılan her işin kendi çalışma alanı olur. Başlıkta görev/merci, süre ve o göreve atanmış uzmanlık modülü görünür.

Görev sekmeleri:
- Görev Özeti
- Görevlendirme
- Materyaller
- Ses ve Transkript
- Sorular ve Bulgular
- Tek Rapor

Bir görevlendirmede bir veya çok ses kaydı, ek belge ve birden çok soru olabilir. Materyal envanteri her dosyayı ayrı izler; hepsi aynı göreve bağlı kalır. ASR kuyruğu o göreve bağlı sesleri otomatik işler; kullanıcı her dosya için başka bir program açmaz.

Her görev sorusunun ayrı yanıtı ve dayanakları olur. Dayanak seçimi arama yapılabilir liste/tablo şeklindedir; küçük, yatay kaydırılan bir kutu değildir.

## 7. Tek rapor: oluştur ve aynı ekranda önizle

Kullanıcı **Tek raporu oluştur** dediğinde o göreve ait şu içerikler tek ana dokümanda birleştirilir:

- Görev ve merci bilgileri.
- Bilirkişi profilinden ilgili kimlik/uzmanlık alanları.
- İnceleme konusu, kapsamı ve sınırları.
- İncelenen tüm materyallerin envanteri.
- Yöntem, teknik dayanak, araç/model/sürüm ve parametreler.
- Uzman tarafından doğrulanmış bulgular.
- Görev sorularının her birine gerekçeli yanıt.
- Sınırlılıklar ve numaralı ekler.

Kullanıcı ayrı ayrı DOCX/ODT/JSON raporu seçmez. Raporun tamamı MİHENK içindeki belge önizlemesinde görünür: solda bölüm listesi, ortada sayfa, sağda kontrol özeti. Bu tek ana rapordur; ek listeleri ve kaynak referansları aynı rapora bağlanır. Büyük ses dosyaları raporun içine gömülmez, envanter ve zaman kodlarıyla ilişkilendirilir.

SVG panosundaki örnek rapor içeriği yer tutucu metindir; gerçek raporun yalnızca uzman tarafından doğrulanmış görev verilerini kullanması gerekir. Önizleme durumu **Taslak / Uzman onayı bekliyor** olur.

## 8. Resmî rapor içeriği ve UYAP Editör

Bilirkişilik Yönetmeliği m.56/1 kapsamında raporda merci, dosya numarası, taraf bilgileri, görevlendirme tarihi/süresi, inceleme konusu, incelenmesi istenen maddi unsurlar, yöntem, bilimsel/teknik dayanaklar, gerekçeli sonuç, düzenleme tarihi ve gerçek kişi bilirkişinin ad/soyad/unvan/sicil/imza bilgileri gibi hususlar yer alır. Mayıs 2025 Temel Eğitim Kaynak Kitabı raporlar için özel ve değişmez bir tek şablon bulunmadığını, örneklere ihtiyatla yaklaşılması ve önceki raporun kopyalanmaması gerektiğini belirtir.

Bu sebeple MİHENK tek bir sabit Bakanlık formunu taklit etmez; görevlendirme içeriğine ve güncel rehbere dayalı görev-özel rapor üretir.

UYAP resmî indirme sayfası Windows için v5.4.20'yi listeliyor. Resmî Editör yardımı UDF'nin varsayılan kayıt biçimi olduğunu, DOC/ODT/PDF/RTF gibi biçimlere dışa aktarma seçeneklerinin bulunduğunu açıklıyor. MİHENK'in ürettiği dosya güncel Windows Editör'de aç/kaydet/yeniden aç testini geçmeden **“UYAP'a hazır”** etiketi gösterilmez. E-imza ve Portal gönderimi bilirkişinin işlemidir.

## 9. Wireframe v0.3'te gösterilen ekranlar

1. İlk açılış: yerel kasa → bilirkişi profili → uzmanlık alanı/modül.
2. Genel Bakış: görev adımları değil, iş özeti; daraltılabilir sol menü ve profil popover'ı.
3. Yeni görevlendirme: belge ekleme, otomatik okuma ve yalnız istisnaları doğrulama.
4. Görev çalışma alanı: çoklu ses materyali ve çoklu soru.
5. Tek rapor: tek belge önizlemesi, rapor özeti ve doğrulama durumu.

## 10. Tasarım kabul maddeleri

- [ ] Sol menü daralır/genişler; dar görünümde simgeler için etiket ipucu vardır.
- [ ] Avatar menüsü profil ve uzmanlık bilgilerine ulaşır.
- [ ] Yerel kasa, bilirkişi profili ve uygulama ayarları farklı işlevlerdir.
- [ ] Profildeki uzmanlık alanı ile yazılım modülü birbirinden ayrıdır.
- [ ] İlk kullanılabilir modül 56.12 olarak görünür.
- [ ] Dashboard sadece özet, Görevlerim ayrı görevlendirme listesidir.
- [ ] Görevlendirme belgesini önce MİHENK okur; kullanıcı yalnız istisnaları doğrular.
- [ ] Bir görevde birden fazla materyal ve soru görünür.
- [ ] Her göreve ait tek ana rapor üretilir.
- [ ] Tek raporun tamamı aynı ekranda önizlenir.
- [ ] UYAP Editör uyumluluğu gerçek testten önce vaat edilmez.

## Kaynaklar

- [Görevlendirme Belgesinin İşlenmesi ve Görev Profili](gorevlendirme-belgesi-ve-gorev-profili.md)
- [Bütünleşik Uzmanlık Modülü Mimarisi](../04-mimari/butunlesik-uzmanlik-modul-mimarisi.md)
- [Alan Modeli](../04-mimari/alan-modeli.md)
- [56.12 Minimum Sürüm Kapsamı](../03-uzmanlik-modulleri/ilk-pilot/56-12-minimum-surum-kapsami.md)
- [Bilirkişilik Temel Eğitimi Kaynak Kitabı, Mayıs 2025](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/15052025204011Bilirkis%CC%A7ilik%20Temel%20E%C4%9Fitimi%20Kaynak%20Kitab%C4%B1.pdf)
- [UYAP Editör resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
- [Windows UYAP Editör indirme sayfası](https://www.uyap.gov.tr/Uyap-Editor)
- [UYAP Editör güncelleme duyurusu, 11.06.2026](https://www.uyap.gov.tr/uyap-dokuman-editoru-guncellendi)
