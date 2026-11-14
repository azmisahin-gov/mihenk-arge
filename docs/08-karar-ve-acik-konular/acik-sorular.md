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


## Sistem tasarımı v1.0 ile yanıtlanan tasarım soruları

> v0.3 kabul edilmedi. Aşağıdaki 22–33 numaralı tasarım soruları [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](../02-urun/mihenk-sistem-ve-kullanici-akisi-v1.0.md) ile ürün tasarımı düzeyinde yanıtlandı. Bunlar yeni wireframe'de gösterilecek; gerçek kullanıcı/uzman ve teknik kabul testleriyle doğrulanacak.

22. **İlk açılış sırası:** Yerel kasa → bilirkişi profili → uzmanlık alanları → 56.12 modül hazırlığı → Genel Bakış. Sonraki açılışlarda yalnız kasa açılır.
23. **Yerel profil sayısı:** İlk ürün varsayımı bir yerel kasa/bir gerçek kişi bilirkişi profilidir. Çoklu profil bu sürümün kapsamı değildir; saha ihtiyacıyla yeniden değerlendirilir.
24. **Profil alanları:** Ad, soyad, sicil numarası ve meslekî unvan rapor kimliği için temel alanlardır. Uzmanlık alanları ayrı çoklu seçimdir. Bölge kurulu, iletişim ve diğer bilgiler isteğe bağlı veya göreve/şablona bağlıdır.
25. **Profil/alan/modül farkı:** Profildeki uzmanlık beyanı ile yazılım modülü ayrıdır. 56.12 ilk kullanılabilir modüldür; görev profiline göre modül önerilir. Kullanıcı motor seçimini her görevde yapmaz.
26. **Gezinme ve menüler:** Sol menü daraltılabilir/genişletilebilir. Avatar menüsü profil ve uzmanlık alanına gider. Kasa ve Güvenlik ile Uygulama Ayarları ayrı ana bölümlerdir.
27. **Dashboard/listeler:** Genel Bakış yalnız iş özetidir; Görevlerim tüm görevlerin ayrı listesidir. Hassas dosya içeriği listede varsayılan gösterilmez.
28. **Belge biçimleri:** Metinli ve taranmış PDF ilk kabul hedefidir. Diğer belge/resim türleri doğrulanmış destek matrisiyle eklenir. UDF orijinal kaynak olarak saklanabilir; doğrudan okuma doğrulanmadan tam destek iddia edilmez. Okunamayan sayfa istisnaya çıkarılır.
29. **Kaynak izi:** Her çıkarılan alan belge/sayfa/konum, çıkarım yöntemi, güven/kalite durumu ve kullanıcı düzeltme geçmişiyle gösterilir.
30. **Çoklu materyal/soru:** Materyaller envanter sayfasında; sorular ve bulgular ayrı görev içi alanda yönetilir. Ses/Transkript birden fazla kayıt ve her kayıt için ayrı kuyruk/segment sunar.
31. **Tek rapor:** Tek ana rapor, görev/merciye uygun bölüm yapısı, A4 sayfa önizlemesi, bölüm listesi ve kalite kontrol paneli kullanır. Yeniden oluşturma sürüm geçmişi üretir. Kullanıcı rapor biçimi seçmez.
32. **UYAP biçimi:** Belge/evrak türü bazında gerçek Windows UYAP Editör aç/kaydet/yeniden aç ve Portal kabul testi hâlâ açıktır. Sistem tasarımı bu teknik kabulü varsaymaz; uygun formatı doğrulanmış testten sonra otomatik seçer.
33. **İlk kullanım yardımı:** İlk kurulum yönlendirmesi, görev boş durumu, belge okuma istisnası, ASR hata/yeniden deneme, geri yükleme, rapor eksikleri ve çevrimdışı durumları ekran kataloğunda tanımlıdır.

## Gerçek pilot/teknik kanıt bekleyen açık noktalar

- Görevlendirme belgesi biçimlerinin gerçek kullanım dağılımı ve OCR doğruluğu.
- B-01 ve ek bilirkişilerle Görev Profili alanlarının ve istisna mesajlarının meslekî doğrulaması.
- Gerçek görevlerde süre başlangıç olayı, fiziki materyal iadesi ve saklama/silme uygulamaları.
- Heyet/tüzel kişi raporu için gelecekteki profil ve imza akışı.
- ASR adaylarının aynı insan referanslı izinli veri üzerinde karşılaştırılması; SEDA'nın en iyi model olduğu varsayılmaz.
- Gerçek cihazlarda model/runtime/donanım performansı ve checksum/lisans doğrulaması.
- UDF ve Portal evrak türü kabulü; güncel Windows UYAP Editör testi.
- Kasa/yedek/kurtarma, otomatik kilit ve güncelleme güvenlik kabulü.
- Bağımsız hukuk, meslekî uygulama ve veri güvenliği incelemesi.
