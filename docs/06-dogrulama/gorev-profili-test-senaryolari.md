# Görev Profili — Sentetik Test Senaryoları

> **Durum:** Taslak test paketi — MİHENK uygulaması henüz geliştirilmedi  
> **Güncelleme:** 13 Kasım 2026  
> **Veri ilkesi:** Bu belgede gerçek dava, kişi, mahkeme, bilirkişi veya belge bulunmaz. Tüm kimlikler ve değerler sentetiktir.

## Amaç

Görevlendirme belgesinden çıkarılan bilgilerin her görev için ayrı tutulduğunu, belirsizliğin gizlenmediğini ve otomasyonun yanlış varsayım üretmediğini test etmek.

Bu senaryolar çalıştırılmış yazılım testleri değildir; gelecekte uygulamanın kabul/regresyon testleri için örnek davranış tanımlarıdır.

## Senaryo GP-01 — Açık alanlar, değişken materyal sayısı

**Girdi:** Sentetik bir görevlendirme yazısı; kapsam ve üç ayrı soru açıkça yazılı; teslim listesinde üç dijital ses dosyası var; rapor süresi ve başlangıcı açık; ilgili merci için resmî şablon seçilebilir.

**Beklenen davranış:**
- Üç soru ayrı görev sorusu kaydı oluşturur.
- Üç dosya materyal envanterine girer.
- Süre ve başlangıç olayı kaydedilir.
- Her soru için rapor yanıt alanı açılır.
- Sistem sekiz dosya veya başka örnek dosya sayısı varsaymaz.
- Kaynak belge/sayfa bağlantısı tüm çıkarılmış alanlarda bulunur.

## Senaryo GP-02 — Başka görevde başka süre ve teslim koşulu

**Girdi:** GP-01'den bağımsız sentetik ikinci görevlendirme; farklı süre, farklı başlangıç olayı, iki fiziki ek ve elektronik rapor teslimi açıkça belirtilmiş.

**Beklenen davranış:**
- GP-01'in süre, materyal, rapor veya soru bilgisi GP-02'ye taşınmaz.
- İki fiziki ek ayrı envanter girdisi olur.
- Teslim biçimi ikinci görevin açık talimatına göre kurulur.
- GP-01'deki üç ses dosyası GP-02'de görünmez.

## Senaryo GP-03 — Süre var, başlangıç olayı belirsiz

**Girdi:** Süre miktarı yazılı; fakat hangi tarihten veya olaydan başlayacağı belgeden güvenle çıkarılamıyor.

**Beklenen davranış:**
- Süre ifadesi kaynak metniyle kaydedilir.
- Son tarih tahmin edilmez.
- Yalnızca “süre başlangıcı” alanı istisnaya çıkarılır.
- Sistem diğer açık alanları otomatik işlemeye devam eder.

## Senaryo GP-04 — Göreve özel nüsha talimatı

**Girdi:** Sentetik bir görevde belirli sayıda fiziki suret talimatı açıkça yazılı; ikinci görevde suret adedi hakkında talimat yok.

**Beklenen davranış:**
- İlk görevde suret talimatı yalnızca o görev profiline yazılır.
- İkinci göreve suret sayısı kopyalanmaz.
- Talimat olmayan dosyada sistem genel bir sayı üretmez.
- Elektronik teslim ve fiziki suret birbirinden ayrı alanlarda tutulur.

## Senaryo GP-05 — Belgeler arasında çelişki

**Girdi:** Görevlendirme yazısında bir süre, ek tutanakta başka süre bulunuyor.

**Beklenen davranış:**
- İki ifade de kaynak ve konumlarıyla saklanır.
- Sistem sessizce birini seçmez veya birleştirmez.
- Sadece çelişkili süre alanı istisnaya çıkarılır.
- Diğer açık görev bilgileri işlenmeye devam eder.

## Senaryo GP-06 — Fiziki teslim ve UYAP erişimi ayrımı

**Girdi A:** Dizi pusulası ve imza karşılığı fiziki teslim bilgisi olan sentetik görev.  
**Girdi B:** UYAP üzerinden dosya inceleme yetkisi verildiği yazılı olan sentetik görev.

