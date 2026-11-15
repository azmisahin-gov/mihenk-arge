# Aşamalar ve Yol Haritası

> **Durum:** Sistem haritası v1.0 hazır; Wireframe v0.5 proje sahibi tarafından 15.11.2026'da kabul edildi. Uygulama eşleme ve teknik kabul aşamasına geçilecek.  
> **Güncelleme:** 15 Kasım 2026

## Güncel durak — Wireframe v0.5 kabul edildi; uygulama eşleme başlıyor

İlk teslimat 56.12 kontrollü uzman pilotudur. v0.3 ve v0.4 **kabul edilmemiş tarihsel taslaklardır**. [MİHENK Sistem Haritası v1.0](../02-urun/mihenk-sistem-ve-kullanici-akisi-v1.0.md) ana bilgi mimarisidir. [Wireframe v0.5](../02-urun/56-12-wireframe-v0.5.md) proje sahibi tarafından 15.11.2026 tarihinde kabul edilmiştir. [Kalite Güvencesi ve Denetim Modeli](../02-urun/56-12-kalite-ve-denetim-modeli-v1.0.md) bilirkişi öz kontrolünü, bağımsız dosya/rapor incelemesini ve MİHENK ürün denetimini ayırır.

**Wireframe v0.5 kabul edilmiştir:** [tasarım açıklaması](../02-urun/56-12-wireframe-v0.5.md), altı SVG pano ve [Kalite Güvencesi/Denetim Modeli](../02-urun/56-12-kalite-ve-denetim-modeli-v1.0.md). v0.3/v0.4 tarihsel ve kabul edilmemiş taslaklardır. Uygulama aşaması artık tasarımın mevcut prototipte hangi ölçüde karşılandığını denetleme, eski dalları güvenli karşılaştırma ve backlog'u netleştirme ile başlayacaktır. Tasarım kabulü teknik kabul değildir.

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

Sistem tasarımı ve ilk teslimat ürün sözleşmesi kullanıcı tarafından gözden geçirilip v0.5 wireframe kabul edildiğinden sonra mevcut prototip üzerinde önceliklendirilmiş düzeltmeler yapılır. Öncelik: ilk kurulum/profil, görevlendirme belgesinin otomatik okunması, bir görevde çoklu materyal ve soru, 56.12 ses/transkript akışı, tek rapor önizlemesi, ardından UYAP Editör biçim doğrulaması. Yeni teknik özellikler bu uçtan uca akışa katkı sağlamıyorsa bekletilir.

## Aşama 6 — Pilot ve doğrulama

- Sentetik veya açık lisansı doğrulanmış veri kullan.
- Gerçek kullanıcılarla görev tamamlama, hata ve manuel müdahale senaryolarını ölç.
- Güvenlik, yedek/geri yükleme, performans ve erişilebilirliği doğrula.
- Pilot sonucuna göre kapsamı daralt veya genişlet.

## Aşama 7 — Bağımsız eleştiri ve yayın hazırlığı

Mevzuat, veri güvenliği, uzmanlık sınırı, lisans ve teknik tasarım bağımsız incelemeye tabi tutulur; açık kritik bulgular kapatılmadan yayın yapılmaz.
\n\n## v0.5 tasarım kabulü ve uygulama kapısı\n\nProje sahibi v0.5 tasarımını kabul etti. Yeni oturumda önce mevcut uygulama main ve üç eski feature dalı dosya/test bazında karşılaştırılacak; açık issue'lar gerçek mevcut durumla eşlenecek. Kullanıcı onayı olmadan eski dal silinmeyecek veya güvenli değişiklikler kaybedilmeyecek. Sonra accepted UI tasarımı mevcut uygulamada aşamalı uygulanacak. Alan uzmanı ve bağımsız teknik/güvenlik denetimi pilot öncesinde ayrıca gereklidir.\n

## Aşama 5A — Mevcut uygulama denetimi ve backlog eşlemesi

- `mihenk` main dalını ve güncel preview/release sürümünü doğrula.
- Üç eski feature dalını main ile dosya, commit, test ve davranış bakımından karşılaştır; henüz silme veya doğrudan merge yapma.
- Açık issue #3 ve #29–#34'ü v0.5 ekranları ve K-01–K-12 ile eşle; yinelenen işleri birleştirmeden önce kapsamı karşılaştır.
- Önce kullanıcı blokajlarını ve mevcut çalışan özellikleri doğrula; test/CI sonucu olmadan “çalışıyor” işareti verme.
- Her uygulama dilimini küçük PR, test ve canlı önizleme ile doğrula.

## Aşama 5B — Çift kalite/denetim kabulü

- Bilirkişinin görev/rapor öz denetimi ve kaynak izlenebilirliği.
- Gerektiğinde bağımsız ikinci uzman incelemesi için denetim paketi.
- MİHENK ürün kalite dosyası, K-01–K-12 ve bağımsız güvenlik/UX/meslekî testleri.
