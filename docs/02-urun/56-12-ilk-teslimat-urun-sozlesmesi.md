# MİHENK 56.12 — İlk Teslimat Ürün Sözleşmesi

> İlk kullanılabilir teslimat: 56.12 Ses Kayıtlarının Metne Dönüştürülmesi kontrollü pilotu. Uzun vadeli ürün: modüler MİHENK bilirkişilik platformu.  
> Güncel tasarım adayı: [Wireframe v0.5 — ekran açıklamaları](56-12-wireframe-v0.5.md) · [Sistem haritası](mihenk-sistem-ve-kullanici-akisi-v1.0.md)

> **Tasarım durumu:** v0.3 ve v0.4 kabul edilmemiş tarihsel taslaklardır. v0.5 proje sahibi tarafından 15.11.2026 tarihinde kabul edilmiştir ve uygulama tasarım temelidir. 56.12 alan uzmanı, teknik, güvenlik ve UYAP kabul kapıları ayrıca geçilmelidir.

## Ürün hedefi

Bilirkişi MİHENK'i kurar, yerel kasasını açar ve bilirkişi profilini bir kez tanımlar. Görevlendirme belgesini ve materyalleri ekler. MİHENK belgeyi okuyup görev profilini çıkarır; sesleri envanterler ve yerel ASR taslağı üretir; uzman düzeltmelerini ve bulgularını görev sorularına bağlar; görev için tek ana bilirkişi raporu hazırlar. Bilirkişi son kontrolü, UYAP Editör/e-imza ve resmî Portal teslimini kendisi yapar.

Bu kapsam UYAP portal otomasyonu, e-imza PIN'inin alınması veya bilirkişi adına teknik/hukukî kanaat üretimi değildir.

## Kavram modeli

- Yerel kasa verinin şifreli saklama ve kurtarma sınırıdır.
- Bilirkişi profili kullanıcıya ait meslekî bilgilerdir; kasanın içinde şifreli saklanır.
- Uzmanlık alanı kullanıcının profil bilgisidir; yazılım modülü ile aynı şey değildir.
- Uzmanlık modülü MİHENK'in sunduğu araç ve iş akışıdır. İlk aktif modül 56.12'dir.
- Bir bilirkişinin birçok ayrı görevlendirmesi olabilir.
- Bir görevlendirme belgesi bir görev profili üretir; görev çoklu materyal ve çoklu soru içerir.
- Her görev için ayrı çalışma alanı ve tek ana rapor vardır; görev verileri birbirine karışmaz.

## Genel menü ve görev alanı

Sol menü daraltılıp genişletilebilir. Genel menü: Genel Bakış, Görevlerim, Uzmanlık Modülleri, Ayarlar ve Kasa. Kullanıcı avatar menüsünden Bilirkişi Profilim, Uzmanlık Alanlarım, Kasa ve Güvenlik, Güncelleme ve Kilitle eylemlerini açar.

Genel Bakış yalnızca iş özeti sunar. Görevlerim her ayrı görevlendirmeyi listeler. Bir görev açıldığında sağ içerikte o göreve ait Görev Özeti, Görevlendirme, Materyaller, Ses ve Transkript, Sorular ve Bulgular, Tek Rapor sekmeleri görünür.

## Görevlendirme başlangıcı ve otomasyon

Görevlendirme belgesi ilk girdi olarak yüklenir. MİHENK metin çıkarımı/OCR adımlarını yürütür; merci, dosya referansı, tarih/süre, kapsam, sorular, materyal ve teslim koşullarını kaynak iziyle çıkarır. Kullanıcı baştan form doldurmaz; yalnız belirsiz, çelişkili veya okunamayan alanları doğrular. Belirsiz süre veya kapsam sistem tarafından uydurulmaz.

Güvenli/tekrarlı işlemler varsayılan olarak otomatik yürür. ASR çıktısı makine taslağıdır; uzman düzeltmesi ve nihai kanaat ayrı tutulur.

## Tek rapor

