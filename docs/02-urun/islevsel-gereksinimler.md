# İşlevsel Gereksinimler

> **Durum:** Görev Profili ve bütünleşik uzmanlık modülleriyle güncellendi — geliştirme kararı değildir  
> **Güncelleme:** 13 Kasım 2026

## Ortak çekirdek işlevler

- Görevlendirme yazısı/tutanağı ve ilgili teslim belgelerini güvenli yerel çalışma alanına içe alma.
- Kaynak belgeyi koruma; metin çıkarımı/OCR sonucu ve kaynak sayfa/metin bağlantısını saklama.
- Belgeden görev kapsamı, sınırlar, cevaplanacak sorular, ücret, rapor süresi ve teslim koşullarını aday alanlara çıkarma.
- Her görevlendirme için ayrı Görev Profili açma.
- Açık ve güvenilir alanlarda otomatik ilerleme; belirsiz veya çelişkili alanları istisna listesine alma.
- Her soruyu ayrı görev nesnesi olarak kaydetme; rapor yanıt alanıyla ilişkilendirme.
- Süre miktarı, başlangıç olayı, tarih, son tarih ve ek süreyi ayrı izleme.
- Fiziki teslim, UYAP dosya erişimi ve diğer izinli materyal edinim biçimlerini ayırma.
- Dizi pusulası, fiziki ekler, dijital medya ve materyal iadesi için envanter.
- Beklenen/alınan/aktarılmış/incelenmiş/iade edilmiş materyal durumlarını izleme.
- Orijinal/çalışma kopyası/türetilmiş çıktı ayrımı.
- Göreve göre oluşturulan kontrol listesi ve rapor iskeleti.
- Her görev için sıfırdan ve yalıtılmış rapor oluşturma.
- Teslim öncesi biçim/tamlık kontrolü ve resmî teslimin kullanıcı tarafından kaydedilmesi.
- Yerel yedekleme/geri yükleme ve veri yaşam döngüsü.

## Bütünleşik uzmanlık araçları

- Bilirkişi, ilgili uzmanlık işlemlerini aynı MİHENK uygulama arayüzünden başlatır, izler ve sonuçlarını rapora bağlar.
- Kullanıcıdan her uzmanlık aracı için ayrı masaüstü uygulaması kurması, komut satırında çalıştırması veya üçüncü taraf sitede dosya yüklemesi istenmez.
- Araçlar MİHENK tarafından doğrulanmış yerleşik kütüphane, paketlenmiş yerel motor veya izole worker olarak dağıtılabilir. Arka planda ayrı süreç kullanılması, kullanıcı deneyiminin ayrı uygulamaya bölünmesi anlamına gelmez.
- Ortak çekirdek dosya içe alma, iş kuyruğu, görev verisi erişimi, denetim kaydı, rapor motoru ve kalite kapısı sağlar.
- Her uzmanlık modülü kendine özgü araç, yöntem, veri alanı, çıktı ve kalite testlerine sahiptir.
- Modül kataloğu yalnızca imzalı, lisansı ve güvenliği incelenmiş paketleri sunar; rastgele üçüncü taraf eklentiler varsayılan olarak yüklenemez.
- Modül güncellemeleri imza/hash, uyumluluk kontrolü, sürüm kaydı ve geri alma ile yönetilir.

## Görev Profili çıkarım davranışı

- Belge metni varsa doğrudan metin çıkarımı; taranmışsa OCR gibi yöntemler seçenek olarak değerlendirilir.
- Her alanın kaynak belge ve metin konumu saklanır.
- Alanın açıkça yazılı olması ile modelin yorumlayarak çıkarması ayrı işaretlenir.
- Düşük güvenli/çelişkili alanlar istisnadır; diğer işlemler mümkün olduğu ölçüde devam eder.
- Kullanıcıya tüm görev profilini yeniden doldurtmak yerine yalnızca çözülemeyen alan sorulur.
- Otomatik çıkarım, bilirkişinin görevi kabul/ret, yetkinlik, çekinme veya teknik kanaat kararını vermez.

## Belge ve rapor işleme

- Rapor içeriği UDF/DOCX/ODT/PDF'den bağımsız bir belge modelinde tutulur.
- MİHENK içindeki belge düzenleme arayüzü, incelenen ve seçilen açık kaynak belge motoruyla tek uygulamanın parçası olarak sunulur.
- Türkçe karakter, tablolar, üstbilgi/altbilgi, sayfa numarası, dipnot, ek, görsel ve şablon biçimi korunması için format regresyon testleri yapılır.
- UDF adaptörü resmî UYAP Editörü ile karşılaştırmalı doğrulanmadan üretim çıktısı olarak kabul edilmez.
- İmzalı belgenin içeriği değişirse imza geçerliliği kaybolabileceğinden imza, içerik ve kalite kontrollerinin sonrasında ele alınır.

## UYAP ve resmî imza sınırı

- MİHENK görev, rapor ve ek hazırlığını otomatikleştirebilir.
- UYAP hesabına giriş, resmî kabul ve rapor gönderimi için yetkili entegrasyon doğrulanmadan otomatik işlem yapılmaz.
- E-imza/m-imza özel anahtarı veya PIN'i MİHENK tarafından saklanmaz.
- Resmî imza son aşamada, yetkili UYAP/Adalet e-İmza akışında uygulanır. Belgelenmiş ve yetkilendirilmiş entegrasyon olursa ayrıca değerlendirilir.

## Bilinçli olarak yapılmayacaklar

- Kullanıcıya uzmanlık araçları arasında elle dosya taşıtmak veya komut satırı yönetmek.
- Lisansı/güvenliği doğrulanmamış eklenti veya çalıştırılabilir paket yüklemek.
- UYAP'ta izinsiz otomatik giriş ve form gönderme.
- Resmî rapor imzası veya elektronik imza üretme/taklit etme.
- Otomatik bilirkişi görevlendirme, görev kabul/ret veya çekinme kararı.
- AI tarafından nihai teknik kanaat veya hukukî değerlendirme yazılması.
- Konuşmacı etiketi üzerinden kişi kimliği, suçluluk, yaş veya cinsiyet çıkarımı.
- Önceki davanın raporunu kopyalayarak yeni rapor oluşturma.

## Kaynaklar

- [Bilirkişilik Yönetmeliği — m.51–52](https://www.lexpera.com.tr/mevzuat/yonetmelikler/bilirkisilik-yonetmeligi-2)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [UYAP Doküman Editörü — resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
