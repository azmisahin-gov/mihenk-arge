# MİHENK 56.12 — İlk Teslimat Ürün Sözleşmesi

> İlk kullanılabilir teslimat: 56.12 Ses Kayıtlarının Metin Hâline Dönüştürülmesi kontrollü pilotu.  
> Uzun vadeli ürün: modüler MİHENK bilirkişilik platformu.  
> Tasarım referansı: [Wireframe v0.2](56-12-wireframe-v0.2.md) · [SVG pano](56-12-wireframe-v0.2.svg)

## Ürün hedefi

Bilirkişi MİHENK'i kurar, yerel profilini bir kez tanımlar, görevlendirme belgesini ve delil materyallerini ekler. MİHENK belgeyi okuyup görevlendirme alanlarını çıkarır; ses materyallerini envanterler ve yerel olarak transkripsiyon taslağı üretir; uzman düzenlemesini ve bulgularını görev sorularına bağlar; tek ana bilirkişi raporunu hazırlar. Bilirkişi son kontrolü yapar ve UYAP Editör/e-imza/Portal üzerinden resmî imzalama ve gönderimini kendisi tamamlar.

Bu kapsam UYAP portal otomasyonu, e-imza PIN'inin uygulamaya alınması veya otomatik teknik/hukukî kanaat üretimi değildir.

## Kavram modeli

- Bir yerel kasa bir bilirkişi profiline bağlıdır (ilk sürüm varsayımı).
- Bir bilirkişinin birçok ayrı görevlendirmesi olabilir.
- Bir görevlendirme bir belge/karar, çoklu materyal ve çoklu soru içerir.
- Her görevlendirme için tek bir çalışma alanı ve tek bir ana rapor vardır.
- Materyal, yanıt, bulgu veya rapor görevler arasında karışamaz.

## Genel menü

1. **Genel Bakış:** sadece özet ve yaklaşan işler; görev adımları içermez.
2. **Görevlerim:** ayrı görevlendirmelerin listesi ve yeni görevlendirme.
3. **Bilirkişi Profilim:** bir kez girilen meslekî profil.
4. **Ayarlar ve Kasa:** yerel güvenlik, yedek, güncelleme.

Bir görev açılınca sağ içerik alanında sadece o işe ait Görev Özeti, Görevlendirme, Materyaller, Ses ve Transkript, Sorular ve Bulgular, Tek Rapor sekmeleri görünür. Görev sekmeleri genel sol menüden ayrıdır.

## Otomasyon kuralı

Görevlendirme belgesini önce MİHENK okur. Merci, dosya referansı, tarih/süre, kapsam, sorular ve materyal talimatlarını çıkarır. Kullanıcı baştan form doldurmaz; yalnızca belirsiz, çelişkili veya okunamayan alanları doğrular. Sistem hiçbir alana uydurma değer yazmaz.

Ses dosyaları görev bazında kuyruğa girer; yerel ASR yalnız makine taslağı üretir. Uzman düzeltmesi, anotasyonu ve onayı ayrı izlenir. Her görev sorusu bir uzman yanıtına ve destekleyen materyal/zaman segmentine bağlanır.

## Tek rapor politikası

Her görevlendirme için bir ana bilirkişi raporu oluşturulur. Bu raporda görev ve merci bilgileri, bilirkişi profili, kapsam/sınırlar, sorular, materyal envanteri, yöntem/model/sürüm, doğrulanmış bulgular, soru bazlı gerekçeli yanıtlar, sınırlılıklar ve numaralı ekler bulunur. Kullanıcıya birbirinden kopuk birden çok rapor dosyası üretilmez.

Bilirkişilik Daire Başkanlığı sayfasında dört merci ailesine ait örnek raporlar listelenir. Mayıs 2025 Temel Eğitim Kaynak Kitabı ise raporların özel ve değişmez bir şablonu olmadığını, örneklerin ihtiyatla kullanılmasını belirtir. Bu nedenle MİHENK merciye göre ilgili örnek iskeleti önerir; onu zorunlu sabit forma dönüştürmez ve önceki rapordan kopyalama yapmaz.

## UYAP Editör sınırı

Tek rapor dosyasının gerçek Windows UYAP Editör'de açılması, Türkçe karakter/sayfa/tablo/ek kontrolü, UDF kaydetme ve yeniden açma testleri yapılmadan çıktı biçimi "UYAP'a hazır" diye sunulmaz. Portalın ilgili evrak türünde kabul ettiği biçim ayrıca doğrulanır. E-imza ve resmî gönderim bilirkişinin işlemidir.

## İlk sürüm kabul kapıları

1. Profil ilk açılışta bir kez oluşturulur ve rapora doğru aktarılır.
2. Görevlendirme belgesi okunur; kaynak izli alanlar çıkarılır; yalnız istisnalar kullanıcıya sorulur.
3. Birden çok görevlendirme birbirinden ayrı saklanır.
4. Tek görevlendirmede birden çok ses ve soru işlenir.
5. Kasa yeniden açıldığında görev ve ses bağlamı geri yüklenir.
6. Yerel ASR kuyruk ve transkript düzenleme akışı çalışır.
7. Her soru yanıtı görev içindeki dayanaklara bağlanır.
8. Görev başına tek rapor oluşturulur; doğru merci örnek iskeleti önerilir.
9. Tek rapor UYAP Editör'de aç/kaydet/yeniden aç kabul testini geçer.
10. Windows MSI temiz kurulum, kasa açma, normal kapatma, güncelleme, başarısız güncelleme ve kurtarma testlerini geçer.
11. 56.12 uzmanı sentetik/izinli görevde akışı tamamlar.

Derleme/birim test başarısı tek başına pilot kabulü değildir. Her kapı kanıtla GEÇTİ/KALDI/ENGELLENDİ olarak kaydedilir.
