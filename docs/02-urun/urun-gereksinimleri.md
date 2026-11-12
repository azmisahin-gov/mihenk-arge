# Ürün Gereksinimleri

> **Durum:** Görev Profili, bütünleşik modül ve resmî araç sınırıyla güncellendi — MVP kararı değil  
> **Güncelleme:** 13 Kasım 2026

## Gereksinim kayıt formatı

Her gereksinim `REQ-*` kimliği, kaynak, tip, gerekçe, öncelik, doğrulama, bağımlılık ve güven seviyesi taşır. Bu listedeki maddeler ürün önerisidir; ayrıca mevzuat dayanağı açıkça belirtilmedikçe hukukî zorunluluk olarak okunmamalıdır.

## Gereksinimler

| ID | İhtiyaç | Kaynak türü | Öncelik | Kabul ölçütü | Durum |
|---|---|---|---|---|---|
| REQ-TASK-001 | Her görevlendirme için ayrı Görev Profili oluşturulmalı | Yönetmelik m.51 + ürün tasarımı | P0 | Görev kapsamı, sınırlar, sorular, ücret ve süre ayrı alanlarda | Taslak |
| REQ-TASK-002 | Görevlendirme belgesindeki açık alanlar otomatik çıkarılmalı | Ürün otomasyonu | P0 | Kaynak sayfa/metin ve çıkarım izi tutulur | Taslak |
| REQ-TASK-003 | Belirsiz/çelişkili alanlar yalnızca istisnaya çıkarılmalı | Güvenilirlik ilkesi | P0 | Sistem tahminî değeri kesinleştirmez; diğer alanlarda ilerler | Taslak |
| REQ-TASK-004 | Her görevde cevaplanacak sorular ayrı kaydedilmeli | Yönetmelik m.51 | P0 | Soru sırası/özgün ifade korunur ve rapor alanına bağlanır | Taslak |
| REQ-TASK-005 | Süre miktarı, başlangıç olayı ve son tarih ayrı yönetilmeli | Yönetmelik m.51–52 | P0 | Başlangıç belirsizse son tarih uydurulmaz | Taslak |
| REQ-TASK-006 | Materyal teslim yolu UYAP/fiziki/diğer olarak göreve göre belirlenmeli | Yönetmelik m.51/2 + saha gözlemi | P0 | Fiziki teslim ile UYAP erişimi farklı akışta izlenir | Taslak |
| REQ-TASK-007 | Suret, format, imza ve iade talimatları görev bazında tutulmalı | Görev belgesi + ürün tasarımı | P0 | Açık talimat başka görevlere varsayılan olmaz | Taslak |
| REQ-TASK-008 | Çıkarılan alanlar kaynak belge/sayfa ile ilişkilendirilmeli | İzlenebilirlik ilkesi | P0 | Her alanın kaynağına geri gidilebilir | Taslak |
| REQ-CORE-001 | Resmî işlem ve uygulama içi hazırlık görsel olarak ayrılmalı | Ürün güvenlik ilkesi | P0 | UYAP teslimi kullanıcı doğrulaması olmadan başarı sayılmaz | Taslak |
| REQ-CORE-002 | Orijinal materyal ile çalışma kopyası ayrı saklanmalı | Teknik iyi uygulama | P0 | Orijinal dosya değişmez; türev metadata tutar | Taslak |
| REQ-CORE-003 | Görev, materyal ve rapor eylemleri denetim kaydı oluşturmalı | Ürün önerisi | P1 | Olay, zaman, uygulama sürümü, önce/sonra kaydı | Taslak |
| REQ-SEC-001 | Yerel veri erişim kontrolü ve şifreleme planı olmalı | Teknik/hukuki | P0 | Tehdit modeli ve güvenlik testleri | Taslak |
| REQ-SEC-002 | Gerçek vaka verisi test ve telemetri için kullanılmamalı | Gizlilik ilkesi | P0 | CI sentetik fixture dışında vaka verisi içermiyor | Taslak |
| REQ-REPORT-001 | Rapor taslağı görev sorularını ve kaynakları eşleyebilmeli | Yönetmelik m.55 + ürün önerisi | P0 | Soru başına yanıt alanı ve kaynak/ek bağlantısı | Taslak |
| REQ-REPORT-002 | Nihai teknik kanaat otomatik üretilmemeli | Bilirkişilik görev sınırı | P0 | Sistem uzman adına teknik kanaat veya hukukî değerlendirme yazmaz | Taslak |
| REQ-REPORT-003 | Her görev için yeni, yalıtılmış rapor oluşturulmalı | Veri yalıtımı ilkesi | P0 | Önceki görevden içerik/ek/metadata sızıntısı testi geçer | Taslak |
| REQ-REPORT-004 | Uygun resmî şablon görev koşullarına göre seçilmeli | Resmî şablon kataloğu + ürün tasarımı | P0 | Şablon kaynağı/sürümü tutulur; belirsiz eşleşme istisnadır | Taslak |
| REQ-REPORT-005 | UDF ve diğer çıktı biçimleri gerçek UYAP akışında doğrulanmalı | UYAP Editör resmî yardımı | P1 | Her evrak türü/format kombinasyonu ayrı test edilir | Araştırma |
| REQ-PLATFORM-001 | Uzmanlık araçları tek MİHENK uygulamasında bütünleşik sunulmalı | Proje sahibinin açık ürün hedefi | P0 | Kullanıcı ayrı araç uygulaması açmadan görevini MİHENK'te yürütür | Kabul adayı |
| REQ-PLATFORM-002 | Yeni uzmanlık modülleri ortak çekirdeğe eklenebilir olmalı | Modüler ürün mimarisi | P0 | Modül sözleşmesi, sürüm, izin ve veri şeması tanımlıdır | Taslak |
| REQ-PLATFORM-003 | Uzmanlık araçları MİHENK tarafından paketlenmeli/yönetilmeli | Güvenlik ve kullanılabilirlik | P0 | İmza, lisans, SBOM, güncelleme ve geri alma kontrolü | Taslak |
| REQ-DOC-001 | Rapor belge modeli DOCX/ODT/PDF/UDF biçimlerinden bağımsız olmalı | Belge motoru araştırması | P0 | Tek içerik modeli farklı çıktı adaptörleriyle üretilebilir | Taslak |
| REQ-DOC-002 | Yerel ve çevrimdışı belge düzenleme desteklenmeli | Proje sahibi tercih/araştırma | P0 | Ağ kapalıyken rapor düzenleme ve çıktı alınabilmeli | Araştırma |
| REQ-DOC-003 | UDF içe alma/çıktı ve imza uyumluluğu resmî editörle test edilmeli | UYAP resmî yardım + teknik araştırma | P0 | Sentetik belgeler UYAP Editör'de açılır; biçim/tablolar/imza sınanır | Araştırma |
| REQ-ASR-001 | Türkçe ASR MİHENK içinde yerel motor olarak çalışmalı | Proje hedefi + açık kaynak araştırması | P0 | Ağ kapalı testte ses dışarı çıkmadan transkript taslağı üretilir | Taslak |
| REQ-ASR-002 | En az iki ASR adayı aynı test setiyle karşılaştırılmalı | Kalite/güvenilirlik | P0 | Model, runtime, checksum, WER/CER, RTF ve kaynak kaydedilir | Taslak |
| REQ-ASR-003 | ASR motoru ve model sürümü görev kaydına bağlanmalı | İzlenebilirlik | P0 | Her segmentin üretim motoru/model/parametre kaynağı görülebilir | Taslak |
| REQ-ASR-004 | Birden fazla modelin çıktısı otomatik olarak doğru kabul edilip birleştirilmemeli | Adli güvenilirlik | P0 | Uyuşmayan bölüm uzman dinlemesine çıkarılır | Taslak |
| REQ-OPS-001 | Yedekleme ve geri yükleme akışı test edilmeli | Güvenilirlik gereksinimi | P0 | Tam geri yükleme ve bütünlük doğrulama | Taslak |

## Öncelik anlamı

P0: Güvenlik, veri kaybı veya resmî görev sınırı açısından ilk kontrollü sürümde gerekli. P1: İlk kontrollü sürüm için önemli fakat kapsam kararı bekliyor. P2/P3: Sonraki kullanıcı kanıtıyla değerlendirilecek. Öncelikler geçicidir.

## Kaynaklar

- [Bilirkişilik Yönetmeliği — özellikle m.51–52](https://www.lexpera.com.tr/mevzuat/yonetmelikler/bilirkisilik-yonetmeligi-2)
- [UYAP Doküman Editörü — resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
- [Whisper ve TurkMedSTT ASR araştırması](../03-uzmanlik-modulleri/ilk-pilot/asr-motor-arastirmasi.md)
- [Pardus ve Adalet Bakanlığı resmî araç araştırması](../01-arastirma/bakanlik-pardus-uyap-resmi-yazilimlari.md)
