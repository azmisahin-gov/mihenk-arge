# Aşamalar ve Yol Haritası

> **Durum:** Sistem ve kullanıcı akışı v1.0 hazır; wireframe v0.4 taslağı oluşturuldu ve değerlendirme bekliyor. v0.3 kabul edilmedi.  
> **Güncelleme:** 15 Kasım 2026

## Güncel durak — Wireframe v0.4 taslağı değerlendirmede

İlk teslimat 56.12 kontrollü uzman pilotudur. v0.3 **kabul edilmemiştir**. Araştırma, mevzuat ve ürün sözleşmesi doğrulamasından sonra [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](../02-urun/mihenk-sistem-ve-kullanici-akisi-v1.0.md) hazırlandı. Bu belge ana gezinmeyi, profil/kasa/uzmanlık/modül ayrımını, yerel ASR sahipliğini, görevlendirme ve çoklu materyal/soru akışını, tek rapor yaklaşımını ve hata durumlarını tanımlar.

**Wireframe v0.4 taslağı hazırdır:** [tasarım açıklaması](../02-urun/56-12-wireframe-v0.4.md) ve sekiz görsel pano. İlk kurulumdan tek rapor önizlemesine, profil/kasa/modül/ASR yönetimine, çoklu materyal/soruya ve hata/kurtarma durumlarına kadar temel ekranlar çizildi. Sıradaki iş kullanıcının panoları değerlendirmesi, gerekli revizyonların yapılması ve tasarım kabulüdür. v0.4 kabul edilmeden uygulama UI kodlaması başlamaz.

Uygulama deposunda mevcut bir masaüstü prototipi ve 0.1.0-53 kullanıcı önizleme durumu vardır. Uygulama geliştirmesi sıfırdan başlamış gibi ele alınmamalı; mevcut kod korunmalı, bilinen kullanıcı blokajları kaybolmadan takip edilmelidir.

## Aşama 0 — Proje başlangıcı ve yönetişim

- Araştırma ve uygulama depoları ayrıldı.
- Önceki transkripsiyon projelerinin yalnızca deneyim referansı olduğu; kod/altyapı taşınmayacağı karara bağlandı.
- Türkçe belge ve GitHub iletişim standardı belirlendi.

## Aşama 1 — Kullanıcı ve problem keşfi

- İlk tek kullanıcıyla görevlendirme, fiziki materyal kabulü, inceleme ve rapor hazırlığı akışı gözlemlendi.
- Bulgular ortak çekirdek ve 56.12'ye özgü hipotezlere ayrıldı.
- Farklı uzmanlık/deneyimlerde kullanıcılarla tekrar eden ihtiyaçların doğrulanması sürüyor.

## Aşama 2 — Görevlendirme ve resmî süreç doğrulama

- Yönetmelik m.51–52'nin Görev Profili alanlarına dönüştürülmesi.
- Görevlendirme belgesindeki kapsam, sorular, süre, ücret, materyal ve teslim koşullarının belirlenmesi.
- Fiziki teslim ile UYAP elektronik erişim yollarının ayrılması.
- Resmî rapor şablonu kataloğu, UDF ve e-imza akışının güncel sürümde doğrulanması.
- Sentetik görevlendirme belgeleriyle otomatik çıkarım ve istisna testleri.
- Farklı görev türleri ve bilirkişi alanlarıyla ortak modelin sınanması.

## Aşama 3 — Ürün tanımı

- Problem tanımı ve hedef kullanıcı.
- Görev Profili ve ortak çekirdek gereksinimleri.
- Uzmanlık modülleri ile göreve özel iş akışlarının ayrımı.
- Otomatik yürütülecek işler, istisna yönetimi ve insan karar sınırları.
- Rapor üretimi, kalite kapısı ve çıktı formatı kabul kriterleri.
- **Sistem/kullanıcı akışı v1.0 tamamlandı:** gezinme, ayar sahipliği, profil, kasa, uzmanlık/modül, ASR, görev, materyal, transkript, sorular, tek rapor, güncelleme ve istisna akışları tek referansta toplandı.

## 56.12 modül dikey dilimi — İlk pilot alt akışı

56.12, proje sahibinin talimatıyla ilk kullanılabilir teslimatın odağıdır; MİHENK'in uzun vadeli modüler platform hedefi korunur. Bu ilk pilot, diğer uzmanlıkların kapsamını belirlemez. [Minimum kapsam ve 12 kabul kapısı](../03-uzmanlik-modulleri/ilk-pilot/56-12-minimum-surum-kapsami.md) tanımlıdır; wireframe v0.3 kullanıcı tarafından henüz kabul edilmemiş ve alan uzmanı onayından geçmemiştir.

1. **M0 – Kapsam doğrulaması:** B-01'in gerçek giriş ses biçimleri, rapor/teslim çıktısı ve meslekî kontrol noktaları doğrulanır.
2. **M1 – Yerel dikey dilim:** Bir ASR motoruyla ses alımı → yerel transkript → sesle karşılaştırarak düzeltme → çıktı akışı denenir.
3. **M2 – Gerekiyorsa model kıyası:** Aynı küçük insan referanslı testte en fazla bir alternatif ölçülür.
4. **M3 – Kabul kapıları:** 12 minimum güvenlik/işlev kapısı sentetik veya izinli yerel veride uygulanır.
5. **M4 – Uzman pilotu:** Zaman ve düzeltme eforu kazanımı ile kabul/ret gerekçesi kaydedilir.

Özel benchmark aracı, otomatik diarization ve ileri ses işleme bu alt akışın ön koşulu değildir. İlk dikey dilim gerçek cihaz ve uzman iş akışı doğrulandıktan sonra mimari kararları besler.

## Aşama 4 — Ürün ve mimari kararlarının tamamlanması

- En az iki teknoloji/mimari alternatifini karşılaştır.
- Yerel/web/mobil, çevrimdışı çalışma, belge işleme, güvenlik ve veri modelini kararlaştır.
- Lisans ve üçüncü taraf bağımlılık politikasını belirle.
- Mevcut prototip mimarisi ve testleri gereksinimlere göre gözden geçir; gerekmedikçe sıfırdan başlama.

## Aşama 5 — Uygulama geliştirme

Sistem tasarımı ve ilk teslimat ürün sözleşmesi kullanıcı tarafından gözden geçirilip v0.4 wireframe kabul edildikten sonra mevcut prototip üzerinde önceliklendirilmiş düzeltmeler yapılır. Öncelik: ilk kurulum/profil, görevlendirme belgesinin otomatik okunması, bir görevde çoklu materyal ve soru, 56.12 ses/transkript akışı, tek rapor önizlemesi, ardından UYAP Editör biçim doğrulaması. Yeni teknik özellikler bu uçtan uca akışa katkı sağlamıyorsa bekletilir.

## Aşama 6 — Pilot ve doğrulama

- Sentetik veya açık lisansı doğrulanmış veri kullan.
- Gerçek kullanıcılarla görev tamamlama, hata ve manuel müdahale senaryolarını ölç.
- Güvenlik, yedek/geri yükleme, performans ve erişilebilirliği doğrula.
- Pilot sonucuna göre kapsamı daralt veya genişlet.

## Aşama 7 — Bağımsız eleştiri ve yayın hazırlığı

Mevzuat, veri güvenliği, uzmanlık sınırı, lisans ve teknik tasarım bağımsız incelemeye tabi tutulur; açık kritik bulgular kapatılmadan yayın yapılmaz.