Her görevlendirme için bir ana rapor üretilir. Rapora görev/merci bilgileri, bilirkişi profili, kapsam/sınırlar, sorular, materyal envanteri, yöntem/araç/model/sürüm, uzman tarafından doğrulanmış bulgular, soru bazlı gerekçeli yanıtlar, sınırlılıklar ve numaralı ekler alınır. Kullanıcı ayrı ayrı rapor formatları arasında seçim yapmak zorunda kalmaz; tek rapor MİHENK içinde önizlenir.

Bilirkişilik Temel Eğitimi Kaynak Kitabı raporlar için özel ve değişmez tek şablon bulunmadığını; örneklerin ihtiyatla kullanılması gerektiğini belirtir. MİHENK görevlendirme içeriği ve güncel rehberle uyumlu görev-özel rapor oluşturur; önceki rapordan kopyalama yapmaz.

## UYAP Editör sınırı

Tek raporun güncel Windows UYAP Editör'de açılması, Türkçe karakter/sayfa/tablo/ek kontrolü, UDF kaydetme ve yeniden açma testi tamamlanmadan çıktı "UYAP'a hazır" olarak sunulmaz. Portal evrak türünün kabul ettiği biçim ayrıca doğrulanır. E-imza ve resmî gönderim bilirkişinin işlemi olarak kalır.

## İlk sürüm kabul kapıları

1. Yerel kasa ve bilirkişi profili ilk açılışta kurulur; sonraki açılışta yalnız kasa açılır.
2. Profil rapora doğru aktarılır; uzmanlık alanı ile yazılım modülü ayrıdır.
3. Görevlendirme belgesi okunur; alanlar kaynak iziyle çıkarılır; istisnalar kullanıcıya sorulur.
4. Birden fazla görevlendirme ayrı saklanır.
5. Bir görevde birden fazla ses ve soru işlenir.
6. Kasa yeniden açıldığında görev ve seçili ses bağlamı geri yüklenir.
7. Yerel ASR kuyruğu, transkript düzeltme ve revizyon geçmişi çalışır.
8. Her soru yanıtı aynı görevin kaynaklarına bağlanır.
9. Görev başına tek rapor oluşturulur ve MİHENK içinde önizlenir.
10. Tek rapor UYAP Editör'de aç/kaydet/yeniden aç kabulünü geçer.
11. Windows MSI temiz kurulum, kasa, kapanma, güncelleme, başarısız güncelleme ve kurtarma testlerini geçer.
12. 56.12 uzmanı sentetik/izinli görevde akışı tamamlar.

Derleme ve birim test başarısı tek başına pilot kabulü değildir. Her kapı kanıtla GEÇTİ/KALDI/ENGELLENDİ olarak kaydedilir.


## Sistem ve kullanıcı akışı tasarım kaynağı

Profil, uzmanlık alanı/modül ayrımı, kasa ve uygulama ayarları, daraltılabilir genel gezinme, Görevlerim/Genel Bakış ayrımı, ASR modül yönetimi, görev içi çoklu materyal/soru akışları, tek rapor ve hata durumları için ana tasarım referansı [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](mihenk-sistem-ve-kullanici-akisi-v1.0.md) belgesidir. Bu belge wireframe v0.5 için sistem ve kullanıcı akışı referansıdır; önceki taslaklar kabul edilmiş değildir ve UI kodlama onayı değildir.

### ASR ve rapor yönteminin açıklanması

ASR, genel uygulama ayarı değil 56.12 uzmanlık modülünün yerel altyapısıdır. Görev ekranı motoru yönetmez; motorun hazır olma, kuyruk, hata ve kullanılan sürüm bilgisini gösterir. Normal kullanıcıya her görevde motor seçtirilmez.

ASR fiilen kullanılmışsa, raporun inceleme yöntemi/teknik araçlar bölümünde kullanılan motor/model adı ve sürümü kısa, anlaşılır ve gerçeğe uygun biçimde açıklanır. Tam runtime, build, parametre, checksum, materyal-run eşlemesi ve revizyon kökeni teknik işlem kaydında; denetim için gerektiğinde teknik ekte tutulur. Mevzuat m.55 inceleme yöntemi ve bilimsel/teknik dayanakları sayar; belirli bir ASR markasını açıkça zorunlu tutmaz. Model bilgisinin açıklanması, MİHENK'in denetlenebilirlik ve şeffaflık ürün politikasıdır.

