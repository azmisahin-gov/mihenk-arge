# UYAP ve Resmî İş Akışları

> **Durum:** KULLANICI DOĞRULAMASI BEKLİYOR  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Resmî portalda açıkça tanıtılan işlevler

UYAP Bilirkişi Portalının kamuya açık açıklamalarında bilirkişinin adliyeye gitmeden dosya işlemlerini takip edebilmesi, dosyaları elektronik ortamda incelemesi, rapor ve ek rapor göndermesi, ön rapor ve çoklu bilirkişi iletişim/iş birliği, görevlendirmeden çekilme ve ücret bilgilerini görüntüleme gibi işlevler açıklanmaktadır. Portalın gerçek menüleri, yetki seviyeleri ve sürüm farkları giriş yapılarak test edilmedi. Daire Başkanlığı ayrıca hukuk/idari-vergi, ceza mahkemesi, Cumhuriyet başsavcılığı ve icra müdürlükleri için ayrı rapor şablonları yayımlamıştır; bu şablonların güncel sürümü her görev türü için ayrı seçilmelidir.

| İşlem | Açık kaynakta durum | Yeni yazılımın rolü | Belirsizlik |
|---|---|---|---|
| Adaylık başvurusu | UYAP Bilirkişi Portal üzerinden; e-Devlet/e-imza veya mobil imza | Belge hazırlama kontrol listesi; resmî başvuru yerine geçmez | Güncel portal ekranları ve alan validasyonları |
| Sicil/liste | Daire Başkanlığı listeleri ve portal tanımı | Kullanıcıya kendi girdiği durumu hatırlatma | Sicil ve aktif portal erişim senkronu |
| Görevlendirme bildirimi | Portal genel kullanım açıklamalarında dosya takibi var | Kullanıcı manuel görev kaydı ekleyebilir | Bildirim kanalı, kabul/ret akışının tam ekranları |
| Dosyayı elektronik inceleme | Portal açık tanıtımında var | UYAP dışı not/çalışma planı | İndirme, görüntüleme, dosya boyutu ve rol tabanlı erişim |
| Fiziki materyal | CMK m.67 gibi düzenlemelerde mühürlü materyal ve tutanak hükümleri bulunur | Teslim/iade kontrol listesi | Portal işlevinden çok fiziki teslim uygulaması |
| Görevi kabul/ret/çekilme | Portalda çekilme işlevi açıkça tanıtılıyor | Taslak gerekçe/not; resmî işlem portalda | Kabul/ret ekranı, süre, gerekçe ve yetki kapsamı |
| Ek süre/ek bilgi | Açık tanıtım sayfasında doğrulanmadı | Kullanıcının talep taslağı ve süre takibi | Portal menüsü ve resmi talep şekli |
| Rapor/ek rapor | Portalda gönderim açıklanıyor | Rapor taslağı, biçim kontrolü, teslim kanıtı saklama | Dosya biçimi/elektronik imza/limitler |
| Kurul iletişimi / ön rapor | Portalda genel olarak duyuruluyor | Ortak çalışma notu, görev dağılımı ve revizyon | Gizlilik ve rol/yetkilendirme detayları |
| Ücret bilgisi | Portal açıklamasında görüntüleme işlevi var | Kişisel muhasebe/masraf kayıtları; resmî ödeme yerine geçmez | Detay ekranları ve gerçek tahsilat takvimi |
| Performans / istatistik | Portalın genel sayfalarında sınırlı açıklama | Ürün içi çalışma metrikleri | Resmî kota ve performans metriklerinin mevcut sürümü |

## Ücret/gider işlevinin ürün sınırı

2026 tarifesi ücret ve gideri ayırır; belge karşılığı mutat giderler, avans, ek ücret koşulları, görevlendirme tarihindeki tarife ve vergi kesintisi gibi hükümler içerir. UYAP içinde ücret bilgisi görüntüleme tanıtılmış olsa da MİHENK resmî ödeme başlatmamalı veya tahakkuk kararı vermemelidir. Kullanıcı yalnızca kendi masraf/ödeme takibini tutabilir.

## Entegrasyon kararı

Bu taramada herkese açık, üçüncü taraf kullanımına izin veren UYAP API dokümantasyonu bulunmamıştır. Bu, hiç API olmadığı anlamına gelmez; yalnızca kamusal doğrulama yoktur. Yazılı izin ve teknik şartname sağlanana kadar otomatik oturum açma, ekran kazıma, veri çekme/gönderme, imza taklidi ve tarayıcı otomasyonu kapsam dışıdır.

## Uygulama sınırı

**UYAP = resmî kayıt ve resmî işlem. MİHENK = bilirkişinin kendi çalışma notu, hazırlığı, materyal envanteri, kontrol listesi ve taslak dokümanı.** Uygulama hiçbir zaman “rapor UYAP'a sunuldu” dememeli; kullanıcı teslimi portalda tamamlayıp kanıtı manuel işaretlemedikçe durum “sunulduğu doğrulanmadı” olmalıdır.

## Kaynaklar

- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [6754 sayılı Bilirkişilik Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [5271 sayılı Ceza Muhakemesi Kanunu — resmî PDF](https://aile.gov.tr/uploads/chgm/uploads/pages/kanunlar/5271-sayili-ceza-muhakemesi-kanunu.pdf)
- [Bilirkişi Rapor Şablonları ve Kontrol Listesi duyurusu](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/Bilirki%C5%9Fi%20Rapor%20%C5%9Eablonlar%C4%B1%E2%80%9D%20ve%20%E2%80%9CBilirki%C5%9Filer%20%C4%B0%C3%A7in%20Kontrol%20Listesi)
- [2026 Yılı Bilirkişilik Asgari Ücret Tarifesi — 26.12.2025 Resmî Gazete](https://www.resmigazete.gov.tr/eskiler/2025/12/20251226-4.htm)
