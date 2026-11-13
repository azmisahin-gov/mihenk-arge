# Yerel Görev Kasası — Şifreleme ve Kurtarma Tasarımı

> **Durum:** MİMARİ ÖN TASARIM — UYGULAMA VE BAĞIMSIZ GÜVENLİK İNCELEMESİ BEKLİYOR  
> **Tarih:** 13 Kasım 2026  
> **Kapsam:** 56.12 prototipinden bağımsız olarak MİHENK görev verilerinin çevrimdışı ve şifreli saklanması için ilk teknik tasarım. Bu belge güvenlik sertifikası veya hukukî görüş değildir.

## 1. Neden bu kapı önce geliyor?

Mevcut masaüstü prototipinde kaynak ses ve transkript yalnızca uygulama oturum belleğinde tutulur. Otomatik kayıt eklemek, veriyi açık biçimde diske yazarsa kabul edilebilir bir çözüm değildir. Gerçek görev materyaliyle deneme başlamadan önce kaynak dosyalar, transkript, görev profili, ara çıktılar, anahtarlar ve yedekler yerel ortamda korunmalı; uygulama kesintisinde tutarlı biçimde geri açılabilmelidir.

**Temel ilke:** Bulut veya uzak ASR yok. Kasa, veriyi cihazda şifreli tutar; resmî UYAP/e-imza işlemlerini devralmaz.

## 2. Varlık ve tehdit sınırı

Korunacak veriler: görev belgesi ve profili, kaynak ses/dosya, dosya envanteri, özgün dosya özeti, ASR ham çıktısı, uzman düzeltmeleri, zaman kodları, rapor taslakları, işlem geçmişi, kasa anahtarı ve yedekler.

İlk kapsamda savunulacak tehditler:
- Cihazın kapalı veya kullanıcı oturumunun kilitli olduğu sırada dosya sistemine yetkisiz erişim.
- Kaynak dosya veya şifreli blokların değiştirilmesi, silinmesi, sırasının bozulması ya da sonunun kesilmesi.
- Uygulama kapanması, güç kaybı, disk dolması veya yarım içe aktarma nedeniyle işin bozulması.
- Bir görevdeki dosyanın veya metnin başka göreve karışması.
- Yedek kaybı, yanlış parola ve başka cihaza geri yükleme.

Kasanın açık olduğu ve kullanıcının oturumu/cihazı kötü amaçlı yazılımla ele geçirildiği durumlar bu mekanizmalarla bütünüyle çözülemez. Tam disk şifrelemesi, işletim sistemi güncellemeleri, kullanıcı hesabı güvenliği ve fiziksel erişim kontrolleri ayrıca gerekir.

## 3. Önerilen veri düzeni

İlk dikey dilim için az sayıda, açıkça sürümlenen yerel bileşen önerilir:

| Bileşen | İçerik | Diskteki durum |
|---|---|---|
| Kasa anahtar zarfı | Argon2id parametreleri, salt, nonce ve sarılmış rastgele kasa anahtarı | Şifreli |
| Görev kataloğu | Görev kimlikleri, profiller, dosya ilişkileri ve durumlar | AEAD ile şifreli metaveri |
| Görev metaverisi | Transkript, segmentler, ham/uzman sürümleri, kaynak izleri | AEAD ile şifreli |
| Materyal kasası | Orijinal ses ve içe alınan diğer dosyalar | Blok bazında şifreli |
| Yedek paketi | Katalog, görev metaverisi, şifreli materyal, biçim sürümleri ve bütünlük manifesti | Baştan sona şifreli |

İlk pilotta veritabanı zorunlu tutulmaz; küçük ve sürümlenmiş bir şifreli katalog/metaveri biçimi yeterli olup olmadığı ölçülür. Katalog büyürse SQLCipher gibi şifreli veritabanı ayrı lisans, paketleme ve Windows/Linux testinden sonra değerlendirilir. Düz SQLite, plaintext WAL/SHM veya tarayıcı localStorage kasa yerine kullanılmaz.

Dosya sistemindeki materyal adları rastgele kimliklerden oluşur. Gerçek dosya adı, dosya yolu, görev adı veya kişi adı şifrelenmemiş dosya/dizin adlarına yazılmaz.