MİHENK raporun yapısını ve doğrulanmış içeriğini otomatik birleştirir; bilirkişinin teknik kanaatini, konuşmanın hukukî anlamını veya soru yanıtını uydurmaz. Makine taslağı, bilirkişi kontrolünden geçmeden nihai transkript olarak gösterilmez.


## v0.5 kullanıcı iş akışı ve ses çalışma tezgâhı

Yeni görevlendirme katı bir wizard değildir. İlk görevlendirme belgesi eklendiğinde otomatik kaydedilen taslak oluşur; belge çıkarımı ve beklenen materyal tespiti otomatik yürür. Ses ve diğer materyaller ilk kabul sırasında veya daha sonra görev içindeki Materyaller alanından eklenebilir. Görev listesine dönüş ve taslağı yeniden açma her zaman mümkündür.

Ses ve Transkript alanı bir görevin bütün kayıtlarını listeler. Kontrol kuyruğu düşük model güveni, gürültü, örtüşme, ses kesilmesi, konuşma/metin boşluğu ve bilirkişi işaretleri gibi nedenlerle önceliklendirilir; bu işaretler gerçek doğruluk yüzdesi sayılmaz. Bilirkişi her zaman tüm kaydı dinleyebilir ve tüm metni arayabilir.

Konuşmacı diarization isteğe bağlıdır; Konuşmacı A/B gibi kayıt içi etiketler uzman tarafından kontrol edilir ve gerçek kişi kimliği iddiası değildir. Ses iyileştirme orijinal dosyaya uygulanmaz; türetilmiş kopya, parametre ve işlem geçmişiyle saklanır.

ASR segmentleri düzenleme ve sese saniye hassasiyetli atlama birimidir. Rapor dökümü mikro-segmentleri satır satır kopyalamaz; konuşmacı sırası ve zaman aralığı korunmuş okunabilir paragraflar oluşturur. Uzun transkript aynı ana raporun ekinde sunulabilir.

## v0.5 rapor biçimi ilkesi

Her görevlendirme için tek ana rapor ve ona bağlı ekler vardır. Merci/dosya türü görevlendirme belgesinden çıkarılır ve uygun Bakanlık örnek raporu referans iskelet olarak otomatik eşleştirilir; belirsizlik varsa bilirkişiden yalnız bu alanı doğrulaması istenir. Bu, tüm bilirkişi raporları için tek ve zorunlu bir resmî şablon bulunduğu iddiası değildir. Raporda görevlendirmenin soruları sırayla, gerekçeli ve kaynaklarıyla yanıtlanır. Gerçek UYAP Editör aç/kaydet/yeniden aç testi tamamlanmadan çıktı “UYAP'a hazır” olarak adlandırılmaz.


## Kalite, denetim ve son kontrol

56.12'de bilirkişinin kendi görev/rapor kontrolü, ikinci bilirkişi veya yetkili denetçinin bağımsız dosya incelemesi ve MİHENK ürününün kendi kalite denetimi birbirinden ayrılır. Her görev için kaynak → materyal → ses/ASR → uzman düzeltmesi → soru/yanıt → rapor revizyonu izlenebilir olmalıdır. Gerektiğinde hassas verisi kullanıcı tarafından gözden geçirilmiş salt okunur denetim paketi hazırlanır. Ürün sürümü için ayrıca test kanıtı, açık risk, bağımlılık/model sürümü ve platform kabul dosyası tutulur.

Detaylı sözleşme: [56.12 Kalite Güvencesi ve Denetim Modeli v1.0](56-12-kalite-ve-denetim-modeli-v1.0.md). Bu model mevcut uygulamada tamamlanmış özellik değildir; uygulama backlog'una ve pilot kabul kapılarına dönüştürülecektir.
