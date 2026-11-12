# Modül Sınırları

> **Durum:** Bütünleşik tek uygulama ve uzmanlık modülü ilkesiyle güncellendi  
> **Güncelleme:** 13 Kasım 2026

## MİHENK tek uygulama hedefi

MİHENK, farklı araçları başlatan bir menü veya bağlantı koleksiyonu değildir. Kullanıcı görevini, materyalini, uzmanlık aracını, bulgularını ve raporunu tek MİHENK arayüzünde yönetir.

Araçlar gerektiğinde MİHENK ile birlikte dağıtılan kütüphaneler, yerel motorlar veya izole işçi süreçleri olabilir. Kullanıcı bunları ayrı program olarak kurup yönetmez. Her modül MİHENK'in ortak görev, dosya güvenliği, iş akışı, denetim ve rapor altyapısını kullanır.

## Katmanlar

- **Ortak görev çekirdeği:** Görev Profili, sorular, süre, tarafsızlık/uzmanlık kontrol listesi, materyal teslim/iade ve rapor süreci.
- **Materyal yönetimi:** Orijinal/çalışma kopyası/türev, hash, metadata, yerel güvenli kasa ve işlem geçmişi.
- **Belge ve rapor motoru:** Ortak belge modeli, şablon katalogu, biçim adaptörleri, soru-bulgu eşlemesi ve kalite kontrol.
- **Uzmanlık modülleri:** Her alan için ayrı iş akışı, araçlar, veri alanları, yöntem ve kabul testleri.
- **Araç çalıştırma katmanı:** Yerleşik kütüphane, doğrulanmış paket veya izole worker süreçleri; kullanıcıya ayrı uygulama açtırmaz.
- **Güvenlik/denetim:** Modül izinleri, sandbox, imzalı paketler, ağ politikası, log, yedek ve geri alma.

## Uzmanlık modülleri

- Her modül yalnızca doğrulanmış uzmanlık akışı ve yetki sınırında çalışır.
- Modül kendi teknik alanlarını ortak çekirdeğe zorunlu kılmaz.
- Modül manifestinde sürüm, girdi/çıktı, izinler, bağımlılıklar, lisans/SBOM, kaynak imzası ve test paketi bulunur.
- Modül bağımsız güncellenebilir ancak uygulama çekirdeğiyle uyumluluğu doğrulanır.
- Modül arızası başka görev veya modülü etkilememelidir.

## 56.12 örnek modülü

56.12 için ses içe alma, metadata, transkripsiyon, ses-metni eşleme, tekrar dinleme ve düzeltme araçları aynı uygulamanın içinden yönetilir. Bu örnek, tüm MİHENK'in yalnızca ses işleme ürünü olacağı anlamına gelmez.

## Güvenlik ilkeleri

- Yalnızca incelenmiş ve imzalanmış modül paketleri.
- Göreve özgü dosya erişimi ve orijinal materyale salt okunur erişim.
- Ağ erişimi varsayılan olarak kapalı; dış servis izni ayrıca değerlendirilir.
- İşlemci/GPU/bellek/süre ve dosya sistemi erişim sınırları.
- Sürüm sabitleme, işlem izi, güvenli güncelleme ve rollback.
- Lisans/bağımlılık envanteri ve güvenlik açığı izleme.
- Gerçek vaka verisi public issue, test fixture, log veya telemetriye girmez.

## Resmî sistem bağlantısı

UYAP ve Adalet e-İmza, yetkili API/izin olmadan otomatikleştirilmez. Resmî imza ve gönderim son aşamada kullanıcı tarafından yürütülür veya ileride yalnızca belgelenmiş/yetkilendirilmiş bir entegrasyonla değerlendirilir.
