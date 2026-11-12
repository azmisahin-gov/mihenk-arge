# Test Stratejisi

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Test katmanları

1. **Mevzuat doğrulama:** Her gereksinim güncel resmî kaynak/maddeye bağlanır; hukukçu onayı bekleyenler ayrıca işaretlenir.
2. **Alan doğrulama:** Her uzmanlık modülü için aktif bilirkişi tarafından iş akışı ve teknik sınır kontrol edilir.
3. **Birim/entegrasyon:** Domain kuralları, DB migrasyonu, dosya yolu, hash, dış süreç, çıktı biçimi.
4. **Güvenlik:** Path traversal, kötü amaçlı medya, shell injection, yedek sızıntısı, ağ trafiği, güncelleme doğrulama.
5. **Kurtarma:** Crash, power loss, DB corruption, partial output, restore.
6. **Kullanılabilirlik:** Aday, yeni bilirkişi ve deneyimli kullanıcı senaryoları.
7. **Pilot:** Sentetik veya izinli veri; görev akışı ve insan iş yükü ölçülür.

## Kabul kapısı

- 0 açık kritik güvenlik bulgusu.
- Yedek/geri yükleme acceptance test geçer.
- Orijinal materyal değişmezliği test edilir.
- Resmî teslimi yanlış gösteren hiçbir otomatik durum yoktur.
- Uzman görüşü ile AI/ASR çıktısı ayrı tutulur.
- Tüm hata senaryoları kullanıcıya açıklanır.

Test sayısı başlı başına kalite kanıtı değildir. Testlerin hangi gerçek riski kapsadığı kaydedilmelidir.

## Kaynaklar

- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
