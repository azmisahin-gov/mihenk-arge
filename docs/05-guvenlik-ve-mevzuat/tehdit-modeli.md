# Tehdit Modeli

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Varlıklar

Görev notu, delil/materyal dosyaları, rapor taslakları, otomatik transcript, uzman düzeltmesi, kullanıcı kimlik verileri, şifreleme anahtarı, yedekler, loglar, uygulama güncellemesi ve bağımlılık paketleri.

## Tehditler

| Tehdit | Etki | Kontrol önerisi |
|---|---|---|
| Bilgisayar çalınması | Dosya gizliliği ihlali | Tam disk şifreleme, ekran kilidi, anahtar koruması |
| Yanlış dosyada çalışma | Gizlilik/rapor hatası | Belirgin görev başlığı, ikinci görev teyidi, materyal kimliği |
| Kötü amaçlı medya | Kod yürütme/çökme | Sandbox/child process sınırı, güvenli decode, kaynak sınırı |
| Yol traversal | Dizin dışına yazma | Ad temizleme, path canonicalization |
| Güncelleme ele geçirilmesi | Kod/anahtar saldırısı | İmzalı güncelleme, release provenance, SBOM |
| Yedek sızıntısı | Toplu dosya ifşası | Şifreli backup, ayrı anahtar, erişim kısıtı |
| DB bozulması | Veri kaybı | Transaction, bütünlük kontrolü, yedek/restore |
| Log değişikliği | Yanlış güven/iz kaybı | Append-only yaklaşım; logun resmî delil olmadığı açıklaması |
| Senkronizasyon çakışması | Yanlış sürüm/yanlış kişi | MVP'de sync yok; ileride conflict resolution |
| Gizli ağ trafiği | Veri sızıntısı | Ağ erişim envanteri, test ve CI policy |

## Ürün güvenlik kapısı

Gerçek dosya ile kullanım başlamadan önce tehdit modeli, veri sınıflandırması, güncelleme imza doğrulaması, şifreleme/anahtar yönetimi, restore testi ve güvenlik testi tamamlanmalıdır.

## Kaynaklar

- [KVKK — Özel Nitelikli Kişisel Verilerin İşlenmesine İlişkin Rehber](https://www.kvkk.gov.tr/Icerik/8184/Ozel-Nitelikli-Kisisel-Verilerin-Islenmesine-Iliskin-Rehber)
- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
