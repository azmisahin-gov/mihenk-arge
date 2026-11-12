# İşlevsel Gereksinimler

> **Durum:** Görev Profili yaklaşımıyla güncellendi — geliştirme kararı değildir  
> **Güncelleme:** 13 Kasım 2026

## Ortak çekirdek işlevler

- Görevlendirme yazısı/tutanağı ve ilgili teslim belgelerini kullanıcı tarafından güvenli yerel çalışma alanına içe alma.
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

## Görev Profili çıkarım davranışı

- Belge metni varsa doğrudan metin çıkarımı; taranmışsa OCR gibi yöntemler seçenek olarak değerlendirilir.
- Her alanın kaynak belge ve metin konumu saklanır.
- Alanın açıkça yazılı olması ile modelin yorumlayarak çıkarması ayrı işaretlenir.
- Düşük güvenli/çelişkili alanlar istisnadır; diğer işlemler mümkün olduğu ölçüde devam eder.
- Kullanıcıya tüm görev profilini yeniden doldurtmak yerine yalnızca çözülemeyen alan sorulur.
- Otomatik çıkarım, bilirkişinin görevi kabul/ret, yetkinlik, çekinme veya teknik kanaat kararını vermez.

## Uzmanlık modülü işlevleri

Modül işlevleri ilgili uzmanlık akışı ve mesleki sınır doğrulandıktan sonra eklenir. 56.12 için çoklu ses içe alma, metadata, otomatik transkripsiyon taslağı, ses/metin eşleme ve insan düzeltmesi araştırılabilir. Bu, tüm MİHENK görevlerinin aynı dosya türü veya işlem adımlarını kullanacağı anlamına gelmez.

## UYAP ve belge çıktısı sınırı

- MİHENK görev, rapor ve ek hazırlığını otomatikleştirebilir.
- UYAP hesabına giriş, resmî kabul, e-imza/m-imza ve rapor gönderimi için yetkili entegrasyon doğrulanmadan otomatik işlem yapılmaz.
- UDF, UYAP Doküman Editörü'nün varsayılan belge biçimidir; MİHENK'in doğrudan UDF üretmesi henüz teknik karar değildir.
- UYAP Editörü ve ilgili portal evrak türü ile biçim/imza uyumluluğu gerçek test ortamında doğrulanmalıdır.
- E-imza özel anahtarı/PIN'i MİHENK tarafından saklanmaz veya kullanılmaz.

## Bilinçli olarak yapılmayacaklar

- UYAP'ta izinsiz otomatik giriş ve form gönderme.
- Resmî rapor imzası veya elektronik imza üretme/taklit etme.
- Otomatik bilirkişi görevlendirme, görev kabul/ret veya çekinme kararı.
- AI tarafından nihai teknik kanaat veya hukukî değerlendirme yazılması.
- Konuşmacı etiketi üzerinden kişi kimliği, suçluluk, yaş veya cinsiyet çıkarımı.
- Ses transkripsiyonunu ses özgünlüğü/manipülasyon incelemesiyle aynı kabul etme.
- Önceki davanın raporunu kopyalayarak yeni rapor oluşturma.

## Kaynaklar

- [Bilirkişilik Yönetmeliği — m.51–52](https://www.lexpera.com.tr/mevzuat/yonetmelikler/bilirkisilik-yonetmeligi-2)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [UYAP Doküman Editörü — resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
