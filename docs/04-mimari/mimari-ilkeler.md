# Mimari İlkeler

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Önerilen ilke seti

1. **Önce yerel çalışma:** Yargı dosyalarının gizliliği ve ağsız çalışma ihtimali nedeniyle yerel-first seçenek ilk prototipte öncelikli değerlendirilmeli.
2. **Modüler monolit:** Ölçek ve çok kiracılık kanıtlanmadığı için mikro hizmet/dağıtık mimari seçilmemeli.
3. **Katman ayrımı:** Domain ve uygulama kuralları arayüz/altyapıdan bağımsız tutulmalı.
4. **Uzmanlık eklentileri:** Modül kendi veri ve yöntem modelini taşımalı; ortak çekirdeğe zorla sığdırılmamalı.
5. **Güvenli dış işlem:** Harici araçlar argument array ile, shell kullanılmadan çalıştırılmalı.
6. **Veri tabanı:** Yerel tek kullanıcılı pilot için SQLite düşünülebilir; eşzamanlı çok kullanıcı ihtiyacı kanıtlanırsa PostgreSQL/servis değerlendirilmeli.
7. **Güncelleme güveni:** Kod imzalama, paket imza doğrulaması ve anahtar yönetimi release şartı olmalı.
8. **Kurtarma:** Yedekleme, restore ve hata sonrası toparlama MVP güvenilirliğinin parçası olmalı.

## Teknoloji karşılaştırması

| Seçenek | Güçlü yön | Sınırlama | Şimdiki öneri |
|---|---|---|---|
| Electron | Mevcut klasik uygulamada olgun JS araçları; hızlı prototipleme | Bellek, büyük tek JS dosyaları/IPC sınırı iyi yönetilmezse karmaşıklık | Yeni ortak ürün için varsayılan değil |
| Tauri + Rust + React | Yerel çekirdek, UI ayrımı, kontrollü IPC, mevcut Next deneyimi | Rust öğrenme/bakım ve Windows/WebView paketleme gereksinimi | 56.12 pilot teknik aday, nihai karar değil |
| C#/.NET Windows | Windows kurumsal desteği ve yerel entegrasyon | Çoklu platform hedefinde sınırlı olabilir | Gerçek kullanıcı ortamı sorulmalı |
| Web uygulaması | Dağıtım kolaylığı/merkezi güncelleme | Hassas dosyaların sunucuya gitmesi, offline sınırlaması | İlk pilot için tercih edilmez |
| Bulut | Ekip/erişim kolaylığı | Veri yerleşimi, sır, erişim, aktarım ve hukuk riski | Yazılı onay ve ihtiyaç kanıtı olmadan kapsam dışı |

Mevcut `forensic-transcriber-next` tasarımı Tauri + Rust + React + SQLite katmanlı bir örnek sunuyor; bu bir nihai karar gerekçesi değildir.

## Kaynaklar

- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
- [KVKK — Özel Nitelikli Kişisel Verilerin İşlenmesine İlişkin Rehber](https://www.kvkk.gov.tr/Icerik/8184/Ozel-Nitelikli-Kisisel-Verilerin-Islenmesine-Iliskin-Rehber)
- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
