# Karar Kaydı

> **Güncelleme:** 13 Kasım 2026

| ID | Tarih | Karar | Gerekçe | Durum |
|---|---|---|---|---|
| ADR-001 | 12.11.2026 | MİHENK ilk aşamada araştırma ve keşif odaklıdır | Ürün ihtiyacı ve kapsam henüz yeterli saha kanıtıyla doğrulanmadı | Geçerli |
| ADR-002 | 12.11.2026 | UYAP otomatik entegrasyonu ilk kapsam dışı | Kamuya açık üçüncü taraf API/izin doğrulanmadı | Geçerli |
| ADR-003 | 13.11.2026 | 56.12 ilk örnek görev testidir; seçilmiş MVP/modül değildir | Tek kullanıcı ve tek test tüm alanı temsil etmez | Geçerli |
| ADR-004 | 12.11.2026 | Önceki örnek depolar birleştirilmeyecek | MİHENK ayrı ve sıfırdan bir projedir | Geçerli |
| ADR-005 | 12.11.2026 | Eski depolardan kod/altyapı/bağımlılık taşınmayacak | Proje sahibinin açık kararı | Kabul edildi |
| ADR-006 | 12.11.2026 | Teknoloji seçimi kullanıcı ve gereksinim keşfinden sonra yapılacak | Mevcut örneklerde kullanılan teknoloji varsayılmamalı | Geçerli |
| ADR-007 | 12.11.2026 | Dokümantasyon ve uygulama kodu ayrı GitHub depolarında tutulacak | Araştırma belgeleri ile uygulama yaşam döngüsü farklıdır | Kabul edildi |
| ADR-008 | 13.11.2026 | Araştırma deposu `mihenk-arge`, uygulama deposu `mihenk` adını kullanacak | Proje sahibinin yeniden adlandırma ve depo ayırma kararı | Kabul edildi |
| ADR-009 | 13.11.2026 | `mihenk` uygulama deposu şimdilik boş tutulacak | Ürün/MVP, mimari, görünürlük ve lisans karar kapıları henüz tamamlanmadı | Geçerli |
| ADR-010 | 13.11.2026 | Her iki public depoda gerçek vaka veya kişiyi tanımlayabilecek veri bulunmayacak | Gizlilik, veri koruma ve delil güvenliği | Kabul edildi |
| ADR-011 | 13.11.2026 | Nihai teknik kanaat, kanıt yorumu ve resmî teslim insan kontrolünde kalacak | Otomasyon doğruluğu garanti edemez; bilirkişi sorumluluğu korunmalı | Kabul edildi |
| ADR-012 | 13.11.2026 | 56.12'de transkript makine taslağıdır; güven puanı nihai doğruluk değildir | Hatalı transkriptin rapor kanaatine etkisini azaltmak | Kabul edildi |
| ADR-013 | 13.11.2026 | Her görevlendirme kendi kapsam, soru, süre, materyal, rapor şablonu ve teslim koşullarını taşır | Mevzuat m.51 görev kapsamı, sorular ve süreyi göreve özgü tanımlar; sekiz dosyalı örnek bütün görevlere genellenemez | Kabul edildi |
| ADR-014 | 13.11.2026 | Güvenli ve tekrarlı işlemlerde varsayılan otomasyon; insan müdahalesi istisna ve mesleki karar noktalarında | Kullanıcı gereksiz onaylardan kaçınmak, iş yükünü mümkün olduğunca azaltmak istiyor | Kabul edildi |
| ADR-015 | 13.11.2026 | Her rapor yeni görev kaydı ve onaylı şablondan temiz biçimde üretilir | Önceki raporu kopyalama yerine görev verisi yalıtımı ve çapraz-görev testleri | Kabul edildi |
| ADR-016 | 13.11.2026 | UDF, UYAP Doküman Editörü'nün yerel belge biçimi/iş akışı olarak ele alınır; doğrudan üretim ve kabul koşulu ayrıca test edilir | Resmî yardım UDF varsayılan kaydetme biçimini ve başka dışa aktarma biçimlerini açıklar; portalın genel biçim listesi evrak türüne özgü kabulü tek başına kanıtlamaz | Araştırma sürüyor |
| ADR-017 | 13.11.2026 | MİHENK kullanıcı dokümantasyonu, README, PR ve commit metinlerinin dili Türkçedir | Proje sahibi Türkçe çalışma standardını açıkça belirtti | Kabul edildi |

Her karar yeni kanıt geldiğinde yeniden açılabilir. Bu kayıt ürün yönetişimidir; hukukî görüş değildir.