## 4. Anahtar hiyerarşisi

Ön tasarım:

1. Kasa oluşturulurken işletim sistemi CSPRNG kaynağından 256 bit rastgele kasa anahtarı üretilir.
2. Kullanıcının kasa parolası, her kasa için benzersiz salt ve sürümlenmiş parametrelerle Argon2id kullanılarak anahtar sarmalama anahtarına dönüştürülür.
3. Rastgele kasa anahtarı XChaCha20-Poly1305 AEAD ile sarılır. Yanlış parola, zarf doğrulaması başarısız olduğunda açılmaz; ayrı ve zayıf bir parola özeti tutulması gerekmez.
4. Her materyal için kasa anahtarından farklı bir dosya anahtarı, dosyanın rastgele kimliği üzerinden HKDF ile türetilir veya kasa anahtarıyla sarılmış rastgele dosya anahtarı kullanılır. Alan ayrımı ve sürüm bilgisi zorunludur.
5. Açık anahtar malzemesi yalnızca ihtiyaç varken bellekte tutulur; kilitleme/çıkışta sıfırlama girişimi yapılır. JavaScript bellek kopyalarının tümünü güvenilir biçimde sıfırladığımız iddia edilmez.
6. Kurtarma anahtarı/parolası, ana kasa parolasından bağımsız tasarlanır. Kurtarma yöntemi kullanıcıya bir kez gösterilir; kasayla ve aynı yedek ortamıyla birlikte saklanmamalıdır.

Argon2id parametreleri sabit tahmin edilmez; desteklenen en düşük donanımda ölçülür ve zarf içinde sürümlenerek kaydedilir. Parametreler açılışta güvenli sınırlarla doğrulanır. Kasa parolasını veya kurtarma bilgisini kaybetmek veri kaybına yol açabilir; ürün akışı bu riski gizleyemez.

## 5. Ses dosyasında rastgele erişim ve bütünlük

Ses oynatıcı ileri/geri sarma yapabildiği için bütün dosyayı her seferinde çözmek veya diske plaintext geçici dosya bırakmak tercih edilmez. İlk prototipte araştırılacak dosya biçimi:

- Ses, örneğin 1 MiB gibi ölçülebilir sabit boyutlu bloklara ayrılır.
- Her blok, XChaCha20-Poly1305 AEAD ile bağımsız şifrelenir; her blok için kriptografik olarak rastgele 192 bit nonce kullanılır.
- AAD; biçim sürümü, kasa kimliği, görev kimliği, materyal kimliği, blok sıra numarası ve açık blok uzunluğunu bağlar. Yanlış sıradaki veya başka dosyaya ait blok açılmaz.
- Şifreli katalogda orijinal byte boyutu, blok sayısı, son blok uzunluğu ve içe alma sırasında hesaplanan tam kaynak SHA-256 değeri saklanır. Bu kayıt da AEAD korumalıdır.
- Herhangi bir aralık isteğinde yalnızca ilgili bloklar diskteki şifreli dosyadan okunur, bellekte açılır ve istenen byte aralığı döndürülür.
- Tauri özel URI protokolü HTTP Range / 206 yanıtlarını uygular; böylece ses oynatıcı seek yapabilir ve plaintext geçici dosyaya ihtiyaç azalır.

Bu bloklu kapsayıcı MİHENK'e özel bir biçim olacaktır. Algoritma kullanımından ayrı olarak dosya başlığı, indeks, offset hesabı, blok sınırları, kesilme, sıra değiştirme, yanlış dosyaya bağlama ve bozuk blok davranışı test edilmeli; biçim sürümü ve migrasyon kuralı yayımdan önce sabitlenmelidir.

## 6. Kaynak dosya içe alma ve otomatik kayıt

