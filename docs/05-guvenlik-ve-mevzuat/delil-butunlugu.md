# Delil Bütünlüğü

> **Durum:** Teknik tasarım ilkeleri — uzman/hukukçu doğrulaması gerekli  
> **Güncelleme:** 13 Kasım 2026

## Kavram ayrımı

- Hash/kriptografik özet, dosyanın belirli bayt dizisini tanımlamaya ve alınan kopyanın daha sonra değişip değişmediğini karşılaştırmaya yarar.
- Dijital imza, imza sahibini ve imzalanan verinin bütünlüğünü doğrulamaya yardımcı olur; her türlü teslim zincirinin yerine geçmez.
- Denetim kaydı, uygulama içindeki olayları kaydeder; mahkeme/kurum tutanağı veya resmî teslim kaydı değildir.
- Şifreleme, saklanan/taşınan verinin gizliliğini korumaya yöneliktir; erişim yönetimi ve anahtar yönetimi olmadan yeterli değildir.

## Önerilen materyal kabul akışı

1. Materyalin hangi kaynaktan, hangi yöntemle ve kim tarafından teslim alındığını kaydet.
2. Fiziki teslim tutanağı/tesellüm kaydı mevcutsa numara ve tarihini, teslim eden/alan bilgisini yetkili yerel kayıtta ilişkilendir.
3. Fiziki taşıyıcı, zarf, etiket, USB ve diğer eklerin teslim anındaki durumunu kurum prosedürüne uygun biçimde kaydet.
4. Teslim edilen fiziki belge ve dijital materyaller için ayrı envanter oluştur; dosya adlarını, sayısını ve içeriği/ilişkisini kaydet.
5. Teslim anındaki kaynak dosya adını, boyutunu, türünü ve erişim durumunu listele.
6. Orijinal materyalin geldiği biçimi koru; uygun olduğunda yazma koruması kullan ve bunun durumunu kaydet.
7. İçe alma sırasında kaynak dosya ve çalışma kopyası için hash al; hash değerlerini karşılaştır.
8. Orijinal ile çalışma kopyasını ayrı tut; analiz işlemlerini yalnızca çalışma kopyasında yap.
9. Dönüştürme, normalleştirme veya yeniden kodlama yapıldıysa kaynak dosya, araç/sürüm ve parametreleri kaydet.
10. Türetilmiş her çıktı için kaynak dosya ve işlem ilişkisini sakla.
11. İşlem sonrasında orijinalin hash'ini yeniden doğrula.
12. Uyuşmazlıkta işlemi durdur, kullanıcıya görünür uyarı ver ve inceleme kaydı oluştur.
13. Fiziki materyal iadesini, iade edilen materyal listesi ve kullanıcının doğrulamasıyla kaydet.
14. Şifreli yedekleme ve geri yükleme testini planla.

## Hash ve özgünlük arasındaki sınır

İlk hash, ölçüm yapıldığı andaki dosya içeriğini tanımlar. Kaydın hash'ini teslim alımından sonra hesaplamak, dosyanın bu ölçümden sonra değişmediğini doğrulamaya yarayabilir; dosyanın teslimden önce hiç düzenlenmediğini, ilk kayıt olduğunu veya sesin gerçek olayla örtüştüğünü tek başına kanıtlamaz.

Dosya oluşturma/değiştirme zamanları ve metadata yararlı teknik gözlem olabilir; tek başlarına kesin özgünlük kanıtı değildir. Sesin özgünlüğü, montajı veya manipülasyonu iddia ediliyorsa ayrı görev kapsamı, uygun orijinal/erken nesil materyal ve bu inceleme için yetkin uzman gerekir. Transkripsiyon özelliği otomatik “orijinal”, “sahte” veya “montaj yok” sonucu üretmemelidir.

SWGDE Best Practices for Forensic Audio v2.5; materyalin teslim alınması, kaynağının belgelenmesi, orijinal/erken nesil kaydın tercih edilmesi, hash ve kopya bütünlüğünün kontrol edilmesi gibi teknik tavsiyeler içerir. SWGDE Digital Audio Authentication rehberi, özgünlük incelemesini ayrı bir teknik inceleme alanı olarak ele alır. Bunlar Türkiye mevzuatının veya resmî bilirkişi talimatının yerine geçmez; teknik başvuru kaynağıdır.

## Sınır

Bu teknik tasarım, materyalin hukuka uygun elde edildiğini, teslim zincirinin resmî olarak kurulduğunu veya mahkemece delil olarak kabulünü garanti etmez. Uygulama “delil zinciri sağlandı” veya “delil hukuken geçerlidir” iddiası kullanmamalıdır. Fiziksel teslim tutanağı ve resmî kayıt, uygulama içi kayıttan ayrıdır.

## Public repo yasağı

Orijinal materyal, çalışma kopyası, hash manifestinde kişiyi/dosyayı tanımlayabilecek veriler, rapor ve gerçek görev günlükleri GitHub'a yüklenmez. Hash bilgisi de dosya veya vaka hakkında bağlam vererek hassas hale gelebileceğinden public issue/commit içinde tutulmaz.

## Kaynaklar

- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [SWGDE Best Practices for Forensic Audio, v2.5 (09.06.2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE Best Practices for Digital Audio Authentication](https://www.swgde.org/documents/published-complete-listing/15-a-001-swgde-best-practices-for-digital-audio-authentication/)
- [ISO/IEC 27037:2012](https://www.iso.org/standard/44381.html)
