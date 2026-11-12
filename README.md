# MİHENK — Araştırma, Ürün Keşfi ve Proje Yönetimi

> **Durum:** Keşif ve gereksinim doğrulama aşaması  
> **Güncelleme:** 13 Kasım 2026  
> **Ürün/MVP kararı:** Henüz verilmedi

MİHENK, Türkiye'de bilirkişilerin görevlerini daha güvenli, düzenli ve verimli yürütebilmeleri için ihtiyaçları araştırılan yeni bir ürün girişimidir. İlk saha gözlemleri başladı; ancak tek uzmanla yapılan ilk çalışma bütün bilirkişileri temsil etmez ve henüz MVP kararı oluşturmaz.

Bu depo **araştırma, mevzuat, anonimleştirilmiş saha sentezleri, gereksinimler, ürün/mimari kararları ve proje yönetimi** içindir. Uygulama kaynak kodu burada tutulmaz.

## Depo ayrımı

| Depo | Sorumluluk | 13.11.2026 durumu |
|---|---|---|
| [mihenk-arge](https://github.com/azmisahin-gov/mihenk-arge) | Araştırma, ürün keşfi, gereksinim, mevzuat, risk ve karar belgeleri | Aktif belge deposu |
| [mihenk](https://github.com/azmisahin-gov/mihenk) | MİHENK uygulamasının sıfırdan yazılacak kodu, testleri, CI ve release süreçleri | Ayrılmış, public ve henüz boş; geliştirme başlamadı |

Depoların adı ayrılmış olsa da ürün kapsamı, ilk sürüm, teknoloji, lisans ve yayın modeli henüz kararlaştırılmadı. Uygulama deposunun public olması, kaynak kodun herkese açık olacağı anlamına gelir; bu tercih bilinçli değilse ilk kaynak kodu eklenmeden önce private yapılması değerlendirilmelidir. Public görünürlük tek başına açık kaynak lisansı seçildiği anlamına gelmez.

## MİHENK sıfırdan tasarlanacak

Önceki iki proje yalnızca geçmişteki denemeleri ve kullanıcı deneyimini anlamak için referanstır:

- [forensic-transcriber](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next](https://github.com/azmisahin-gov/forensic-transcriber-next)

Bu projelerden kod, mimari, veri modeli, bağımlılık, arayüz bileşeni, model veya paket taşınmayacaktır. Bunlar MİHENK'in teknik başlangıç noktası değildir.

## İlk saha çalışmasının mevcut anlamı

İlk deneme, bir bilirkişinin 56.12 kapsamındaki örnek ses-kayıt işi ve UYAP Bilirkişi Portal ekran akışı üzerinden yürütüldü. İlk gözlemler, tek başına transkripsiyon üretmenin yeterli olmadığını; materyal kabulü, güvenli envanter, inceleme, düzeltme, raporun biçimlendirilmesi ve teslim öncesi kontrollerin de işin parçası olduğunu düşündürüyor. Bunlar henüz doğrulanması gereken ürün hipotezleridir.

56.12, ilk test senaryosudur; MİHENK'in seçilmiş tek uzmanlık alanı veya kesin MVP'si değildir. 56.11 ile kapsamı karıştırılmayacaktır.

## Ürün ilkesi

MİHENK'in hedefi “uzmanın yerine karar veren yazılım” değil; görevin başından sonuna kadar işi düzenleyen, tekrarlı kontrolleri yapan, kaynak materyali koruyan, belirsizlikleri görünür kılan ve uzmanın nihai teknik değerlendirmesini destekleyen bir çalışma ortamı hipotezidir.

Otomatik kontrol yalnızca tanımlı kontrollerin geçtiğini gösterebilir. Yazılım, raporun hukuken/mesleki olarak eksiksiz olduğunu veya incelemenin mutlak doğruluk taşıdığını garanti edemez. Nihai teknik kanaat, kanıt değerlendirmesi, rapor onayı ve resmî teslim bilirkişinin kontrolünde kalır.

## Proje yönetimi

- **Proje sahibi / saha araştırması:** Kullanıcı. Bilirkişilerle görüşür, anonimleştirilmiş bulguları aktarır ve kapsam/yayın kararlarını verir.
- **Ürün ve teknik çalışma ortağı:** ChatGPT. Araştırmayı, gereksinimleri, riskleri, kararları, yol haritasını ve GitHub belgelerini yürütmeye yardımcı olur.
- **Alan doğrulayıcıları:** Bilirkişiler, gerektiğinde hukukçu ve kişisel veri/güvenlik uzmanları.

ChatGPT kendiliğinden bilirkişilerle görüşemez veya sürekli arka planda çalışamaz; kullanıcı bilgi sağladığında ve görev verdiğinde oturum içinde ilerler.

## Public depo güvenliği

Her iki depo public olduğundan GitHub'a hiçbir koşulda gerçek vaka dosyası, ses/görüntü, dosya numarası, kişi/kurum bilgisi, UYAP ekran görüntüsü, rapor, e-imza/sertifika, erişim anahtarı, parola, üretim logu veya gizli evrak konmaz. Pseudonym kullanmak tek başına anonimleştirme garantisi değildir; tekil uzmanlık ve deneyim birleşimleri de kişiyi tanınabilir kılabilir. Saha bulguları yalnızca genelleştirilmiş ve yeniden kimliklendirme riski azaltılmış şekilde yayımlanır.

## Belge haritası

- `docs/00-yonetim/`: amaç, çalışma yöntemi, proje yönetimi ve karar kuralları
- `docs/01-arastirma/`: mevzuat, UYAP, görev akışı ve saha gözlemleri
- `docs/02-urun/`: kullanıcılar, yolculuklar, gereksinimler ve MVP hipotezleri
- `docs/03-uzmanlik-modulleri/`: uzmanlık bazlı araştırma; henüz seçilmiş modül yok
- `docs/04-mimari/`: teknoloji bağımsız mimari ilkeler ve veri modeli hipotezleri
- `docs/05-guvenlik-ve-mevzuat/`: hukuk, kişisel veri, tehdit, delil bütünlüğü ve yedekleme
- `docs/06-dogrulama/`: görüşme, test ve pilot planları
- `docs/07-yol-haritasi/`: aşamalar ve karar kapıları
- `docs/08-karar-ve-acik-konular/`: ADR, risk ve açık sorular
- `templates/`: görüşme ve ürün şablonları

## Çalışma kuralları

- Kullanıcı anlatımı, araştırmacı yorumu, resmî kaynak, teknik öneri ve hukuki zorunluluk birbirinden ayrılır.
- Tek görüşme veya tek test tüm bilirkişileri temsil eden kanıt sayılmaz.
- Hukukî yorum, yetkin uzman teyidi olmadan kesin hüküm olarak sunulmaz.
- UYAP için belgelenmiş ve yetkilendirilmiş entegrasyon olmadan giriş/ekran otomasyonu yapılmaz.
- Büyük ürün ve teknoloji kararları ADR ile kaydedilir.
- Uygulama kodu ayrı depoda, dal/PR/test disipliniyle geliştirilir.

## Resmî ve teknik kaynaklar

- [6754 sayılı Bilirkişilik Kanunu](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [2026 Temel ve Alt Uzmanlık Alanları](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [KVKK — Kişisel Verilerin Yurt Dışına Aktarılması Rehberi](https://www.kvkk.gov.tr/Icerik/8143/Kisisel-Verilerin-Yurt-Disina-Aktarilmasi-Rehberi)
- [NISTIR 8387 — Digital Evidence Preservation](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
