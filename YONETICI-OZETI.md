# MİHENK — İlk Araştırma Yönetici Özeti

> **Durum:** TASLAK — hukukçu ve bilirkişi doğrulaması gerekli  
> **Araştırma tarihi:** 12 Kasım 2026

## Karar özeti

Bugünkü kanıtlar genel bir bilirkişi platformunun hemen kodlanmasını haklı çıkarmıyor. Öneri: MİHENK'i araştırma/ürün karar deposu olarak aç; aktif bilirkişi görüşmelerini gerçekleştir; 56.12'yi yalnızca kontrollü pilot adayı olarak kullan; mevcut `forensic-transcriber-next` uygulamasını sentetik/izinli veriyle güvenilirlik ve kullanılabilirlik yönünden test et. Kullanıcı ihtiyacı kanıtlanmadan ortak platform geliştirme.

## Doğrulanan temel bulgular

- 6754 sayılı Kanun, bilirkişinin bağımsız, tarafsız ve objektif çalışmasını; uzmanlık/özel/teknik bilgi sınırında kalmasını; hukuki nitelendirme yapmamasını; görevi şahsen yapmasını ve sır saklamasını düzenler.
- 2026 sicile kabul esasları, e-Devlet üzerinden UYAP Bilirkişi Portal'a elektronik/mobil imza ile başvuruyu, tek bölge kuruluna başvuru ilkesini ve en fazla üç temel alan altında altı alt alan seçimini içerir. Genel koşulların yanında alan özelindeki yeterlilikler de incelenmelidir.
- 2025 başvuru ilanı 24.12.2025–26.01.2026 tarihlerini duyurmuş; başvuru süresi 16.02.2026 23:59'a kadar uzatılmıştır. 05.06.2026 ek duyurusu, listelerin ilan tarihini 02.10.2026 olarak güncellemiştir. Bu araştırma planlanan tarihte listelerin gerçekten yayımlandığını doğrulayamadı.
- Temel eğitim 24 ders saati (12 teori + 12 uygulama), yenileme eğitimi en az 6 ders saati olarak 05.05.2025 tarihli Daire Başkanlığı duyurusunda belirtilmiştir.
- 2026 listesinde 56.11 ve 56.12 ayrı alanlardır. 56.12, metne dönüştürme ile sınırlı ve yargı mercilerinin ses/görüntü bilişim sistemi istisnası içerir.
- UYAP Bilirkişi Portalı dosya inceleme, rapor/ek rapor gönderimi, ön rapor/kurul iletişimi, çekilme ve ücret bilgisi gibi işlevler tanıtmaktadır. Kamuya açık üçüncü taraf API dokümantasyonu veya yazılı entegrasyon yetkisi bu taramada doğrulanmamıştır.
- 2026 bilirkişilik asgari ücret tarifesi 01.01.2026'da yürürlüğe girmiştir. Ek rapor ücreti; yeni bilgi talebi ile mevcut rapordaki eksiklik/belirsizliği giderme ayrımına bağlıdır.
- `azmisahin-gov/mihenk` repo zaten var ve GitHub API “This repository is empty” döndürdü.
- `forensic-transcriber` Electron; `forensic-transcriber-next` Tauri/Rust/React yaklaşımında ve ikisi de AGPL-3.0-only olarak lisanslanmış. Her ikisinin üçüncü taraf bileşenleri ayrı lisanslıdır. Kod taşıma lisans incelemesi gerektirir.

## İlk pilot

56.12 en iyi pazar olarak kanıtlanmış değildir; ancak resmî ayrımının açık olması ve mevcut iki teknik prototip nedeniyle en somut değerlendirme pilotudur. En az 5 aktif 56.12 bilirkişisiyle görüşme, insan referans transkript, sentetik/izinli materyal, yedek/restore testi ve uzmanlık sınırı kontrolü olmadan gerçek vaka pilotu yapılmamalıdır.

## En önemli ürün sınırları

- UYAP işlemlerini taklit etme veya izinsiz otomasyon yok.
- Bilirkişi yerine kanaat, hukuki değerlendirme veya kimlik tespiti üretme yok.
- Orijinal materyal ile çalışma kopyası ayrı. Hash, audit log ve şifreleme ayrı amaçlara hizmet eder; hiçbiri tek başına hukuki delil zinciri garantisi değildir.
- Gerçek dosya ve kişisel veriler araştırma GitHub deposuna konmaz.
- Bulut, senkronizasyon ve çok kullanıcılı işbirliği ancak hukuk/veri koruma ve kullanıcı ihtiyacı kanıtlandıktan sonra.

## Kapılar

1. 2025 değişikliği dahil Yönetmelik konsolide metnini hukukçu ile doğrula.
2. 2026 uzmanlık listesinin tüm 35 sayfasını alan ve yeterlilik düzeyinde envanterle.
3. UYAP ekranlarının güncel davranışını yetkili gerçek kullanıcı ile teyit et.
4. 8–12 bilirkişi görüşmesi ve üç görev akışı gözlemi.
5. 56.12 pilotunda insan referans veri kümesi, güvenilirlik, yedek/restore ve hata kurtarma.
6. Bağımsız hukuk/teknik değerlendirme.

## Nihai öneri

**Seçenek 4 — şimdilik yeni ürün kodlamamak; araştırma ve kullanıcı doğrulamasını sürdürmek.** Paralelde var olan 56.12 uygulaması sınırlı pilot nesnesi olsun. Pilot kanıtları ortak platformun gerekliliğini gösterirse ayrı mimari/ürün kararı alınsın.