**Beklenen davranış:**
- A görevinde fizikî teslim ve iade akışı oluşur.
- B görevinde UYAP erişim durumu kaydedilir; fizikî teslim varsayılmaz.
- İki yol da aynı materyal envanteri kavramına bağlanır; teslim kanalı farklı kalır.

## Senaryo GP-07 — Heyet halinde görevlendirme

**Girdi:** Birden fazla bilirkişi görevlendirilmiş sentetik görev ve raporda imza gereksinimi belirtilmiş.

**Beklenen davranış:**
- Görev heyet bilgisi taşır.
- Rapor imza koşulu tek bilirkişilik görevinden farklı kurulur.
- Eksik imzalar teslim öncesi kontrol listesinde görünür.
- MİHENK imza üretmez veya başka bilirkişi adına işlem yapmaz.

## Senaryo GP-08 — Şablon belirsizliği

**Girdi:** Görev belgesinde merci bilgisi var ancak şablon sınıfını belirlemek için gerekli alan eksik veya çelişkili.

**Beklenen davranış:**
- Sistem olası resmî şablonları kaynaklarıyla önerir.
- Bir şablonu sessizce kesin seçmez.
- Sadece şablon seçimi istisnaya çıkarılır.
- Diğer bağımsız görev hazırlıkları devam eder.

## Senaryo GP-09 — Önceki görev verisinin rapora sızmaması

**Girdi:** Sentetik Görev A'da yalnızca test amacıyla üretilmiş benzersiz bir işaretleyici; ardından farklı içerikli Görev B.

**Beklenen davranış:**
- Görev B raporu sıfırdan oluşturulur.
- Görev A işaretleyicisi Görev B raporu, ekleri, metadata'sı ve çıktı paketinde bulunmaz.
- Aynı resmî şablonun kullanılması görev verilerinin paylaşılmasına neden olmaz.

## Senaryo GP-10 — Düşük belge okuma güveni

**Girdi:** Tarama kalitesi düşük bir sentetik tutanak; görev konusu okunuyor fakat süre hanesi okunamıyor.

**Beklenen davranış:**
- Okunabilen alanlar otomatik işlenir.
- Süre alanı düşük güvenli olarak işaretlenir ve kaynak sayfa gösterilir.
- Kullanıcıdan bütün belgeyi tekrar girmesi istenmez; yalnızca süre alanı netleştirilir.
- OCR/çıkarım güveni belgenin doğruluğu veya hukukî anlamın kesinliği gibi sunulmaz.

## Senaryo GP-11 — Birden fazla materyal türü

**Girdi:** Sentetik görevde bir PDF evrak, iki görüntü ve değişken sayıda dijital medya dosyası listelenmiş.

**Beklenen davranış:**
- Her materyal kendi türü ve kaynağıyla envantere girer.
- Dosya sayısı kullanıcı veya eski örnekten alınmaz; içe alınan gerçek sentetik fixture üzerinden hesaplanır.
- Beklenen, alınan, kopyalanan ve incelenen durumlar birbirinden ayrılır.

## Senaryo GP-12 — Rapor biçimi ve UDF akışı

**Girdi:** Sentetik görevde raporun elektronik olarak sunulması talimatı mevcut; belge biçiminin açıkça belirtilmediği durum.

**Beklenen davranış:**
- Sistem “UDF zorunlu” varsayımı üretmez.
- UYAP Doküman Editörü'nün güncel sürümü ve ilgili evrak türü için doğrulanmış biçim bilgisi kullanılır.
- Biçim doğrulanmamışsa uygun test/istisna açılır.
- İmzalanmış belge değişirse yeniden imza gerekliliği kullanıcıya bildirilir.

## Test paketi kabul ölçütü

- Göreve özgü değerler görevler arasında taşınmaz.
- Belirsiz/çelişkili alanlar gizlenmez.
- Kaynak belgeye geri iz sürülebilir.
- Açık alanlar için kullanıcıdan gereksiz onay istenmez.
- Materyal sayısı, türü ve teslim kanalı her görevde değişebilir.
- Rapor her görev için temiz üretilir.
- Otomatik sistem hiçbir durumda nihai teknik kanaat, e-imza veya resmî teslimi kendi yapmış gibi göstermez.
