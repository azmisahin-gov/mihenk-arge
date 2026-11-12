# Veri Koruma

> **Durum:** HUKUKİ İNCELEME BEKLİYOR  
> **Güncelleme:** 13 Kasım 2026

## Veri risk profili

Bilirkişilik materyalinde kimlik, iletişim, sağlık, biyometrik/genetik, ceza mahkûmiyeti ve güvenlik tedbirleri, siyasi/dini görüş veya başka hassas bilgiler bulunabilir. Ses kaydı tek başına otomatik olarak biyometrik veri değildir; kişiyi benzersiz tanımlama amacıyla teknik işleme yapılması ayrı değerlendirme gerektirir. Dosya içeriğine göre özel nitelikli veri riski değişir.

## GitHub görünürlüğü

MİHENK'in araştırma deposu `mihenk-arge` ve boş uygulama deposu `mihenk` public olarak doğrulanmıştır. Public depolarda:
- Vaka materyali, ses/görüntü, rapor, dosya numarası, taraf/uzman kimliği veya UYAP ekran görüntüsü bulunmaz.
- Gerçek görüşme notları yerine yalnızca yeniden kimliklendirme riski azaltılmış tematik bulgular yayımlanır.
- Sertifika, imza anahtarı, token, parola, üretim ayarı ve gizli log commit edilmez.
- Katılımcı kodu veya uzmanlık/deneyim kombinasyonu tek başına anonimlik sayılmaz.

Public bir GitHub deposu, gizli veya kişisel veriler için güvenli bir özel çalışma alanı değildir. Commit geçmişi de dikkate alınmalıdır; dosyayı sonradan silmek geçmişteki yayını otomatik olarak ortadan kaldırmaz.

## İlk ürün tasarım ilkeleri

- Veri minimizasyonu: yalnızca görevin gerektirdiği asgari veriyi tut.
- Cihazda çalışma: çevrimdışı/yerel seçenek araştır; ancak yerel depolama kendi başına güvenlik garantisi değildir.
- Erişim: işletim sistemi hesabı ve uygulama seviyesinde erişim kontrolü tasarla.
- Şifreleme: tam disk şifrelemesi, uygulama/veri tabanı şifreleme ve anahtar yönetimini ayrı değerlendir.
- Paylaşım: e-posta/harici bulut/ortak link ile dosya paylaşımını varsayılan kapalı tutmayı değerlendir.
- Yedek: şifreli ve kullanıcı kontrollü; yedek içindeki dosyalar da saklama/silme politikasına tabi.
- Telemetri: vaka içeriği, dosya adı, kişi adı, dosya id ve hata dump'ı dışarı çıkmamalı.
- Silme: aktif veri, geçici dosya, cache ve yedekler için ayrı politika tanımla.
- Haricî yapay zekâ/işleme servisi: dosya göndermeden önce yetki, hukuki sebep, veri işleyen, aktarım ülkesi ve güvenlik koşullarını doğrula.

## Güncel hukuki araştırma notu

KVKK'nın kişisel verilerin yurt dışına aktarılmasına ilişkin rehberi, 6698 sayılı Kanun'un 9. maddesi kapsamındaki aktarım şartlarının değerlendirilmesi için başvuru kaynağıdır. 2026 tarihli Kurul ilke kararı, aydınlatma metni ile açık rıza metninin farklı kavramlar olduğunu ve gerektiğinde ayrı düzenlenmesini vurgular. Bu kaynaklar MİHENK'in somut veri sorumlusu/veri işleyen rolünü veya yargısal faaliyet istisnasının bu projeye uygulanışını tek başına belirlemez; hukukçu incelemesi gerekir.

## Hukuki doğrulama

Somut veri sorumlusu/işleyen rolleri, yargısal faaliyet istisnaları, işleme sebebi, saklama süresi, veri ihlali prosedürü ve yurt dışı aktarımı için uzman hukukçu değerlendirmesi gereklidir.

## Kaynaklar

- [KVKK — Kişisel Verilerin Yurt Dışına Aktarılması Rehberi](https://www.kvkk.gov.tr/Icerik/8143/Kisisel-Verilerin-Yurt-Disina-Aktarilmasi-Rehberi)
- [KVKK — 18.02.2026 tarihli 2026/347 sayılı İlke Kararı duyurusu](https://www.kvkk.gov.tr/Icerik/8710/veri-sorumlulari-tarafindan-acik-riza-ve-aydinlatma-metinlerinin-ayri-ayri-duzenlenmesi-gerektigi-hakkinda-kisisel-verileri-koruma-kurulunun-18-02-2026-tarihli-ve-2026-347-sayili-ilke-kararina-iliskin-kamuoyu-duyurusu)
- [KVKK — Özel Nitelikli Kişisel Verilerin İşlenmesine İlişkin Rehber](https://www.kvkk.gov.tr/Icerik/8184/Ozel-Nitelikli-Kisisel-Verilerin-Islenmesine-Iliskin-Rehber)
- [6754 sayılı Bilirkişilik Kanunu](https://mevzuat.adalet.gov.tr/mevzuat/104136)
