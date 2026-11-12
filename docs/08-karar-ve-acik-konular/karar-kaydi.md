# Karar Kaydı

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

| ID | Tarih | Karar | Gerekçe | Alternatif | Durum |
|---|---|---|---|---|---|
| ADR-001 | 12.11.2026 | MİHENK ilk aşamada araştırma deposu olarak kalacak | Ürün ihtiyacı ve kapsam henüz kullanıcı araştırmasıyla kanıtlanmadı | Hemen uygulama kodlamak | Geçici |
| ADR-002 | 12.11.2026 | UYAP otomatik entegrasyonu ilk kapsam dışı | Kamuya açık üçüncü taraf API/izin belgesi bulunmadı | Ekran otomasyonu | Kabul edildi |
| ADR-003 | 12.11.2026 | 56.12 kontrollü pilot adayı | Resmî alan ayrımı net ve mevcut teknik örnek var; ihtiyaç kanıtı yok | Başka uzmanlık seçimi | Koşullu |
| ADR-004 | 12.11.2026 | Mevcut depolar birleştirilmeyecek | Farklı mimari, veri ve lisans/bağımlılık riskleri | Tek repo/monorepo | Geçici |
| ADR-005 | 12.11.2026 | Kod taşıma lisans incelemesi olmadan yapılmayacak | Her iki repo AGPL-3.0-only; üçüncü taraf lisansları farklı | Kodun doğrudan kopyalanması | Kabul edildi |
| ADR-006 | 12.11.2026 | İlk mimari alternatifi local-first, modular monolith olarak incelenecek | Gizlilik ve offline ihtiyacı hipotezi; saha doğrulaması bekleniyor | Bulut/çok kiracılı | Koşullu |

Her karar yeni kanıt geldiğinde yeniden açılabilir. Bu kayıt hukukî değerlendirme değil, proje yönetişim kaydıdır.
