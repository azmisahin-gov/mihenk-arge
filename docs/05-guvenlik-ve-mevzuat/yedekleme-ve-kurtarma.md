# Yedekleme ve Kurtarma

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## P0 gereksinim

Vaka verisi üretim ortamında kullanılmadan önce doğrulanmış yedekleme ve geri yükleme akışı olmalıdır. Yalnızca yedek dosyası oluşturmak yeterli değildir; restore testi geçmelidir.

## Önerilen yaklaşım

- Tek dosya değil, veritabanı + materyal dizini + uygulama metadata'sı tutarlı snapshot olarak alınmalı.
- Snapshot manifestinde uygulama sürümü, şema sürümü, yedek tarihi, dosya envanteri ve hash değerleri bulunmalı.
- Yedek şifrelenmeli; anahtar yedek dosyasından ayrı saklanmalı.
- Atomik temp-then-rename yazımı, DB transaction ve restore öncesi bütünlük kontrolü kullanılmalı.
- Geri yükleme mevcut veriyi ezmeden önce kullanıcı onayı ve yedek kopya gerektirmeli.
- Yedek içeriği aynı retention ve gizlilik kurallarına tabi olmalı.
- Otomatik yedekleme kapatılabilir olmalı ama veri kaybı riski açıkça gösterilmeli.

## Test senaryoları

Bozuk DB, yarım export, yarım import, dosya kaybı, disk dolması, uygulamanın işlem ortasında kapanması, yanlış yedek, yedekten seçici geri yükleme, şifre anahtarının kaybı ve yedek dosyasının başka cihaza taşınması.

## Açık karar

RPO/RTO, yedek sıklığı, şifreleme çözümü ve saklama süresi kullanıcı çalışma alışkanlığı ve mevzuat/hukukçu değerlendirmesiyle belirlenmelidir.

## Kaynaklar

- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [KVKK — Özel Nitelikli Kişisel Verilerin İşlenmesine İlişkin Rehber](https://www.kvkk.gov.tr/Icerik/8184/Ozel-Nitelikli-Kisisel-Verilerin-Islenmesine-Iliskin-Rehber)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
