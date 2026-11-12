# Risk Kaydı

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

| ID | Risk | Olasılık / etki | Önlem | Durum |
|---|---|---|---|---|
| R-01 | Ürün ihtiyacı varsayımdan ibaret | Yüksek / yüksek | Uygulayıcı görüşmesi, problem kanıtı | Açık |
| R-02 | UYAP işlevlerini yanlış varsaymak | Orta / yüksek | Portal içi yetkili kullanıcı doğrulaması | Açık |
| R-03 | UYAP entegrasyonuna izinsiz erişim | Orta / kritik | API/yazılı izin yoksa entegrasyon yok | Kapsam dışı |
| R-04 | Bilirkişi kapsamı dışına taşma | Orta / kritik | Uzmanlık kodu ve workflow guardrails | Açık |
| R-05 | Delil materyalinin değişmesi/kaybolması | Orta / kritik | Orijinal kopya, hash re-verify, backup/restore | Açık |
| R-06 | Gizli/özel nitelikli veri sızıntısı | Orta / kritik | Local-first, encryption, data minimization | Açık |
| R-07 | ASR yanlış transkript ve aşırı güven | Yüksek / yüksek | İnsan doğrulaması, belirsiz bölüm, quality corpus | Açık |
| R-08 | AGPL/third-party lisans uygunsuzluğu | Orta / yüksek | SBOM ve hukukî lisans inceleme | Açık |
| R-09 | Güncelleme tedarik zinciri saldırısı | Orta / yüksek | İmzalı yayın, provenance, checksum/signature | Açık |
| R-10 | Çoklu cihaz/senkronizasyon veri çakışması | Orta / yüksek | İlk sürümde sync yok | Önlem önerildi |
| R-11 | Güncel başvuru listesi takvimi yanlış yorumlanır | Orta / orta | Planlanan ilan/yayımlanan liste ayrımı | Açık |
| R-12 | UI testleri saha koşullarını temsil etmez | Yüksek / yüksek | Target-machine + human corpus validation | Açık |

## Risk yönetimi kuralı

Kritik riskler kabul edilmeden gerçek vaka verisiyle dağıtım yapılmaz. Risk sahibi, hedef tarih ve kapatma kanıtı her satıra eklenmelidir.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [KVKK — Özel Nitelikli Kişisel Verilerin İşlenmesine İlişkin Rehber](https://www.kvkk.gov.tr/Icerik/8184/Ozel-Nitelikli-Kisisel-Verilerin-Islenmesine-Iliskin-Rehber)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
