# Açık Kaynak Belge, Ofis ve PDF Araçları Araştırması

> **Durum:** İlk karşılaştırma — entegrasyon/teknoloji kararı değildir  
> **Araştırma tarihi:** 13 Kasım 2026  
> **Öncelik:** Açık kaynak ve yerel çalışma; lisans, güvenlik ve UYAP uyumluluğu doğrulanmadan bileşen seçilmez.

## 1. Araştırmanın amacı

MİHENK'in rapor, tutanak, teknik ek, tablo ve PDF işlerini tek uygulamanın içinden yürütebilmesi hedeflenir. Kullanıcının ayrıca Word, ayrı PDF dönüştürücü, OCR programı veya her uzmanlık için farklı masaüstü araçları kurup aralarında dosya taşıması istenmez.

Bununla birlikte MİHENK'in bütün belge düzenleme motorlarını kendisinin sıfırdan yazması gerekmez. Lisansı ve güvenliği uygun açık kaynak motorlar, MİHENK'in arayüzü ve iş akışı içinde çalışan gömülü/bağlı bileşenler olarak değerlendirilebilir. Son kullanıcı tek uygulamayla çalışır; teknik olarak bazı motorlar arka planda ayrı işçi süreçleri olabilir. Bu, kullanıcıdan bağımsız üçüncü taraf uygulama kurmasını veya yönetmesini istemekle aynı şey değildir.

## 2. UYAP'ın mevcut resmî belge akışı

UYAP Doküman Editörü Bakanlık tarafından geliştirilen ve UYAP ile entegre çalışan kelime işlemci olarak tanımlanır. Resmî yardımında:
- Editörün belgeleri varsayılan olarak `.udf` biçiminde kaydettiği,
- `.usf`, `.doc`, `.pdf`, `.odt`, `.rtf`, `.tif` ve `.jpg` gibi başka biçimlere farklı kaydetme yapılabildiği,
- Birden fazla UDF belgesinin topluca DOC, ODT, PDF ve RTF'ye çevrilebildiği,
- İmzalı belge değiştirilirse imzanın kaybolabileceği ve tekrar imzalanması gerektiği

açıklanır.

UYAP Editör indirme sayfasında Windows, macOS ve Pardus/Debian tabanlı sistemler için paketler; ayrıca Android ve iOS uygulamaları listelenir. Bu araştırma sırasında sayfada masaüstü sürümü olarak v5.4.17 görünüyordu. Sürüm dağıtım öncesi yeniden kontrol edilmelidir.

31.05.2026 tarihli Bakanlık duyurusuna göre ArkSigner üzerinden UYAP'a giriş yöntemi 01.06.2026 itibarıyla sona ermiş; elektronik imza ile girişte e-Devlet veya Adalet e-İmza Uygulaması belirtilmiştir. UYAP Doküman Editörü'nün de güncel sürüme yükseltilmesi istenmiştir.

**Ürün sonucu:** UDF, MİHENK'in kendi rapor veri modeli değildir; UYAP'a teslim sürecinde önemli olan resmî belge biçimidir. MİHENK'in DOCX/ODT/PDF gibi biçimleri de desteklemesi gerekir, ancak hangi formatın hangi evrak türünde kabul edildiği portalda ayrıca test edilmelidir.

## 3. Ofis ve kelime işlemci seçenekleri

