# Test Stratejisi

> **Durum:** Görev bazlı kurallar, rapor üretimi ve UYAP biçim uyumu eklendi  
> **Güncelleme:** 13 Kasım 2026

## Test katmanları

1. **Mevzuat/resmî şablon:** Görev kapsamı, süre, rapor alanları ve şablonlar kaynak madde/sürümle doğrulanır.
2. **Görev belgesi okuma:** Farklı tutanaklardan kapsam, sorular, süre, teslim materyali, nüsha ve format alanları çıkarılır; düşük güven/çelişki doğru biçimde istisnaya yükseltilir.
3. **Birim testleri:** Görev durumu, tarih hesabı, materyal sayımı, metadata, hash, kopya ilişkisi, soru/cevap alanları ve rapor üretimi.
4. **Entegrasyon:** Çoklu dosya içe alma, transkripsiyon kuyruğu, ses-metni eşleştirme, rapor ve ek dışa aktarma.
5. **Güvenlik:** Path traversal, kötü amaçlı medya, decoder sınırı, shell injection, yedek sızıntısı, ağ trafiği ve imzalı güncelleme.
6. **Kurtarma:** Çökme, elektrik kesintisi, veri tabanı bozulması, kısmi çıktı, tekrar başlatma ve yedek/geri yükleme.
7. **Kullanılabilirlik/insan faktörü:** İlk kurulum, görev açma, dinleme, tekrar, düzeltme, rapor hazırlığı ve son kontrol süresi.
8. **UYAP belge uyumu:** UDF, PDF ve diğer portalın kabul ettiği biçimlerin ilgili evrak türünde açılma, görüntülenme, imza ve gönderim davranışı.
9. **Uzman kabulü:** Sentetik/açık lisanslı test verisi ile bilirkişi iş akışı doğrulaması.

## Göreve özgü kural testleri

- 30 günlük süre verilen bir test tutanağı doğru görev için 30 gün olarak kaydediliyor mu?
- Başka tutanakta farklı süre varsa önceki görevden 30 gün taşınıyor mu? Taşınmamalı.
- Süre başlangıç olayı belirtilmiyorsa yazılım varsayım yapmadan uyarı veriyor mu?
- Tutanakta taraf sayısı + 1 suret yazıyorsa bu koşul yalnızca ilgili göreve mi uygulanıyor?
- Tutanakta nüsha sayısı yoksa yazılım evrensel adet uyduruyor mu? Uydurmamalı.
- Bir görevde sekiz ses dosyası, başka bir görevde farklı sayıda veya farklı materyal varsa envanter gerçek içeriğe göre kuruluyor mu?
- Görevlendirme soruları değiştiğinde rapor bölümleri ve kalite listesi de göreve göre değişiyor mu?
- Eksik/çelişkili kapsam veya şablon alanında sistem doğru adımı istisna listesine alıyor mu?

## Raporun görevler arasında yalıtımı

Her rapor yeni bir görev verisi ve sürümlü şablondan üretilir. Önceki raporun kopyalanması temel yaklaşım değildir.

Otomatik testlerde:
- Test A raporuna yalnızca A görev bilgileri,
- Test B raporuna yalnızca B görev bilgileri eklenir.
- A görevine özel sentetik “işaretleyici” ad, tarih ve dosya kodları B raporunda aratılır.
- Eski görevden alan, ek, görsel, açıklama, metadata veya gizli belge parçası taşınmadığı doğrulanır.
- Aynı rapor şablonu tekrar kullanılsa bile oluşturulan belge içeriği ve görev verisi yalıtılmış olmalıdır.

## 56.12 özel otomatik testleri

- Sekiz ses dosyası içeren örnek görevde içe alınan/işlenen/rapora bağlanan dosya sayıları eşleşiyor mu? Sekiz yalnızca bu senaryonun fixture değeridir; genel sınır değildir.
- Aynı adlı farklı klasör dosyaları üzerine yazılıyor mu?
- Eksik/bozuk/codec desteklenmeyen dosya uyarılıyor mu?
- Orijinal hash işlem boyunca değişmeden kalıyor mu?
- Transkript, zaman damgası ve kaynak ses dosyasına geri bağlanıyor mu?
- Belirsiz/fısıltılı/örtüşen bölüm tahminle gizlenmek yerine işaretleniyor mu?
- Konuşmacı etiketleri nötr mü, gerçek kişi kimliği iddiası üretmiyor mu?
- Alıntılar kaynak dosya ve zaman aralığıyla eşleşiyor mu?

## UDF ve imza uyumluluk testleri

- UYAP Doküman Editörü'nün güncel sürümü test ortamında belirlenir.
- MİHENK'in ürettiği temiz rapor, doğrulanmış içe alma/dönüştürme yoluyla UYAP Editörü'nde açılabilir mi?
- Editörde UDF olarak kaydedilen dosya yeniden açıldığında metin, tablo ve ek referansları korunuyor mu?
- UDF, PDF ve DOCX için portalın ilgili evrak türünde kabul davranışı ayrı test edilir; portalın genel kabul ettiği format listesi her evrak türüne genellenmez.
- E-imza/m-imza doğrulaması yalnızca test sertifikası/izinli ortam ile sınanır; özel anahtar ve PIN hiçbir zaman otomasyon test verisine konmaz.
- Heyet halinde görevlendirmede gereken imza koşulları test edilir.
- MİHENK, imza uygulanmış belgeyi değiştirerek imzayı geçersizleştirmez.

## Test verisi ilkeleri

- Önce sentetik Türkçe diyalog ve kullanım koşulları doğrulanmış açık lisanslı veriler kullan.
- Sekiz dosyalı örnek görev, çoklu materyal testi olarak korunur; ayrıca 1, 2, farklı çoklu ve sıfır/eksik dosya senaryoları test edilir.
- Her örnek için kaynak, sürüm, lisans, checksum ve kullanım amacı kaydedilir.
- Gerçek dava kaydı, UYAP ekran görüntüsü veya kişisel veri public CI, fixture veya log'a giremez.

## Kabul kapısı

- 0 açık kritik güvenlik bulgusu.
- Yedek/geri yükleme testi geçer.
- Orijinal materyal değişmezliği ve kopya izlenebilirliği doğrulanır.
- Tüm içe alınan materyaller envanterde görünür.
- Göreve özgü süre, kapsam, soru, nüsha ve format bilgisi başka görevlere sızmaz.
- Her rapor yalnızca kendi görev verisiyle üretilir.
- Resmî teslimi yanlış gösteren otomatik durum yoktur.
- E-imza/m-imza ve resmî gönderim kullanıcı kontrolündedir.
- Uzman görüşü ile AI/ASR taslağı ayrıdır.

## Kaynaklar

- [Bilirkişilik Yönetmeliği](https://rayp.adalet.gov.tr/resimler/494/dosya/bilirkisilik-yonetmeligi16-06-20254-49-pm.pdf)
- [6100 sayılı HMK](https://mevzuat.adalet.gov.tr/mevzuat/103103)
- [5271 sayılı CMK](https://mevzuat.adalet.gov.tr/mevzuat/102946)
- [UYAP Doküman Editörü — Resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
- [UYAP Bilirkişi Portal Kullanım Rehberi](https://rayp.adalet.gov.tr/resimler/489/dosya/portal-kullanimi21-09-202210-21-am.pdf)
- [NISTIR 8387](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
