# MİHENK 56.12 — İlk Teslimat Ürün Sözleşmesi

> İlk kullanılabilir teslimat: 56.12 Ses Kayıtlarının Metne Dönüştürülmesi kontrollü pilotu. Uzun vadeli ürün: modüler MİHENK bilirkişilik platformu.  
> Güncel tasarım: [Wireframe v0.3 — ekran açıklamaları](56-12-wireframe-v0.3.md) · [SVG ekran panosu](56-12-wireframe-v0.3.svg)

> **Tasarım durumu:** Wireframe v0.3 çalışma taslağıdır; proje sahibi tarafından henüz kabul edilmemiştir. Bu sözleşme ilk teslimat yönünü ve iş hedefini kaydeder; son UI yerleşimi olarak yorumlanmamalıdır. Yeni oturumda kullanıcı akışı yeniden gözden geçirilmelidir.

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
