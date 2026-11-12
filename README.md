# MİHENK — Araştırma, Ürün Keşfi ve Proje Yönetimi

> **Durum:** Keşif ve gereksinim doğrulama aşaması  
> **Güncelleme:** 12 Kasım 2026  
> **Ürün/kod kararı:** Henüz verilmedi

## MİHENK nedir?

MİHENK, Türkiye'de bilirkişilerin işlerini daha düzenli, güvenli ve verimli yürütebilmeleri için ihtiyaçları araştırılan yeni bir proje girişimidir. Nihai ürün kapsamı, gerçek bilirkişilerle yapılacak görüşmeler ve mevzuat/teknik doğrulama sonrasında kararlaştırılacaktır.

Bu depo **araştırma, gereksinim, ürün kararları, mimari kararlar ve proje yönetimi belgeleri** içindir. Uygulama kaynak kodu burada tutulmayacaktır.

## Önemli proje kararı

**MİHENK sıfırdan tasarlanacaktır.** Aşağıdaki iki proje yalnızca önceki denemeleri ve kullanıcıya gösterilmiş örnekleri anlamak için referanstır:

- [forensic-transcriber](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next](https://github.com/azmisahin-gov/forensic-transcriber-next)

Bu projelerden kod, mimari, veri modeli, bağımlılık, arayüz bileşeni veya paket taşınmayacaktır. Bunlar MİHENK'in teknik başlangıç noktası, pilot uygulaması veya temel alınacak şablonu değildir. Gerektiğinde yalnızca geçmişte hangi yaklaşımın denendiğini anlamak için incelenebilir.

## Depo ayrımı

| Depo | Sorumluluk |
|---|---|
| `azmisahin-gov/mihenk` | Araştırma, mevzuat, anonim görüşme sentezleri, gereksinimler, ürün/mimari kararları ve yol haritası |
| Yeni uygulama deposu (adı daha sonra kararlaştırılacak) | MİHENK uygulamasının sıfırdan geliştirilecek kaynak kodu, testleri, build ve release süreçleri |

Uygulama geliştirme kararı çıkmadan ikinci depo açılmayacak ve kod yazılmaya başlanmayacaktır. İki depo arasında README bağlantıları ve karar/sürüm referansları bulunacaktır.

## Proje yönetimi

- **Proje sahibi / saha araştırması:** Kullanıcı. Bilirkişilerle görüşür, soruları sorar, anonimleştirilmiş bulguları aktarır ve iş/ürün kararlarını onaylar.
- **Ürün ve teknik çalışma ortağı:** ChatGPT. Araştırmayı yürütür, bulguları yapılandırır, gereksinim/risk/karar kayıtlarını günceller, alternatifleri karşılaştırır ve GitHub belgelerini yönetir.
- **Alan uzmanları:** Bilirkişiler ve gerektiğinde hukukçu/kişisel veri uzmanı. Mesleki pratiği, mevzuat yorumunu ve iş akışını doğrular.

ChatGPT arka planda sürekli çalışan veya kendiliğinden bilirkişilerle görüşen bir yönetici değildir. Çalışma, kullanıcı yeni bilgi sağladığında veya görev verdiğinde oturum içinde yürütülür.

## İlk aşamada beklenen sonuç

1. Hedef kullanıcı ve problem tanımı.
2. Bilirkişi görev yaşam döngüsünün gerçek saha haritası.
3. UYAP ve diğer resmî sistemlerle sınırların belirlenmesi.
4. Tekrarlanan, maliyetli ve yazılımla çözülebilir sorunların kanıtlanması.
5. Ürün kapsamı ve ilk uzmanlık/modül kararının verilmesi.
6. Uygulama yapılacaksa sıfırdan teknoloji ve mimari seçimi.
7. Ayrı uygulama deposu açılması ve geliştirme planı.

## Belge haritası

- `docs/00-yonetim/`: amaç, çalışma yöntemi, proje yönetimi ve karar kuralları
- `docs/01-arastirma/`: mevzuat, başvuru, UYAP, görev akışı ve örnek proje incelemeleri
- `docs/02-urun/`: kullanıcılar, yolculuklar, gereksinimler ve MVP hipotezleri
- `docs/03-uzmanlik-modulleri/`: uzmanlık bazlı keşif notları; henüz seçilmiş modül değildir
- `docs/04-mimari/`: teknoloji bağımsız mimari ilkeleri ve veri modeli hipotezleri
- `docs/05-guvenlik-ve-mevzuat/`: hukuk, KVKK, tehdit, delil bütünlüğü ve yedekleme
- `docs/06-dogrulama/`: görüşme, test ve pilot planları
- `docs/07-yol-haritasi/`: aşamalar ve karar kapıları
- `docs/08-karar-ve-acik-konular/`: ADR, risk ve açık sorular
- `templates/`: görüşme ve ürün şablonları

## Çalışma kuralları

- Doğrulanmış bilgi, hukuki zorunluluk, teknik öneri, ürün hipotezi ve kullanıcı talebi birbirinden ayrılır.
- Kullanıcı görüşmesi olmadan ürün özelliği kesin gereksinim sayılmaz.
- Hukukî yorum, yetkin uzman teyidi olmadan kesin hüküm olarak sunulmaz.
- Gerçek vaka dosyası, ses, kişisel veri, UYAP ekran görüntüsü veya gizli evrak bu depoya yüklenmez.
- Büyük ürün/teknoloji kararları ADR ile kaydedilir.
- Uygulama kodu ayrı depoda, dal/PR/test disipliniyle geliştirilir.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [2026 Bilirkişilik Siciline Kabul Usul ve Esasları](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122125906255Bilirkişilik%20Siciline%20Kabule%20İlişkin%20Usul%20Ve%20Esaslar.pdf)
- [2026 Temel ve Alt Uzmanlık Alanları](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
