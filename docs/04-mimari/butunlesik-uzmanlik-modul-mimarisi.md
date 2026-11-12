# Bütünleşik Uzmanlık Modülü Mimarisi

> **Durum:** Ürün/mimari hedef — teknoloji seçimi değildir  
> **Güncelleme:** 13 Kasım 2026

## 1. Ürün ilkesi

MİHENK, bilirkişiyi farklı masaüstü uygulamalarına, web sitelerine, komut satırı araçlarına veya dosya dönüştürücülere yönlendiren bir başlatıcı olmayacaktır.

**Kullanıcı tek bir MİHENK uygulamasında çalışır.** Uzmanlık alanının gerektirdiği inceleme, ölçüm, dönüştürme, doğrulama, rapor hazırlığı ve kalite kontrol araçları MİHENK'in kendi arayüzünde sunulur. Alttaki motorlar MİHENK tarafından yönetilen, sürümü ve lisansı doğrulanmış yerleşik kütüphane, yerel çalışma zamanı veya izole işçi süreçleri olabilir. Bu teknik ayrıntı kullanıcıya ayrı uygulama kurma/yönetme işi çıkarmamalıdır.

Bu hedef, bütün uzmanlık alanlarının tüm araçlarının ilk sürümde tamamlanacağı anlamına gelmez. Hedef; yeni uzmanlık modüllerinin aynı güvenli ortak platforma eklenebildiği, kapsamlı ve uzun ömürlü tek bir uygulama oluşturmaktır. Modüller gerçek kullanıcı akışı ve meslekî yöntem doğrulamasıyla sırayla eklenir.

## 2. Katmanlar

### A. MİHENK ortak çekirdeği

Her uzmanlık alanında ortak olan hizmetler:
- Kullanıcı ve yerel çalışma alanı.
- Görev Profili, görevlendirme belgesi ve görev koşulları.
- Süre, iş listesi, aşama ve bildirim.
- Fiziki/dijital materyal kabulü, envanter ve orijinal/kopya yönetimi.
- Güvenli dosya kasası, şifreleme ve yedekleme.
- İş akışı motoru, kuyruk, ilerleme, kesinti sonrası devam ve hata toparlama.
- Modül/araç kataloğu ve sürüm yöneticisi.
- Ortak belge modeli, şablon ve rapor üretimi.
- Görev soruları, kalite kapısı ve kontrol listesi.
- Denetim/işlem kaydı ve teslim öncesi çıktı paketi.
- Modüller için izin, kaynak ve güvenlik sınırı.

### B. Uzmanlık modülleri

Bir modül, belli bir uzmanlık veya birbiriyle ilişkili uzmanlık grubu için gereken araç ve iş akışlarını içerir. Örnek olarak 56.12 modülü:
- Çoklu ses içe alma ve ses envanteri.
- Ses formatı/metadata ve süre kontrolleri.
- Makine transkripsiyonu.
- Zaman damgası, ses-metni eşleştirme, tekrar dinleme ve düzeltme.
- Nötr konuşmacı sıralaması ve belirsiz bölüm işaretleme.
- Kaynak ses bağlantılı bulgu/alıntı ve rapor bölümü üretimi.
- 56.12'ye özgü kalite testleri.

Başka uzmanlık modülleri kendi ihtiyaçlarına göre farklı araç seti, veri modeli, yöntem ve kontrol listelerine sahip olabilir. Ses araçları bütün bilirkişilere zorunlu değildir; başka modülün gereksinimi 56.12'nin sınırına zorlanmaz.

### C. Araç ve motor katmanı

Modül içindeki her işlevin uygulamaya bağlanma biçimi:
- Yerleşik kütüphane/API.
- MİHENK dağıtımı içinde lisansı ve sürümü sabitlenmiş yerel motor.
- İzole worker/yardımcı süreç.
- İzinli yerel donanım/işletim sistemi bağlantısı.
- Yetkilendirilmiş haricî servis, ancak hukuk/gizlilik onayı ve kullanıcı tarafından etkinleştirilmiş izinle.

Kullanıcı arayüzü ve görev akışı MİHENK'te kalır. Arka plan worker'ı ayrı süreçte çalışsa bile kullanıcı ayrı bir program açmak zorunda değildir. Modülün kullandığı motorlar lisans, güvenlik, sürüm ve destek açısından MİHENK tarafından yönetilir.

## 3. Modül sözleşmesi

Her modül dağıtım paketi en az şu bilgileri taşımalıdır:
- Benzersiz modül kimliği, adı ve Türkçe açıklaması.
- Sürüm ve desteklenen MİHENK çekirdek sürüm aralığı.
- Uzmanlık alanı/kapsamı ve açıkça kapsam dışı işlemler.
- Girdi/çıktı türleri ve ortak veri sözleşmeleri.
- Araç listesi, yöntem ve parametre sürümleri.
- İstenen sistem izinleri (dosya, donanım, ağ, GPU, işlemci/bellek).
- Ağ erişim politikası; varsayılan olarak kapalı.
- Paket, model ve veri dosyalarının sürüm/hash bilgileri.
- Tam bağımlılık ağacı ve üçüncü taraf lisansları/SBOM.
- Test paketi, kabul ölçütü, bilinen sınırlamalar ve güvenlik bildirimi.
- Kaynak imza/sağlayıcı kimliği ve güncelleme kanalı.

