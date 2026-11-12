# Mevcut Depo İncelemesi

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Özet

İki mevcut depo da 56.12 ses transkripsiyonu ve uzman incelemesine odaklanıyor; MİHENK'in genel platform kapsamını kendiliğinden karşılamıyor.

### `forensic-transcriber` (Electron)

- README, Windows masaüstü, Electron, yerel SQLite, FFmpeg, whisper.cpp ve offline-first mimari beyan ediyor.
- Akış: vaka açma, ses dosyası kopyalama, SHA-256 ve teknik metadata, 16 kHz mono çalışma kopyası, yerel transkripsiyon, ses-metni eşleştirerek insan gözden geçirmesi ve JSON/TXT/SRT/HTML dışa aktarma.
- Otomatik ve uzman çıktısı `AUTOMATIC`, `REVIEWED`, `EDITED`, `VERIFIED` statüleriyle ayrılıyor.
- Konuşmacı kimliği, ses karşılaştırması, deepfake tespiti, hukuki yorum ve video görüntü analizi kapsam dışında.
- Güvenlik belgesi, dar preload API, context isolation, kısıtlı CSP, `shell:false`, yol temizleme ve isteğe bağlı GitHub model/güncelleme trafiğini açıklıyor.
- `docs/56-12-PRODUCT-DISCOVERY.md` (03.10.2026) eski mimaride 5,960 satır civarı JS, uzun ana/renderer dosyaları, yedek/geri yükleme yokluğu, veri tabanı bütünlük kontrolü eksikliği, transkripsiyona devam etme eksikliği ve çoklu ses akışıyla ilgili riskleri kaydetmiş.
- Repo dokümanları arasında sürüm/test sayısı tutarsızlığı var: README kısa sürüm tablosu 0.1.0/119 test; `docs/VERIFICATION.md` ve `FINAL_REPORT.md` ise 0.5.0 ve daha ileri test sayıları/işlevler anlatıyor. Bu durum belge güncelleme disiplini gerektiriyor.

### `forensic-transcriber-next` (Tauri/Rust)

- README, bağımsız yeniden yazım olduğunu; Tauri 2, Rust, React/TypeScript ve SQLite kullandığını belirtiyor.
- İş kuralları Rust domain/application katmanında; arayüz doğrudan veritabanına erişmiyor.
- `docs/PROJECT_STATE.md` ve `docs/methodology.md` hash doğrulaması, orijinal dosya-kopya ayrımı, revizyon/audit kaydı ve gerçek Whisper test akışını anlatıyor.
- README/Project State; vaka arama, yedek/geri yükleme, `.ftcase` arşiv, ikinci inceleme, dalga biçimi ve gerçek Türkçe WER/CER referans corpus'unu eksik gösteriyor.
- README'nin test sayılarında tutarsızlık var: özet bölümünde frontend 26; doğrulama komutları bölümünde 22/24 gibi farklı sayılar; proje state belgesi 24 olarak raporluyor. Commit/CI çıktısı üzerinden sabitlenmeli.
- `THIRD_PARTY_NOTICES.md` bazı lisans özetlerini “yaklaşık” olarak işaretliyor; sürüm bazında otomatik lisans taraması gerekir.

## Lisans

Her iki proje uygulama kodunu AGPL-3.0-only olarak bildiriyor. Legacy projede Electron MIT, FFmpeg LGPL, whisper.cpp MIT, model ve VAD lisansları ayrıca belirtiliyor. Next projede Rust/npm bağımlılıkları, FFmpeg ve modeller ayrı koşullara tabi. AGPL uyumu, değişikliklerin dağıtımı/ağ üzerinden sunumu, bağımlılıkların kesin lisansları ve paketleme yükümlülükleri hukukî/fikri mülkiyet incelemesi gerektirir. Kod taşınması için izin/uyum kararı olmadan kopyalama önermiyoruz.

## Karar önerisi

- Depoları birleştirmeyin.
- MİHENK araştırma belgelerini uygulama depolarından ayrı tutun.
- `forensic-transcriber-next` mimari aday/teknik pilot nesnesi olarak daha yeni ve modüler görünüyor; bu bir kalite garantisi değildir.
- Legacy repo, tarihsel özellik ve test kapsamı referansı olarak kalsın.
- Kod yeniden kullanımını ancak lisans/bağımlılık denetimi, test ve veri şeması uyumluluğu sonrası ele alın.
- İlk iş olarak iki README ve doğrulama dokümanı arasındaki sürüm/test sayılarını tek kaynağa bağlayın.

## Kaynaklar

- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
