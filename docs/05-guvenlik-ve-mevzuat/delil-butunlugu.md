# Delil Bütünlüğü

> **Durum:** Teknik tasarım ilkeleri — uzman/hukukçu doğrulaması gerekli  
> **Güncelleme:** 13 Kasım 2026

## Kavram ayrımı

- Hash/kriptografik özet, dosyanın belirli bayt dizisini tanımlamaya ve zaman içinde değişip değişmediğini karşılaştırmaya yarar.
- Dijital imza, imza sahibini ve imzalanan verinin bütünlüğünü doğrulamaya yardımcı olur; her türlü teslim zincirinin yerine geçmez.
- Denetim kaydı, uygulama içindeki olayları kaydeder; mahkeme/kurum tutanağı veya resmî teslim kaydı değildir.
- Şifreleme, saklanan/taşınan verinin gizliliğini korumaya yöneliktir; erişim yönetimi ve anahtar yönetimi olmadan yeterli değildir.

## Önerilen materyal kabul akışı

1. Materyalin hangi kaynaktan, hangi yöntemle ve kim tarafından teslim alındığını kaydet.
2. Teslim anındaki dosya adını, boyutunu, türünü ve erişim durumunu envantere al.
3. Orijinal materyalin geldiği biçimi koru; mümkünse fiziksel kaynağı yazma korumalı ele al.
4. İçe alma sırasında hash al; çalışma kopyasının hash'ini karşılaştır.
5. Orijinal ile çalışma kopyasını ayrı tut; analiz işlemlerini yalnızca çalışma kopyasında yap.
6. Dönüştürme, normalleştirme veya yeniden kodlama yapıldıysa kaynak dosya, araç/sürüm ve parametreleri kaydet.
7. Türetilmiş her çıktı için kaynak dosya ve işlem ilişkisini sakla.
8. İşlem sonrasında orijinalin hash'ini yeniden doğrula.
9. Uyuşmazlıkta işlemi durdur, kullanıcıya görünür uyarı ver ve inceleme kaydı oluştur.
10. Şifreli yedekleme ve geri yükleme testini planla.

NISTIR 8387; dijital dosyalarda kaynak/transfer bilgisinin kaydını, hash kullanımını, güvenli saklamayı ve delil işlemlerinin belgelenmesini öneren teknik bir başvuru kaynağıdır. Bu öneriler tek başına Türkiye'de resmî delil zinciri veya hukuki kabul garantisi değildir.

## Sınır

Bu teknik tasarım, materyalin hukuka uygun elde edildiğini, teslim zincirinin resmî olarak kurulduğunu veya mahkemece delil olarak kabulünü garanti etmez. Uygulama “delil zinciri sağlandı” veya “delil hukuken geçerlidir” iddiası kullanmamalıdır. Fiziksel teslim tutanağı ve resmî kayıt, uygulama içi kayıttan ayrıdır.

## Public repo yasağı

Orijinal materyal, çalışma kopyası, hash manifestinde kişiyi/dosyayı tanımlayabilecek veriler, rapor ve gerçek görev günlükleri GitHub'a yüklenmez. Hash bilgisi de dosya veya vaka hakkında bağlam vererek hassas hale gelebileceğinden public issue/commit içinde tutulmaz.

## Kaynaklar

- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE Best Practices for Digital Evidence Collection](https://www.swgde.org/documents/published-complete-listing/18-f-002-best-practices-for-digital-evidence-collection/)
- [ISO/IEC 27037:2012](https://www.iso.org/standard/44381.html)