| Ürün | Lisans / dağıtım | Güçlü yön | Sınırlama ve MİHENK açısından değerlendirme |
|---|---|---|---|
| **LibreOffice Writer + UNO** | Ana proje MPL 2.0; kurulumda farklı bileşenlerin ek lisansları da vardır | Yerel/çevrimdışı masaüstü ofis paketi; ODT, DOCX, DOC, RTF ve PDF iş akışları; UNO SDK ile Java/Python/C++ üzerinden otomasyon ve bileşen geliştirme örnekleri | Tam editör arayüzünü MİHENK'e gömmek basit bir kontrol eklemek kadar kolay değildir; UNO köprüsü/arka plan motoru ve süreç yönetimi gerekir. UDF'yi doğal olarak üretmez. **Yerel çalışma için ilk teknik PoC adayı.** |
| **ONLYOFFICE Desktop Editors / Docs** | Community bileşenleri AGPLv3; Developer ve Enterprise ticari seçenekleri bulunur | Desktop Editors yerel belgeleri internet olmadan açıp düzenleyebilir; DOCX uyumluluğuna odaklıdır; editör uygulamaya entegre edilebilir | Community sürümünü MİHENK içinde markalı biçimde sunma ve dağıtma koşulları dikkatle incelenmelidir. Üretici, markasız/white-label ve uygulama içine entegrasyon için Developer/ticari lisans yolunu gösterir. AGPL ağda sunulan türev işlere kaynak açıklama yükümlülüğü doğurabilir. **Lisans uyumu netleşmeden seçilmez.** |
| **Collabora Online / CODE** | Kodun büyük kısmı MPLv2 ve LibreOffice tabanlıdır; destekli sürüm ticari abonelikle sunulur | WOPI üzerinden kendi web uygulamasına gömülebilen, kurum içinde barındırılabilen tarayıcı tabanlı ofis düzenleyicisi; DOCX/ODT/RTF/PDF dahil geniş format desteği | WOPI sunucusu, kimlik doğrulama ve belge depolama entegrasyonu gerekir. CODE geliştirme sürümü test/ev kullanımı içindir ve üretim ortamı için önerilmez. **MİHENK web tabanlı kurulursa alternatif PoC.** |
| **Apache OpenOffice** | Apache License 2.0 | Açık kaynak, çoklu işletim sistemi ve ofis biçimleri | 14.10.2026 tarihinde 4.1.17 güvenlik sürümü yayımlanmış olsa da LibreOffice'in UNO SDK/entegrasyon ekosistemi bu araştırma için daha uygun ilk adaydır. İkinci öncelikli karşılaştırma seçeneği. |

### İlk değerlendirme

**LibreOffice Writer/UNO**, yerel ve mümkün olduğunca çevrimdışı çalışan MİHENK için araştırılacak ilk kelime işlemci motorudur. Bu, teknoloji kararı değildir. En azından aşağıdaki işlemlerle PoC yapılmalıdır:
- MİHENK'in kendi rapor şablonundan yeni belge üretme.
- Tablo, birleştirilmiş hücre, üstbilgi/altbilgi, sayfa numarası, dipnot, liste ve ekleri koruma.
- Türkçe karakter ve farklı fontları doğrulama.
- DOCX/ODT/PDF içe/dışa aktarma.
- UYAP Doküman Editörü'nde açma ve sayfa düzeni karşılaştırması.
- Büyük rapor ve yüzlerce sayfalı ek paketinde bellek/performans.
- Motor çökmesi halinde görevin kaybolmadan yeniden açılması.

ONLYOFFICE ve Collabora, aynı test belgeleriyle karşılaştırılmalı; yalnızca arayüz benzerliğine göre seçilmemelidir.

## 4. UDF biçimi ve açık kaynak topluluk araçları

UYAP'ın resmî kullanıcı yardımında UDF'nin iç teknik paket yapısı için geliştirici belgesi veya resmî format spesifikasyonu yayımlanmış görünmüyor. Topluluk projeleri UDF'yi ZIP tabanlı paket ve XML belge içeriği olarak tersine mühendislikle inceliyor. Bu açıklamalar resmî teknik standart değil, topluluk gözlemi/uygulamasıdır.

### İncelenen topluluk projeleri

