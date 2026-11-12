# İşlevsel Olmayan Gereksinimler

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

| Alan | Gereksinim önerisi | Kabul testi |
|---|---|---|
| Gizlilik | Veri varsayılan olarak yerel kalmalı; ağ çağrısı envanteri yayın öncesi test edilmeli | Ağ trafiği analizi ve bağımlılık kontrolü |
| Bütünlük | Orijinal dosyanın içeriği değişmemeli; materyal yeniden hashlenebilmeli | Import sonrası ve saklama süresince hash karşılaştırma |
| Güvenilirlik | Yarım yazım/çökme sonrası veri bozulması görünür ve kurtarılabilir olmalı | Kesinti, güç kaybı ve veritabanı bozulma testleri |
| Güvenlik | Az yetki, güvenli süreç başlatma, dosya adı/yol doğrulama | Tehdit modeline dayalı red-team |
| Kullanılabilirlik | Türkçe, görev odaklı ve erişilebilir arayüz | Görev tamamlamalı kullanılabilirlik testi |
| Taşınabilirlik | Önce Windows hedefi; diğer sistemler kullanıcı ve kurumsal şartlarla doğrulanmalı | Destek matrisi ve temiz makine testleri |
| Performans | Uzun dosya/çok materyal durumunda UI kilitlenmemeli | Ölçek fixture'larıyla benchmark |
| Bakım | Sürümler, modeller, bağımlılıklar ve migrasyonlar pinlenmeli | SBOM/lisans raporu ve release gate |
| Denetlenebilirlik | Otomatik ve insan eylemleri ayırt edilebilir olmalı | History audit testleri |
| Yedekleme | Kullanıcı geri yüklemeyi uygulama içinden doğrulayabilmeli | Restore acceptance senaryosu |

Bunlar ürün kalitesi hedefleridir; mevzuatın her maddesiyle doğrudan eşdeğer sayılmaz.

## Kaynaklar

- [KVKK — Özel Nitelikli Kişisel Verilerin İşlenmesine İlişkin Rehber](https://www.kvkk.gov.tr/Icerik/8184/Ozel-Nitelikli-Kisisel-Verilerin-Islenmesine-Iliskin-Rehber)
- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
