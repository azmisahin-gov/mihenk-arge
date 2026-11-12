# Veri Koruma

> **Durum:** HUKUKİ İNCELEME BEKLİYOR  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Veri risk profili

Bilirkişilik materyalinde kimlik, iletişim, sağlık, biyometrik/ genetik, ceza mahkûmiyeti ve güvenlik tedbirleri, siyasi/dini görüş veya başka hassas bilgiler bulunabilir. Bir ses kaydı tek başına otomatik olarak biyometrik veri değildir; kişiyi benzersiz tanımlama amacıyla teknik işleme yapılması ayrı değerlendirme gerektirir. Dosya içeriğine göre özel nitelikli veri riski değişir.

## İlk ürün tasarımı

- Veri minimizasyonu: yalnızca görevin gerektirdiği asgari veriyi tut.
- Yerel depolama: cloud upload kapalı.
- Erişim: işletim sistemi hesabı ve uygulama seviyesinde erişim kontrolü tasarla.
- Şifreleme: cihaz tam disk şifrelemesi ile uygulama/veri tabanı şifreleme ihtiyacını ayrı değerlendir; anahtar yönetimi test edilmeli.
- Paylaşım: e-posta/harici bulut/ortak link ile dosya paylaşımını varsayılan kapat.
- Yedek: şifreli ve kullanıcı kontrollü, yedek içindeki dosyalar da retention'a tabi.
- Telemetri: vaka içeriği, dosya adı, kişi adı, dosya id ve hata dump'ı dışarı çıkmamalı.
- Silme: aktif veri, geçici dosya, cache ve yedekler için ayrı silme politikası.

## Hukuki doğrulama

KVKK'nın 2024 özel nitelikli kişisel veri rehberi, 12.03.2024 tarihli 7499 sayılı Kanun değişikliğinden sonra m.6 işleme şartlarının güncellendiğini belirtir. Ürünün somut veri sorumlusu/işleyen rolleri, yargısal faaliyet istisnaları ve işleme sebebi için hukukçu değerlendirmesi gereklidir.

## Kaynaklar

- [KVKK — Özel Nitelikli Kişisel Verilerin İşlenmesine İlişkin Rehber](https://www.kvkk.gov.tr/Icerik/8184/Ozel-Nitelikli-Kisisel-Verilerin-Islenmesine-Iliskin-Rehber)
- [6754 sayılı Bilirkişilik Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/104136)
