# 56.12 Araçlar ve Yöntemler

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Araçların rolü

- **FFmpeg/FFprobe:** Medya çözme ve teknik metadata okuma için genel amaçlı araçlar. Tek başına adli yöntem veya bilirkişi görüşü değildir.
- **whisper.cpp / Whisper ailesi:** Otomatik konuşma tanıma. Makine çıktısı taslaktır; insan doğrulaması olmadan nihai transkript kabul edilmemelidir.
- **Praat:** Fonetik/ses incelemede kullanılan araştırma aracı; 56.12 için otomatik olarak gerekli değildir.
- **Audacity:** Ses dinleme/düzenleme genel aracıdır; orijinal materyalin değiştirilmeyip çalışma kopyasında çalışılması gerekir.

## Ses materyali ilkeleri

SWGDE forensic audio v2.5, mümkün olduğunda orijinal veya elde edilebilir en erken nesil kaydın istenmesini ve materyalin alınma/transfer yönteminin kaydını vurgular. Yeniden kodlama/örnekleme ses niteliğine etki edebilir; bu nedenle ASR için mono/16kHz dönüşüm gerekiyorsa orijinal korunmalı, türetilmiş kopyanın parametreleri belgelenmelidir.

## Kalite ölçümü

- WER/CER yalnızca insan tarafından doğrulanmış referans transkriptle anlamlıdır.
- Test seti aksan, lehçe, gürültü, telefon kalitesi, çoklu konuşmacı, üst üste konuşma, özel isim ve sayıları ayrı etiketlemelidir.
- Duyulmayan kısımlar tahminle tamamlanmamalı; açık placeholder kullanılmalı.
- Motor, model, quantization, sürüm ve parametreler kayıt altına alınmalıdır.
- İnsan gözden geçirme süresi ve hata sınıfları da ölçülmelidir.

## Uzmanlık sınırı

Bu modül transkripsiyon için destek sağlar. Kimlik tespiti, konuşmacı karşılaştırması, ses özgünlüğü, manipülasyon tespiti veya hukuki değerlendirme yapmaz.

## Kaynaklar

- [SWGDE Best Practices for Forensic Audio, v2.5 (09.06.2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
- [Temel ve Alt Uzmanlık Alanları ve Aranan Nitelikler — 22.01.2026 PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
