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
| ADR-018 | 13.11.2026 | Her görevlendirme belgesi ayrı bir Görev Profili üretir; çıkarılan alanların kaynak izi korunur | Yönetmelik m.51'deki göreve özgü kapsam, sorular, ücret ve süre; materyal tesliminin izlenebilirliği | Kabul edildi |
| ADR-019 | 13.11.2026 | Güvenli ve tekrarlı işlemler varsayılan olarak otomatik yürür; yalnızca belirsizlik, çelişki, risk veya mesleki karar gereken nokta kullanıcıya çıkar | Gereksiz onayların ve manuel iş yükünün azaltılması hedefi | Kabul edildi |
| ADR-020 | 13.11.2026 | Görev Profili ve belge çıkarımı ilk aşamada yalnızca sentetik test belgeleriyle doğrulanır | Public depolarda gerçek görev verisi bulunamaz; gerçek veriyle pilot için ayrı izin/hukuk/güvenlik kapıları gerekir | Kabul edildi |
| ADR-021 | 13.11.2026 | MİHENK tek uygulama deneyimi sunan bütünleşik uzmanlık platformu olacaktır | Kullanıcı uzmanlık araçları için ayrı programlar arasında dosya taşımak istemiyor; araçlar uzmanlık modülleriyle MİHENK içinde yönetilecek | Kabul edildi |
| ADR-022 | 13.11.2026 | Belge motoru ve uzmanlık araçlarında açık kaynak önceliklidir; lisans/güvenlik/biçim doğruluğu geçmeden bağımlılık eklenmez | Kullanıcı açık kaynak alternatiflerini önceliklendirdi; public GitHub deposu lisans incelemesi gerektirir | Kabul edildi |
| ADR-023 | 13.11.2026 | UDF ve e-imza son aşaması resmî UYAP/Adalet akışıyla uyumluluk testinden geçmelidir | UDF resmî format; topluluk kütüphaneleri reverse-engineered ve imza/portal kabulünü tek başına garanti etmez | Araştırma sürüyor |
| ADR-024 | 13.11.2026 | Uzmanlık modülleri imzalı, sürümlü, izinleri sınırlı ve geri alınabilir paketler olmalıdır | Modül kapsamı büyüdükçe tedarik zinciri ve veri erişimi riski artar | Taslak |
| ADR-025 | 13.11.2026 | UYAP Editörü ve Adalet e-İmza resmî son aşama araçlarıdır; MİHENK yükleyicisine dahil edilmez | Bakanlık resmî indirme/destek kanalı sunuyor; yeniden dağıtım lisansı ve kaynak kodu doğrulanmadı | Kabul edildi |
| ADR-026 | 13.11.2026 | MİHENK için Bakanlık onaylı ASR modeli doğrulanmadığından yerel açık kaynak modeller MİHENK test kabulünden geçmeden üretimde kullanılmaz | Kamuya açık resmî kaynaklarda 56.12 ASR onayı bulunamadı | Kabul edildi |
| ADR-027 | 13.11.2026 | 56.12 ASR en az iki aday modelle, aynı yerel test seti ve aynı referans metin üzerinden karşılaştırılır | Türkçe doğal konuşma başarımı, düşük ses, gürültü, örtüşme ve kaynak kullanımı modele göre değişebilir | Kabul edildi |
| ADR-028 | 13.11.2026 | ASR motorları yerel/çevrimdışı çalışır; birden fazla çıktının otomatik çoğunlukla birleştirilmesi yapılmaz | Gerçek vaka sesinin dışarı çıkmaması ve model uyuşmazlığının insan dinlemesine yönlendirilmesi | Kabul edildi |

Her karar yeni kanıt geldiğinde yeniden açılabilir. Bu kayıt ürün yönetişimidir; hukukî görüş değildir.