Bir modül yeni sürüme güncellendiğinde eski görevlerin işlem kayıtları hangi modül/araç sürümünde yürütüldüğünü korumalıdır.

## 4. Güvenli modül yürütme

- Modül kataloğuna yalnızca MİHENK tarafından incelenmiş ve imzalanmış paketler alınır.
- Kullanıcının internetten rastgele eklenti yüklemesi varsayılan olarak mümkün değildir.
- Her görev modülü yalnızca o görev için gerekli materyale erişir.
- Orijinal materyal salt okunur kalır; modül çalışma kopyası ve türevlerle çalışır.
- Her worker süreç sınırı, dosya yolu, bellek, işlemci/GPU, ağ ve zaman aşımı ile kısıtlanır.
- Modül internet erişimi istemiyorsa ağ kapalı çalışır. Haricî servis kullanımı için açık gerekçe, izin ve veri aktarım değerlendirmesi gerekir.
- Modül arızası MİHENK'in diğer görevlerini ve veri kasasını etkilememelidir.
- Başarısız güncelleme geri alınabilir; aktif bir inceleme sırasında sürüm değişikliği kullanıcıya bildirilmeden yapılmaz.
- Modül çıktısı kaynak dosya, yöntem, sürüm, parametre ve zamanla ilişkilendirilir.

## 5. Otomatik çalışma biçimi

- Görev Profili tamamlandığında ilgili modül(ler) belirlenir.
- Modül araçları gerekli girdileri kontrol eder ve güvenli/tekrarlı adımları otomatik sıraya koyar.
- İş akışı bağımlılıkları yönetir; tamamlanan adımlar tekrar çalıştırılmadan korunur.
- Belirsiz/çelişkili alan, bozuk materyal veya güvenlik riski yalnızca ilgili adımı istisnaya çıkarır.
- Uzmanlık modülünün ürettiği makine çıktısı, ölçüm ve öneriler; uzman tarafından doğrulanan bulgu ve nihai kanaatten ayrı tutulur.
- Rapor ve ek paketi ortak rapor motoruna teslim edilir.
- Nihai meslekî kanaat, resmî imza ve UYAP teslimi bilirkişiye aittir.

## 6. Araçların uygulamaya dahil edilmesi

“Araçlar MİHENK'in bünyesinde olacak” ilkesi, her kütüphaneyi MİHENK'in sıfırdan yazacağı anlamına gelmez. Uygun açık kaynak kütüphane ve motorlar, lisans uyumu ve güvenlik incelemesi sonrası ürün dağıtımına dahil edilebilir. Ancak:
- MİHENK kullanıcıya ayrı uygulama açtırmaz.
- Kullanıcıdan her uzmanlık için manuel Python/Java/Node kurulumu istenmez.
- Her araç MİHENK tarafından sürümlenir, güncellenir ve denetlenir.
- Ağ, lisans, model indirme ve üçüncü taraf hizmetleri için net izin kuralları olur.
- Uygun açık kaynak bileşen bulunamazsa bu gerçek ürün kararı olarak kaydedilir; lisanssız veya güvensiz araç kullanılmaz.

## 7. Ürün kapsamı sınırı

MİHENK'in uzun vadeli hedefi bilirkişinin görevini tek uygulama içinden yönetip tamamlayabileceği kapsamlı bir platformdur. Bunun güvenilir olması için her uzmanlık modülünde:
1. Resmî görev alanı ve meslekî yöntem doğrulanır.
2. Bilirkişinin kullandığı araçlar ve manuel adımlar çıkarılır.
3. Otomatikleştirilebilir işler belirlenir.
4. Uygun açık kaynak/yerleşik motorlar araştırılır.
5. Veri, güvenlik, lisans ve hata riskleri değerlendirilir.
6. Sentetik/açık verilerle test edilir.
7. Gerçek kullanıcı kabulüyle modül yayımlanır.

Bu nedenle 56.12 ilk somut kullanım örneğidir; bütün MİHENK'in ses transkripsiyonuna indirgenmesi veya ilk modül seçiminin bugünden kesinleştirilmesi değildir.

## 8. Kabul ölçütleri

- Kullanıcı tek MİHENK arayüzünde görev ve modül işlerini yürütebilir.
- Modülün alt motorunu ayrıca açma/kurma/yönetme zorunluluğu yoktur.
- Modül sürüm, lisans, imza ve bağımlılık bilgileri denetlenebilir.
- Bir modülün hatası diğer modülleri ve görevleri etkilemez.
- Ağ erişimi izinli değilse modül çevrimdışı çalışır.
- Görev verisi ve işlem çıktıları görevler arasında yalıtılır.
- Araç sürümü ve parametreleri rapor/işlem kaydına bağlanır.
- Yeni uzmanlık modülü ortak çekirdeği değiştirmeden eklenebilir.
- Nihai kanaat ve resmî imza/teslim sınırı korunur.
