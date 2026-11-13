# Aşamalar ve Yol Haritası

 > **Durum:** Keşif ve 56.12 minimum pilot kapsamı tanımlı; uzman doğrulaması ve PoC bekliyor  
> **Güncelleme:** 13 Kasım 2026

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

## 56.12 modül dikey dilimi — İlk pilot alt akışı

Bu çalışma genel MİHENK platform MVP'sinden ayrıdır. 56.12 için [minimum kapsam ve 12 kabul kapısı](../03-uzmanlik-modulleri/ilk-pilot/56-12-minimum-surum-kapsami.md) tanımlanmıştır; bu, modülün ürünleştiği veya alan uzmanı tarafından onaylandığı anlamına gelmez.

1. **M0 – Kapsam doğrulaması:** B-01'in gerçek giriş ses biçimleri, rapor/teslim çıktısı ve meslekî kontrol noktaları doğrulanır.
2. **M1 – Yerel dikey dilim:** Bir ASR motoruyla ses alımı → yerel transkript → sesle karşılaştırarak düzeltme → çıktı akışı denenir.
3. **M2 – Gerekiyorsa model kıyası:** Aynı küçük insan referanslı testte en fazla bir alternatif ölçülür.
4. **M3 – Kabul kapıları:** 12 minimum güvenlik/işlev kapısı sentetik veya izinli yerel veride uygulanır.
5. **M4 – Uzman pilotu:** Zaman ve düzeltme eforu kazanımı ile kabul/ret gerekçesi kaydedilir.

Özel benchmark aracı, otomatik diarization ve ileri ses işleme bu alt akışın ön koşulu değildir. İlk dikey dilim gerçek cihaz ve uzman iş akışı doğrulandıktan sonra mimari kararları besler.

## Aşama 4 — Sıfırdan mimari ve teknoloji kararı

- En az iki teknoloji/mimari alternatifini karşılaştır.
- Yerel/web/mobil, çevrimdışı çalışma, belge işleme, güvenlik ve veri modelini kararlaştır.
- Lisans ve üçüncü taraf bağımlılık politikasını belirle.
- Uygulama deposunda CI, test ve release iskeletini kur.

## Aşama 5 — Uygulama geliştirme

Önceki karar kapıları geçildiğinde başlanır. İlk dikey dilim, onaylanmış sentetik görevlendirme belgesini alıp Görev Profili ve görev bazlı kontrol listesini otomatik oluşturmalıdır. Ardından materyal envanteri, uzmanlık işlemi ve rapor üretimi eklenir.

## Aşama 6 — Pilot ve doğrulama

- Sentetik veya açık lisansı doğrulanmış veri kullan.
- Gerçek kullanıcılarla görev tamamlama, hata ve manuel müdahale senaryolarını ölç.
- Güvenlik, yedek/geri yükleme, performans ve erişilebilirliği doğrula.
- Pilot sonucuna göre kapsamı daralt veya genişlet.

## Aşama 7 — Bağımsız eleştiri ve yayın hazırlığı

Mevzuat, veri güvenliği, uzmanlık sınırı, lisans ve teknik tasarım bağımsız incelemeye tabi tutulur; açık kritik bulgular kapatılmadan yayın yapılmaz.