- Orijinal kaynak dosya kullanıcı konumunda değiştirilmez; MİHENK yalnızca şifreli çalışma kopyası oluşturur.
- İçe alma sırasında dosya akışlı okunur; plaintext hash hesaplanırken şifreli bloklar geçici .part dosyasına yazılır.
- Tüm bloklar ve metaveri doğrulanmadan görev kataloğuna tamamlandı kaydı eklenmez.
- Geçici dosya tamamlandıktan sonra flush/sync_all ve atomik yeniden adlandırma yapılır. İşlem ortasında hata olursa yarım kayıt görünür hâle gelmez.
- Transkript değişikliği kısa bir debounce sonrasında şifreli metaveriye yazılır. Kapanışta son yazma tamamlanır; ani güç kaybına karşı journal/transaction davranışı test edilir.
- Açık oturum kilitlendiğinde oynatma durur, geçici kaynak erişim belirteçleri iptal edilir ve kasa anahtarı bellekten çıkarılır.

## 7. Yedekleme ve başka cihaza taşıma

Yedek, şifreli materyal + şifreli katalog + sürüm bilgisi + bütünlük manifestini tek tutarlı paket olarak içerir. Yedekleme sırasında dosyalar decrypt edilmez. Restore önce geçici bir klasöre yapılır; bütünlük ve şema doğrulaması tamamlanmadan mevcut kasanın üzerine yazılmaz. Başka cihaz testi zorunludur.

Yedek anahtarının yedek paketinden ayrı tutulması gerekir. Bulut senkronizasyonu veya GitHub'a vaka verisi yükleme ilk kapsamda yoktur. Kullanıcıya yedek oluşturma, doğrulama tarihi ve son başarılı geri yükleme testi açıkça gösterilir.

## 8. Değerlendirilen kütüphaneler ve sınırlar

| Aday | Ne için değerlendirildi | Ön bulgu | Karar |
|---|---|---|---|
| RustCrypto chacha20poly1305 0.11.x | XChaCha20-Poly1305 AEAD | 0.11.0 sürümü XChaCha desteği, NCC Group güvenlik denetimi ve Apache-2.0/MIT lisansı bildiriyor | Blok başına AEAD için ilk PoC adayı; kapsayıcı yine de güvenlik incelemesi ister |
| RustCrypto argon2 0.6.x | Paroladan anahtar türetme | Argon2id destekliyor; anahtar türetme API'si ve Apache-2.0/MIT lisansı mevcut | Anahtar zarfı için ilk PoC adayı; parametre benchmarkı şart |
| Tauri Stronghold 2.4.x | Gizli anahtar saklama | Tauri 2 eklentisi; Windows/Linux/macOS desteği ve Argon2 ile parola tabanlı başlatma dokümantasyonu var | Kullanım kolaylığı ve kurtarma akışı için araştırılacak; veri kasası yerine anahtar saklama rolü ayrı test edilmeli |
| keyring 4.x | İşletim sistemi kimlik bilgisi deposu | Windows Credential Manager ve Linux Secret Service arka uçları sunuyor | İsteğe bağlı cihaz içi kilit açma kolaylığı olabilir; tek kurtarma kaynağı yapılmaz |
| age 0.12.x | Şifreli dosya ve akış | Streaming API var; ancak crate belgeleri 1.0 öncesi sürümleri beta/test amaçlı olarak uyarıyor | İlk pilotun temel biçimi olarak seçilmedi |
| enc_file 0.6.x | Büyük dosya şifreleme | Akışlı şifreleme sunduğunu bildiriyor; kendi güvenlik notu üçüncü taraf denetimi olmadığını belirtiyor | Güvenlik incelemesi olmadan kullanılmayacak |
| orion 0.18.x | Akışlı AEAD | XChaCha tabanlı streaming API var; proje üçüncü taraf güvenlik denetimi bulunmadığını belirtiyor | İlk üretim adayı değil |
| SQLCipher / rusqlite | Şifreli yapılandırılmış veri | SQLCipher entegrasyonu mevcut; paketleme ek crypto bağımlılığı gerektirir | Katalog ihtiyacı büyürse paket/CI/lisans incelemesiyle ayrıca değerlendirilecek |

Bu tablo kütüphanelerin proje içinde kullanılmaya başlandığı anlamına gelmez. Sürüm sabitleme, transitif bağımlılık/SBOM, lisans, Windows/Linux derlemesi, hata/bozulma testleri ve bağımsız güvenlik incelemesi olmadan bağımlılık eklenmeyecektir.

