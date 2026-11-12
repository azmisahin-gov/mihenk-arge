# Bütünleşik Uzmanlık Modülü Mimarisi

> **Durum:** Ürün/mimari hedef — teknoloji seçimi değildir  
> **Güncelleme:** 13 Kasım 2026

## 1. Ürün ilkesi

MİHENK, bilirkişiyi farklı masaüstü uygulamalarına, web sitelerine, komut satırı araçlarına veya dosya dönüştürücülere yönlendiren bir başlatıcı olmayacaktır.

**Kullanıcı tek bir MİHENK uygulamasında çalışır.** Uzmanlık alanının gerektirdiği inceleme, ölçüm, dönüştürme, doğrulama, rapor hazırlığı ve kalite kontrol araçları MİHENK'in kendi arayüzünde sunulur. Alttaki motorlar MİHENK tarafından yönetilen, sürümü ve lisansı doğrulanmış yerleşik kütüphane, yerel çalışma zamanı veya izole işçi süreçleri olabilir.

UYAP Editörü ve Adalet e-İmza gibi resmî Bakanlık uygulamaları özel durumdur: kaynak kodu ve yeniden dağıtım lisansı doğrulanmadığı için MİHENK'e gömülmez veya yükleyiciye eklenmez. MİHENK resmî sürece hazır belge/rapor paketi sağlar; imza ve resmî gönderim son aşamada yetkili resmî uygulamalarda kalır. Bu sınırlama, MİHENK'in kendi uzmanlık araçlarının ayrı programlar olmasını gerektirmez.

## 2. Katmanlar

### A. MİHENK ortak çekirdeği
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

### B. Uzmanlık modülleri
Bir modül belli bir uzmanlık veya ilişkili uzmanlık grubu için gereken araç ve iş akışlarını içerir. 56.12 modülü:
- Çoklu ses içe alma ve ses envanteri.
- Ses formatı/metadata ve süre kontrolleri.
- Yerel ASR motorlarının seçimi ve çalıştırılması.
- Zaman damgası, ses-metni eşleştirme, tekrar dinleme ve düzeltme.
- Nötr konuşmacı sıralaması ve belirsiz bölüm işaretleme.
- Kaynak ses bağlantılı bulgu/alıntı ve rapor bölümü üretimi.
- 56.12'ye özgü kalite testleri.

Başka uzmanlık modülleri kendi ihtiyaçlarına göre farklı araç seti, veri modeli, yöntem ve kontrol listelerine sahip olabilir.

### C. Araç ve motor katmanı
- Yerleşik kütüphane/API.
- MİHENK dağıtımı içinde lisansı ve sürümü sabitlenmiş yerel motor.
- İzole worker/yardımcı süreç.
- İzinli yerel donanım/işletim sistemi bağlantısı.
- Yetkilendirilmiş haricî servis (ancak hukuk/gizlilik onayı ve kullanıcı izniyle).

Kullanıcı arayüzü ve görev akışı MİHENK'te kalır. Worker ayrı süreçte çalışsa bile kullanıcı ayrı bir program açmak zorunda değildir.

## 3. Modül sözleşmesi

Her modül manifestinde:
- Benzersiz modül kimliği, Türkçe açıklaması, sürüm ve çekirdek uyumluluğu.
- Uzmanlık alanı/kapsamı ve kapsam dışı işlemler.
- Girdi/çıktı türleri ve ortak veri sözleşmeleri.
- Araç listesi, yöntem ve parametre sürümleri.
- Dosya, donanım, ağ, GPU, işlemci/bellek izinleri.
- Paket/model checksum, tam bağımlılık ağacı, lisans/SBOM.
- Kaynak imzası, test paketi, kabul ölçütü ve bilinen sınırlamalar.
- Güncelleme kanalı ve geri alma bilgisi.

Eski görevlerin işlem kayıtları çalıştırılan modül/araç/model sürümünü korumalıdır.

## 4. Güvenli modül yürütme

- Yalnızca MİHENK tarafından incelenmiş ve imzalanmış paketler kataloğa alınır.
- Her görev modülü yalnızca o görevin gerekli materyaline erişir.
- Orijinal materyal salt okunur; modül çalışma kopyası ve türevlerle çalışır.
- İşçi süreç dosya yolu, bellek, CPU/GPU, ağ ve süre bakımından sınırlandırılır.
- Ağ erişimi varsayılan olarak kapalıdır.
- Model ve araç güncellemeleri imza/hash, sürüm sabitleme, güvenlik taraması ve geri alma ile yönetilir.
- Modül arızası diğer görevleri ve veri kasasını etkilemez.

## 5. ASR modül ilkesi

- ASR motoru MİHENK'e gömülü/beraber dağıtılan yerel çalışma zamanı olarak sunulur; kullanıcı ASR web servisine dosya yüklemez.
- İlk adaylar Whisper ailesi (whisper.cpp veya doğrulanmış başka yerel backend), Türkçe Whisper M1 uyarlaması ve küçük bağımsız ufakzeka-kulak modelidir.
- Motor seçimi model ağırlığı, lisans/veri kökeni, Türkçe doğal konuşma başarımı, GPU/CPU performansı ve tekrarlanabilir testle yapılır.
- Birden fazla motorun çıktısı otomatik uzlaştırılıp doğru kabul edilmez; uyuşmazlıklar dinleme kuyruğuna alınır.
- ASR çıktısı makine taslağıdır; nihai metin ve bilirkişi değerlendirmesi ayrı sürümlenir.

## 6. Otomatik çalışma biçimi

- Görev Profili tamamlandığında ilgili modül belirlenir.
- Güvenli/tekrarlı işlemler otomatik sıraya konur ve kesintiden sonra devam eder.
- Belirsiz/çelişkili talimat, bozuk materyal veya güvenlik riski yalnızca ilgili adımı istisnaya çıkarır.
- Uzman modül çıktısı ile bilirkişinin doğruladığı bulgu/kanaat ayrı tutulur.
- Rapor ve ek paketi ortak rapor motoruna aktarılır.
- Nihai meslekî kanaat, resmî imza ve UYAP teslimi bilirkişiye aittir.

## 7. Kabul ölçütleri

- Kullanıcı tek MİHENK arayüzünde görev ve modül işlerini yürütür.
- Modülün alt motorunu ayrıca kurma/yönetme zorunluluğu yoktur.
- Modül sürüm, lisans, imza ve bağımlılık bilgileri denetlenebilir.
- Ağ erişimi izinli değilse modül çevrimdışı çalışır.
- Görev verisi ve işlem çıktıları görevler arasında yalıtılır.
- Araç sürümü ve parametreleri işlem kaydına bağlanır.
- Yeni uzmanlık modülü ortak çekirdeği değiştirmeden eklenebilir.
- Resmî Bakanlık yazılımları kendi doğrulanmış imza/teslim alanında kalır.
