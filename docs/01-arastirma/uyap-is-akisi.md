# UYAP ve Resmî İş Akışları

> **Durum:** Kullanıcı ekran gözlemi eklendi — yetkili süreç doğrulaması bekliyor  
> **Güncelleme:** 13 Kasım 2026

## Resmî portalın yeri

UYAP Bilirkişi Portalı resmî görevlendirme, dosya işlemleri ve rapor sunumu için kullanılan sistemdir. MİHENK portalın yerine geçmez; resmî kaydı veya resmî teslimi kendi içinde gerçekleşmiş gibi göstermemelidir.

UYAP'ın kamuya açık sayfası, portalı bilirkişilerin adliyeye gitmeden dosyalarıyla ilgili işlemlerini takip edebildiği hizmet olarak tanıtır. Erişim ve yetki koşulları portalın resmî açıklamasına tabidir.

## 12 Kasım 2026 tarihli kullanıcı ekran görüntülerinden gözlemler

Aşağıdaki maddeler tek bir kullanıcının redakte edilmiş ekran görüntülerinde görülen arayüz öğeleridir. Tüm kullanıcılar, yargı birimleri veya yetkiler için genel kural oldukları anlamına gelmez. Görüntüler bu public depoya eklenmemiştir.

- Ana sayfada bildirimler, aylık/yıllık dosya sayısı ve kota, tüm görevlendirmeler, rapor teslim eden/bekleyen sayaçları ve yaklaşan işler alanları görülüyor.
- Sol menüde bilirkişi bilgileri, iş listesi, işlemlerim, bölge kuruluna evrak gönderme, bilişimsel iletişim, dosya reddiyatları, önceki görevlendirmeler ve duyurular gibi bölümler görünüyor.
- İş listesinde tarih aralığı filtreleri, görev nedeni/türü, görevlendirme ve rapor teslim tarihi ile “Dosya Görüntüle” ve “Mahkemeye Evrak Gönder” eylemleri görünüyor.
- Dosya görüntüleme penceresinde “Dosya Bilgileri”, “Evrak” ve “Taraf Bilgileri” sekmeleri var.
- Evrak sekmesindeki uyarıda, Cumhuriyet savcılıkları ve ceza mahkemeleri görevlendirmelerinde evrakları görüntüleyebilmek için portal üzerinden “Bilirkişinin Dava Dosyasını İnceleme Talebi (Portal)” gönderilmesi ve ilgili birim amirinin yetki vermesi gerektiği yazıyor. Bu ekran gözlemidir; her dosyaya uygulanacak genel bir kural olduğu varsayılmamalıdır.
- “Mahkeme Evrak Gönder” penceresinde “Bilirkişi Raporu”, “Bilirkişi Genel Talep Dilekçesi” ve “Bilirkişi Ek Süre Talebi” türleri görünüyor. Ekranda evrakların 10 MB'tan küçük ve belirtilen biçimlere uygun olması uyarısı yer alıyor. Kesin dosya türü/limit, güncel portal kuralı olarak ayrıca doğrulanmalıdır.
- “Bölge Kuruluna Talep Gönderme” ekranında bilgi güncelleme, nakil, savunma, şikâyet ve genel talep dilekçesi seçenekleri görünüyor.
- “Dosya Tartışma” görünümünde görevlendirmedeki diğer bilirkişilere belge gönderme ve mesaj gönderme eylemleri bulunuyor.

## İlk kullanıcı testinden çıkarılan süreç hipotezi

1. Bilirkişi görevlendirmeyi ve gerekli dosya/evrak erişimini UYAP üzerinden görür.
2. Görev kabulü ve resmî portal adımları bilirkişi tarafından UYAP içinde yürütülür.
3. Materyal portal üzerinden veya fiziki ortamda (ör. USB) edinilebilir; teslim kaynağı ve yöntemi dosyadan dosyaya değişebilir.
4. Bilirkişi MİHENK'te manuel olarak yeni bir çalışma/dosya alanı açar ve gerekli görev bilgisini girer.
5. MİHENK'e aktarılacak kopyalar güvenli biçimde envantere alınır; orijinal materyal korunur.
6. Kontroller, inceleme araçları ve rapor hazırlık adımları MİHENK içinde yürütülür.
7. Uzman, otomatik hazırlanmış taslakları ve işaretlenen eksikleri gözden geçirir; nihai teknik değerlendirmeyi yapar.
8. Rapor ve ekler uygun biçimde dışa aktarılır; bilirkişi bunları UYAP'a kendisi yükler ve resmî teslimi portalda doğrular.