| Proje | Lisans / gözlem | Yetenek | Karar |
|---|---|---|---|
| [gokselb/udfpdf](https://github.com/gokselb/udfpdf) | Apache 2.0; TypeScript paketi; CI, tip kontrolü ve testler mevcut; yayımlanan paket sürümü 0.1.0 | UDF okuyup PDF, DOCX, HTML, Markdown ve metne dönüştürme | **UDF içe alma/okuma PoC adayı.** Tam editör, UDF yazarı veya imza motoru değildir. Arşiv açma güvenliği, XML boyutu, bozuk dosya, tablo/görsel kapsamı ve imzalı belge davranışı ayrıca denetlenmelidir. Üçüncü taraf test fikstürü MİHENK'e taşınmayacak; sentetik fixture üretilecek. |
| [saidsurucu/UDF-Toolkit](https://github.com/saidsurucu/UDF-Toolkit) | Depoda LICENSE dosyası ve açık bir lisans bildirimi bulunamadı | Python betikleriyle DOCX/PDF ↔ UDF dönüştürme denemeleri | Açık kaynak lisansı kanıtlanmadan kodu kopyalamak veya bağımlılık yapmak yok. Yalnızca teknik araştırma referansı. |
| [johanfaberrr/uyap-udf-mcp](https://github.com/johanfaberrr/uyap-udf-mcp) | README MIT lisansı belirtiyor; 01.05.2026 tarihli ilk commit görünüyordu | Metin/biçimlendirme paragraflarından temel UDF üretimi; MCP servis biçimi | Erken aşama ve dar kapsamlıdır; kapsamlı sayfa düzeni editörü, doğrulama paketi veya UYAP imza çözümü değildir. Şimdilik yalnızca araştırma referansı. |
| [miasimbilir/udf-cevirici](https://github.com/miasimbilir/udf-cevirici) | Kaynak kod kullanım koşulları ticari ürüne dahil etmeyi yazılı izne bağlıyor/yasaklıyor | DOCX/ODT/RTF ↔ UDF dönüşümü; Windows/macOS masaüstü uygulaması | MİHENK'e dahil edilmeyecek. Yazılı izin ve ayrı hukukî değerlendirme olmadan kodu, kütüphanesi veya türevi kullanılamaz. |

### UDF için önerilen yaklaşım

1. MİHENK kendi, biçimden bağımsız bir rapor belge modeli tutar.
2. DOCX/ODT/PDF üretimi kelime işlemci motoru ve belge üretim katmanıyla yapılır.
3. UDF okuma/dönüşüm için lisansı uygun, güvenlik incelemesinden geçmiş bir uyarlayıcı araştırılır. `udfpdf` ilk PoC adayıdır; doğrudan ürün bağımlılığı değildir.
4. UDF yazma desteği ancak sentetik belgeler UYAP Editör'de açılıp kaydedilerek; tablo, görsel, sayfa düzeni, metin, metadata ve doğrulama kodu karşılaştırılarak kabul edilir.
5. Elektronik imza bilgisi bulunan bir UDF dosyasına müdahale edildiğinde imzanın korunacağı varsayılmaz. İmzalı belge değişikliği yeniden imzalama gerektirebilir.
6. UYAP'ın resmi editörü ve Adalet e-İmza uygulaması, resmî UDF/imza doğrulamasında güvenilir son aşama olarak korunur. Yetkili yerel API veya belgelenmiş entegrasyon bulunmadan imza otomasyonu yapılmaz.

## 5. PDF görüntüleme, işleme ve OCR

| Bileşen | Lisans | Uygun kullanım | Sınır |
|---|---|---|---|
| [PDF.js](https://github.com/mozilla/pdf.js) | Apache 2.0 | MİHENK içinde PDF görüntüleme, sayfa gezintisi ve metin katmanı gösterimi | Tam PDF sayfa düzeni editörü değildir |
| [Apache PDFBox](https://pdfbox.apache.org/) | Apache 2.0 | PDF metin çıkarma, birleştirme/bölme, form, PDF üretimi ve PDF imzalama API'leri | UYAP UDF/e-imza sürecinin yerine geçmez; imza kabulü ve sertifika zinciri ayrıca test edilir |
| [OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) | MPL 2.0; bazı bileşenlerin ayrı lisansları vardır | Taranmış PDF'ye aranabilir metin katmanı eklemek, sayfa düzeltme ve OCR hattı | Genel amaçlı belge editörü değildir; çalıştırma motoru ve yardımcı bağımlılıkları paketlenmelidir |
| [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) | Apache 2.0 | Türkçe dahil dil modelleriyle görüntüden metin çıkarma | Dil modeli paketi ayrıca dağıtılır; OCR sonucu insan tarafından doğrulanması gereken metindir |

Stirling PDF gibi çok özellikli araçlar kullanıcıya kapsamlı görünse de proje deposunda uygulama düzeyinde üretim lisansı/abonelik koşulları bulunabilmektedir. Bir ürünün GitHub'da açık kaynak olarak görünmesi, bütün uygulamanın MİHENK'e ücretsiz ve sınırsız gömülebileceği anlamına gelmez. Bileşen ve lisans bazında inceleme yapılmadan bu tür paketler kullanılmamalıdır.

Türkçe OCR için `tur` dil verisi mevcuttur. Ancak Türkçe ad, sayı, tarih, tablo, mühür, el yazısı ve düşük kaliteli taramalarda doğruluk ayrı test edilmelidir.

## 6. MİHENK için belge işleme mimarisi önerisi

- **Tek rapor modeli:** İçerik, başlık, paragraf, tablo, görsel, ek, kaynak bağlantısı, sayfa ve imza durumu; UDF/DOCX/ODT/PDF'den bağımsız saklanır.
- **Belge oluşturma:** Görev Profili ve uzmanlık modülünden gelen doğrulanmış alanlar, göreve ait temiz şablona aktarılır.
- **Düzenleme:** MİHENK'in kendi arayüzünde çalışan gömülü ofis motoru; kullanıcı başka bir uygulamada dosya aramaz.
- **PDF:** Görüntüleme, sayfa organizasyonu, metin çıkarımı, OCR ve export aynı görev alanından yürütülür.
- **UDF:** Ayrı ve testli adaptör; resmî editörle karşılaştırmalı uyumluluk.
- **İmza:** Nihai içerik dondurulduktan sonra, imza için yetkili/resmî Adalet e-İmza ve UYAP akışı kullanılır. Özel anahtar ve PIN MİHENK'e alınmaz.
- **Çıktı denetimi:** Rapor kaynağı, şablon sürümü, çıktı formatı, oluşturma zamanı ve son değişiklik/imza durumu kaydedilir.

## 7. Güvenlik ve lisans kabul kapıları

Hiçbir açık kaynak bileşen yalnızca yıldız sayısı veya kolay kurulum nedeniyle seçilmez. Aday bileşen için:
- Ana ve tüm transitif bağımlılık lisansları/SBOM çıkarılır.
- Ticari dağıtım, ağ üzerinden kullanım, markalama, kaynak kod açıklama ve türev eser koşulları hukukî olarak değerlendirilir.
- Kaynak depo etkinliği, sürümleme, güvenlik bildirimi, test kapsamı ve bakım sorumlusu incelenir.
- İmzasız/zararlı paket, ZIP bombası, XML entity/DoS, bellek tüketimi ve hatalı font/görsel dosyası test edilir.
- Bileşen mümkün olduğunda ağ erişimi kapalı, görev bazında izole işçi süreçte çalıştırılır.
- Paket ve güncellemeler imza/checksum ile doğrulanır; sürüm sabitlenir ve geri alma yolu bulunur.
- Gerçek vaka verisi test fikstürü veya telemetriye girmez.

## 8. Araştırma sonucu — şimdilik karar değil

**İlk yerel editör PoC adayı:** LibreOffice Writer/UNO.  
**Web editörü alternatifleri:** Collabora Online ve ONLYOFFICE; lisans ve dağıtım modeli karşılaştırılmalı.  
**PDF araç adayları:** PDF.js + PDFBox + OCRmyPDF/Tesseract.  
**UDF okuma/dönüşüm PoC adayı:** Apache 2.0 lisanslı `udfpdf`; güvenlik ve biçim kapsamı testi şart.  
**UDF/imza son aşaması:** Resmî UYAP Doküman Editörü ve Adalet e-İmza akışıyla doğrulama.

Henüz hiçbir bileşen MİHENK uygulamasına eklenmedi. Teknoloji seçimi ve bağımlılık kilitlemesi ayrı mimari karar kapısında yapılacaktır.

## 9. Kaynaklar

- [UYAP Editör Yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
- [UYAP Editör indirme sayfası](https://www.uyap.gov.tr/UYAP-Editor)
- [UYAP Doküman Editörü güncelleme duyurusu — 31.05.2026](https://bigm.adalet.gov.tr/Home/SayfaDetay/uyap-dokuman-editoru-guncellendi01062026122201)
- [LibreOffice lisansları](https://www.libreoffice.org/licenses/)
- [LibreOffice 26.8 SDK](https://api.libreoffice.org/)
- [LibreOffice SDK örnekleri](https://api.libreoffice.org/examples/examples.html)
- [LibreOffice desteklenen dosya biçimleri](https://books.libreoffice.org/en/GS262/GS26210-FileFormatsSecurityExporting.html)
- [ONLYOFFICE Community lisans açıklaması](https://helpcenter.onlyoffice.com/docs/faq/docs-community.aspx)
- [ONLYOFFICE Desktop Editors çevrimdışı kullanım](https://helpcenter.onlyoffice.com/desktop/getting-started)
- [Collabora Online entegrasyon ve WOPI](https://www.collaboraonline.com/faqs/)
- [Collabora CODE üretim uyarısı](https://www.collaboraonline.com/code/)
- [Apache PDFBox](https://pdfbox.apache.org/)
- [OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF)
- [Tesseract dil dosyaları — Türkçe `tur`](https://tesseract-ocr.github.io/tessdoc/Data-Files.html)
- [PDF.js](https://github.com/mozilla/pdf.js)