## 9. Zorunlu güvenlik ve kurtarma testleri

1. Doğru parola ile açma; yanlış parola ile hiçbir veriyi açmama.
2. Anahtar zarfı, katalog ve materyal dosyasında tek byte değişikliğiyle açma hatası.
3. Şifreli blok silme, kopyalama, sıra değiştirme, yeniden oynatma ve son blok kesilmesi.
4. Başka görev/kasa/materyal bağlamında blok açma girişiminin reddi.
5. İçe alma ortasında uygulamayı kapatma, disk dolması, izin kaybı ve yarım dosya.
6. Transkript düzenlerken ani sonlandırma; yeniden açılışta son tutarlı sürüme dönüş.
7. Büyük dosya ve çoklu kayıt altında bellek üst sınırı, CPU ve disk throughput ölçümü.
8. Range isteklerinin blok sınırı öncesi/sonrası, dosya sonu ve geçersiz aralık testleri; ses oynatıcıda ileri/geri sarma.
9. Şifreli kasa yedeğini yeni Windows ve Pardus/Linux profiline geri yükleme.
10. Vault klasöründe açık ses/transkript/parola/anahtar kalmadığının test edilmesi; log ve hata raporunda hassas içerik bulunmaması.
11. Yedek manifesti, hash, şema sürümü ve geri yükleme sonrasında kaynak hash eşleşmesi.
12. Uygulama kilitleme/çıkışında oynatma ve kaynak erişiminin iptali.

## 10. Gerçek materyale geçiş kapısı

Bu tasarımın yazılmış olması gerçek vaka kullanımını açmaz. En azından aşağıdakiler tamamlanmalıdır:

- Şifreli kasa ve bloklu dosya biçiminin uygulanması ve testleri.
- Yanlış parola, bozuk veri, yarım işlem ve restore testlerinin Windows/Pardus üzerinde geçmesi.
- Şifreli yedek başka bir cihaza taşınarak açılması.
- Kısa bağımsız kriptografi/kod incelemesi ve tehdit modelinin güncellenmesi.
- KVKK/hukuk incelemesi, gerçek uzmanla kontrollü kabul testi ve kullanıcı dokümantasyonu.
- CI'da sentetik veri dışında vaka verisi bulunmadığının doğrulanması.

**Kilit kural:** Şifreli kalıcı kasa ve doğrulanmış restore tamamlanana kadar mevcut prototipte yalnızca sentetik veya kullanım izni bulunan test sesleri kullanılabilir.

## Kaynaklar

- [Tauri Stronghold 2.x](https://tauri.app/plugin/stronghold/) — gizli anahtar deposu, platform desteği ve parola tabanlı kurulum.
- [RustCrypto chacha20poly1305 0.11.0](https://docs.rs/chacha20poly1305/0.11.0/chacha20poly1305/) — XChaCha20-Poly1305, NCC Group denetimi, Apache-2.0/MIT.
- [RustCrypto Argon2 0.6.0](https://docs.rs/argon2/0.6.0/argon2/) — Argon2id ve anahtar türetme.
- [keyring 4.2.0](https://docs.rs/keyring/4.2.0/keyring/v1/) — Windows Credential Manager ve Linux Secret Service.
- [age 0.12.1](https://docs.rs/age/0.12.1/age/) — streaming ve sürüm öncesi 1.0 beta uyarısı.
- [enc_file 0.6.6](https://docs.rs/enc_file/0.6.6/enc_file/) — streaming ve kendi güvenlik denetimi uyarısı.
- [Orion 0.18.1](https://docs.rs/orion/0.18.1/orion/aead/streaming/) — akışlı AEAD; proje üçüncü taraf denetimi olmadığını bildiriyor.
- [rusqlite / SQLCipher entegrasyonu](https://github.com/rusqlite/rusqlite) — özellikler ve lisans bilgisi.
- [Tauri özel URI protokolü](https://docs.rs/tauri/latest/tauri/struct.Builder.html) — özel kaynak protokolü; HTTP Range davranışı için Tauri asset protocol örneği de test edilmelidir.
