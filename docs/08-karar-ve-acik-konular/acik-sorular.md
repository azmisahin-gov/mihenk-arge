# Açık Sorular

> **Durum:** Araştırma ve ürün keşfi  
> **Güncelleme:** 15 Kasım 2026

## Görevlendirme ve resmî süreç

1. Görevlendirme belgesinde alanların hangi biçimlerde yer aldığı (PDF metni, tarama, UDF veya karma ekler) hangi oranlarda görülüyor?
2. Görev başlangıç tarihi ve rapor süresinin hesabında hangi olay/tarih esas alınıyor; tutanaklarda belirsizlik olduğunda merci nasıl açıklama yapıyor?
3. Farklı merci/yargı türlerinde rapor şablonu ve zorunlu ekler hangi ölçüde değişiyor?
4. Rapor ve ekler için UYAP Portal'da kabul edilen biçimler, evrak türüne ve güncel sürüme göre nasıl değişiyor?
5. UDF dosyasının MİHENK'ten üretilmesi mi, yoksa başka biçimde üretilip güncel UYAP Editörü'nde açılarak UDF kaydedilmesi mi güvenilir ve destekli yol?
6. Fizikî dosya/dizi pusulası/ekler için iade ve saklama uygulaması dosya türüne göre nasıl farklılaşıyor?
7. Heyet görevlendirmesinde rapor, ekler ve imza akışı nasıl ilerliyor?
8. Üçüncü taraf yazılım entegrasyonu için yetkili UYAP API veya yazılı izin süreci var mı?

## Görev Profili doğrulaması

9. B-01 ile incelenen görevlendirme örneğinde Görev Profili'ne çıkaracağımız alanlar gerçek iş akışıyla uyumlu mu?
10. Bilirkişi hangi görevlendirme alanlarının sistemce çıkarılmasını, hangilerinin kendisine sorulmasını istiyor?
11. Belirsiz/çelişkili görevlendirme metninde hangi durumlarda merciye açıklama sorusu gönderiliyor?
12. Uzmanlık alanı ve görev kapsamı arasındaki uyumsuzluk nasıl ele alınıyor?

## Kullanıcı ve ürün

13. Farklı uzmanlık alanlarında ortak görev profili ve envanter ihtiyaçları aynı mı?
14. Bilirkişiler en çok hangi manuel kontrolü ve rapor işini tekrar ediyor?
15. İlk kurulum ve güncellemede hangi işletim sistemi/izin/kurum kısıtları var?

## Güvenlik ve teknik

16. Gerçek görev verisinin cihazda saklanma ve görev sonrası iade/silme yükümlülükleri nelerdir?
17. Belge çıkarımı/OCR ve model çalışması yerelde mi, haricî hizmette mi yapılmalı; bunun hukukî ve güvenlik koşulları nedir?
18. UDF/format uyumluluk testini yapabileceğimiz izinli ve sentetik bir test ortamı mevcut mu?
19. Şifreleme, yedek, geri yükleme ve kurtarma kabul ölçütleri nelerdir?

## Bağımsız doğrulama

20. İkinci bilirkişi veya farklı uzmanlık alanı ile ortak çekirdek gereksinimleri nasıl doğrulayacağız?
21. Hukuk, meslekî uygulama ve teknik güvenlik bulgularını kim/hangi kaynakla bağımsız doğrulayacak?


## Wireframe v0.3 tasarım gözden geçirmesi

> v0.3 kullanıcı tarafından kabul edilmedi. Aşağıdaki sorular yeni oturumda ekran/akış tasarımıyla birlikte yanıtlanmalıdır.

22. İlk açılışta yerel kasa oluşturma, bilirkişi profilini bir kez tanımlama ve uzmanlık alanlarını belirtme sırası kullanıcı için en anlaşılır sıra mı?
23. Bir yerel kasa/bir bilirkişi profili ilk sürüm için yeterli mi; aynı Windows hesabında farklı bilirkişilerin profilleri gerekecek mi?
24. Bilirkişi profilinde rapor için gerçekten gereken zorunlu alanlar hangileri? Ad-soyad, sicil numarası, unvan/sıfat, temel/alt uzmanlık, bölge kurulu ve iletişim alanlarının hangileri şablon/görev türüne bağlı?
25. Profil, uzmanlık alanı ve yazılım modülü arasındaki ilişki kullanıcıya nasıl anlatılmalı? Modül, görevlendirme belgesindeki uzmanlık ihtiyacına göre otomatik mi önerilmeli, kullanıcıya hangi noktada seçim sunulmalı?
26. Sol menü daraltma/genişletme, ikon etiketleri ve durumun hatırlanması nasıl davranmalı? Avatar menüsünde profil ve uzmanlık alanı; ayrı ekranda kasa/güvenlik ve uygulama ayarları mı olmalı?
27. Genel Bakış dashboard'unda hangi az sayıdaki özet gerçekten yararlı? Görevlerim listesinde hangi görev bilgileri görünmeli; hassas dosya bilgileri nasıl korunmalı?
28. İlk belge alımında hangi formatlar (metinli/taranmış PDF, UDF, RTF, DOCX ve ekler) ilk pilotta desteklenmeli? OCR/okuma başarısızlığında kullanıcıya nasıl istisna gösterilmeli?
29. Görevlendirme belgesinden çıkarılan alanlarda kaynak sayfa izi, güven/kalite işareti ve kullanıcı düzeltme geçmişi nasıl gösterilmeli?
30. Görev içi sekmelerde çoklu materyal ve çoklu soru en anlaşılır biçimde nasıl sunulmalı? Büyük dosya, eksik materyal ve ASR hata/yeniden dene durumları nasıl gösterilmeli?
31. Tek rapor önizlemesinde bölüm listesi, sayfa, kontrol özeti ve düzeltme alanı nasıl düzenlenmeli? Kullanıcı için raporun tek ana dosya olması hangi eklerin aynı rapora bağlanmasını, hangilerinin ayrı teslim eki kalmasını gerektiriyor?
32. Gerçek Windows UYAP Editör testine girecek ilk rapor dosya biçimi ve ilgili Bilirkişi Portalı evrak türü nedir?
33. İlk kez kullanan bilirkişinin sentetik görevi yardımsız tamamlaması için hangi yönlendirme/boş durum/geri dönüş ekranları gerekir?
