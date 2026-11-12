# Test Stratejisi

> **Durum:** Görev Profili, modül mimarisi ve belge biçim testleriyle güncellendi  
> **Güncelleme:** 13 Kasım 2026

## Test katmanları

1. **Mevzuat/resmî şablon:** Görev kapsamı, süre, rapor alanları ve şablonlar kaynak madde/sürümle doğrulanır.
2. **Görev belgesi okuma:** Farklı tutanaklardan kapsam, sorular, süre, teslim materyali, nüsha ve format alanları çıkarılır; düşük güven/çelişki istisnaya yükseltilir.
3. **Birim testleri:** Görev durumu, tarih hesabı, materyal sayımı, metadata, hash, kopya ilişkisi, soru/cevap ve rapor üretimi.
4. **Bütünleşik modül:** Modül manifesti, girdi/çıktı sözleşmesi, izin, sürüm ve ortak çekirdek uyumluluğu.
5. **Güvenlik:** Path traversal, kötü amaçlı medya, ZIP/XML bombası, decoder sınırı, shell injection, yedek sızıntısı, ağ erişimi ve imzalı güncelleme.
6. **Kurtarma:** Çökme, elektrik kesintisi, veri tabanı bozulması, kısmi çıktı, devam, yedek/geri yükleme ve rollback.
7. **Kullanılabilirlik/insan faktörü:** İlk kurulum, görev açma, uzmanlık araçlarının aynı arayüzde kullanımı, inceleme ve rapor süresi.
8. **Belge/format:** DOCX/ODT/PDF/UDF içe/dışa aktarma, Türkçe karakter, tablo, görsel, dipnot, sayfa düzeni, yazı tipi ve imza durumu.
9. **UYAP uyumu:** UDF çıktılarının güncel resmî Doküman Editörü'nde açılması, yeniden kaydedilmesi ve portalda ilgili evrak türü için test edilmesi.
10. **Uzman kabulü:** Sentetik/açık lisanslı test verisi ile gerçek bilirkişi iş akışı doğrulaması.

## Belge motoru kabul testleri

- Aynı rapor modeli DOCX, ODT, PDF ve UDF adaptörlerine aktarılabiliyor mu?
- Türkçe karakterler (I/İ/ı/ğ/ş/ü/ö/ç) ve seçilen fontlar korunuyor mu?
- Başlıklar, tablolar, birleştirilmiş hücreler, liste girintileri, üstbilgi/altbilgi, sayfa numarası, dipnot, resim ve ekler doğru mu?
- Belge UYAP Doküman Editörü'nde açıldığında sayfa sayısı ve yerleşim beklenen sonuçla karşılaşıyor mu?
- İmzalı UDF/PDF içeriği değiştirilmeden korunuyor mu; değişiklik yapılırsa imza uyarısı ve yeniden imza adımı gösteriliyor mu?
- Bozuk, aşırı büyük veya kötü amaçlı ZIP/XML/PDF girdileri güvenli biçimde reddediliyor mu?
- UDF → DOCX/PDF ve DOCX/ODT → UDF dönüşümlerinde içerik/biçim kaybı test ediliyor mu?
- Her test sentetik belge ve sabitlenmiş checksum ile tekrar üretilebiliyor mu?

## Modül güvenlik ve dağıtım testleri

- İmzasız veya bütünlüğü bozuk modül yüklenmiyor mu?
- Modül manifesti izin vermiyorsa internet, kamera, mikrofon, GPU veya diğer görev dosyalarına erişemiyor mu?
- Bir modül çökünce görev durumu ve orijinal materyal etkilenmiyor mu?
- İşlem kaydı modül/araç/model sürümünü ve parametreleri tutuyor mu?
- Güncelleme yarıda kesilirse son çalışan sürüme dönülebiliyor mu?
- Ağ kapalıyken yerel modüller işleyebiliyor mu?
- Lisans envanteri ve SBOM sürüme göre saklanıyor mu?

## Görevler arası veri yalıtımı

Her rapor yeni görev kaydı ve sürümlü şablondan üretilir. Test A'nın sentetik benzersiz işaretleyicileri Test B raporu, ekleri, metadata'sı ve çıktı paketinde bulunmamalıdır.

## Test verisi ilkeleri

- Önce sentetik Türkçe belge/ses ve kullanım koşulları doğrulanmış açık lisanslı veriler kullanılır.
- Gerçek dava kaydı, UYAP ekran görüntüsü, taraf bilgisi veya kişisel veri public CI, fixture veya log'a giremez.
- Açık kaynak proje deposundaki gerçek dosya örnekleri izin ve gizlilik incelemesi olmadan kopyalanmaz.
