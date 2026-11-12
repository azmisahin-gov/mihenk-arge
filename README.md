# MİHENK — Araştırma ve Ürün Keşfi

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Amaç

MİHENK, Türkiye'deki bilirkişilik faaliyetinin başvuru aşamasından görev kapanışına kadar gerçek yaşam döngüsünü araştırmak ve kanıtlanmış ihtiyaçlara göre doğru yazılım ürününü tanımlamak için açılmış ürün araştırma deposudur. Şimdilik ürün değil, araştırma ve karar alanıdır.

## İlk masa başı bulguları

1. Bilirkişilik Kanunu; bağımsızlık, tarafsızlık, objektiflik, uzmanlık sınırında kalma, hukuki nitelendirmeden kaçınma, görevi şahsen yapma ve sır saklama ilkelerini düzenler.
2. 2026 kabul esasları başvurunun e-Devlet üzerinden UYAP Bilirkişi Portal’a erişilerek elektronik veya mobil imza ile yapılmasını öngörür. Bir kişi yalnızca bir bölge kuruluna başvurur; en fazla üç temel alan altında altı alt uzmanlık alanı seçebilir.
3. 2026 uzmanlık listesinde 56.11 ve 56.12 ayrı alt uzmanlık alanlarıdır. 56.12, yargı mercilerinin ses ve görüntü bilişim sistemini kullanmasına ilişkin istisna içerir.
4. UYAP Bilirkişi Portalı dosyaya erişim, rapor/ek rapor gönderimi ve bazı görev yönetimi işlevlerini zaten sunar. Ürün bu resmî işlemlerin yerine geçmemelidir.
5. `azmisahin-gov/mihenk` deposu GitHub’da zaten vardır; ilk içerik commit’inden önce GitHub API’si depoyu boş olarak döndürmüştür.
6. İki mevcut Forensic Transcriber deposu 56.12 iş akışına odaklanır. Yeniden kullanım kararı AGPL-3.0-only ve üçüncü taraf lisans incelemesi tamamlanmadan verilmemelidir.

## İlk karar önerisi

**Şimdilik yeni bir genel bilirkişi platformu kodlamaya başlamayın.** Önce 8–12 gerçek uygulayıcıyla görev yaşam döngüsü görüşmeleri yapın; mevcut `forensic-transcriber-next` uygulamasını 56.12 için kontrollü, sentetik/izinli veriyle kullanılabilirlik ve hata-yolu pilotu olarak değerlendirin. Bu, 56.12’nin pazar ihtiyacını kanıtladığı anlamına gelmez; yalnızca bugün incelenebilen en somut teknik test nesnesidir.

## Repo durumu

- Depo: `azmisahin-gov/mihenk` (public, `main` dalı)
- Bu ilk commit, araştırma ve ürün keşfi belgelerini kaynak koddan ayrı olarak `main` dalına yerleştirir.
- Depo başlangıçta araştırma ve karar belgeleri için kullanılacaktır; ürün kodu eklenmesi ayrı bir karar kapısına bağlıdır.
- Gerçek bilirkişi dosyası, ses, kimlik veya gizli evrak depoya konmamalıdır.

## Belge haritası

- `docs/00-yonetim/`: amaç, sözlük ve çalışma kuralları
- `docs/01-arastirma/`: mevzuat, başvuru, UYAP, görev akışı, uzmanlık ve depo incelemesi
- `docs/02-urun/`: kullanıcı, gereksinim, otomasyon ve MVP
- `docs/03-uzmanlik-modulleri/`: pilot seçimi ve 56.12 pilotu
- `docs/04-mimari/`: mimari, veri modeli ve modül sınırları
- `docs/05-guvenlik-ve-mevzuat/`: hukuk, KVKK, tehdit, delil bütünlüğü ve yedekleme
- `docs/06-dogrulama/`: test, kullanıcı araştırması ve pilot planı
- `docs/07-yol-haritasi/`: aşamalar
- `docs/08-karar-ve-acik-konular/`: risk, açık sorular ve karar kaydı
- `templates/`: tekrar kullanılabilir araştırma ve ürün şablonları

## Kanıt ve durum sözlüğü

Her ifade mümkün olduğunda şu sınıflardan biriyle gösterilir: doğrulanmış bilgi, hukuki zorunluluk, resmî rehber/tavsiye, teknik iyi uygulama, ürün önerisi, doğrulanmamış varsayım veya araştırma gerektiren konu. Resmî kaynaklarda erişilemeyen veya giriş isteyen ekranlar doğrulanmış sayılmaz.

## Kapılar

Ürün ihtiyacı, kullanıcı görüşmeleri, UYAP sınırları, güvenlik/veri yaşam döngüsü ve ilk uzmanlık modülü doğrulanmadan üretim yazılımı geliştirmeye geçilmemelidir.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [Bilirkişilik Siciline Kabule İlişkin Usul ve Esaslar — 22.01.2026 PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122125906255Bilirkişilik%20Siciline%20Kabule%20İlişkin%20Usul%20Ve%20Esaslar.pdf)
- [Temel ve Alt Uzmanlık Alanları ve Aranan Nitelikler — 22.01.2026 PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
- [azmisahin-gov/mihenk GitHub deposu](https://github.com/azmisahin-gov/mihenk)