Bu sıra tek bir senaryo üzerinden oluşturulmuş çalışma hipotezidir; görev türüne ve yargı birimine göre farklılaşabilir.

## UYAP işlevleri ile MİHENK sınırı

| İşlem | Portalda görülen / resmî açıklamada bulunan | MİHENK için araştırılacak destek | Sınır |
|---|---|---|---|
| Bildirim ve görevlendirme | İş listesi ve bildirim alanları | Kullanıcının manuel görev kaydı ve süre hatırlatması | Yetkili entegrasyon yoksa otomatik veri çekme yok |
| Dosya/evrak erişimi | Dosya görüntüleme; erişim talebi uyarısı | Erişilebilen materyalin yerel envanteri | Portal erişim yetkisi MİHENK tarafından verilemez |
| Fiziki materyal | Tekil test anlatımında USB ile materyal edinimi | Teslim notu, dosya listesi, hash ve çalışma kopyası | Orijinal materyale yazma yapılmamalı |
| Rapor hazırlığı | Portal rapor gönderim eylemi | Şablon, taslak, ek ve kontrol listesi | Resmî şablon/biçim güncel kaynakla doğrulanmalı |
| Raporun sunulması | “Mahkemeye Evrak Gönder” eylemi | Dışa aktarma paketi ve kullanıcıya yükleme kontrol listesi | MİHENK gönderimi yapmış gibi durum gösteremez |
| Ek süre/genel talep | Ekran görüntüsünde talep türleri | Dilekçe taslağı ve süre takibi | Hukuki gerekçe ve gönderim insan onayında |
| Bölge kurulu talebi | Bilgi güncelleme, nakil, savunma, şikâyet, genel talep seçenekleri | Belge hazırlık kontrolü | Resmî işlem portalda |
| Diğer bilirkişi iletişimi | Dosya tartışma/mesaj ve evrak gönderme alanı | İzinli ekip notu/iş listesi hipotezi | Gizlilik ve erişim yetkisi ayrıca değerlendirilmeli |

## Entegrasyon kararı

Bu araştırmada herkese açık, üçüncü taraf kullanımını açıkça yetkilendiren UYAP API dokümantasyonu doğrulanamadı. Bu, kurum içinde veya yetkili taraflara açık API bulunmadığını kanıtlamaz. Yazılı izin, yetkili API dokümantasyonu ve teknik şartname sağlanana kadar otomatik oturum açma, ekran kazıma, veri çekme/gönderme, imza taklidi ve tarayıcı otomasyonu kapsam dışıdır.

## Resmî işlem sınırı

**UYAP = resmî kayıt ve resmî işlem. MİHENK = bilirkişinin çalışma alanı, materyal envanteri, inceleme hazırlığı, taslak ve kalite kontrolü.**

MİHENK “rapor UYAP'a sunuldu” dememelidir. Kullanıcı portalda teslimi tamamlayıp sonucu kendisi doğrulamadıkça durum “UYAP teslimi kullanıcı tarafından doğrulanmadı” olmalıdır.

## Kaynaklar

- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [Bilirkişilik Daire Başkanlığı — Bilirkişi Rapor Şablonları ve Kontrol Listesi](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/Bilirki%C5%9Fi%20Rapor%20%C5%9Eablonlar%C4%B1%E2%80%9D%20ve%20%E2%80%9CBilirki%C5%9Filer%20%C4%B0%C3%A7in%20Kontrol%20Listesi)
- [6754 sayılı Bilirkişilik Kanunu](https://mevzuat.adalet.gov.tr/mevzuat/104136)
