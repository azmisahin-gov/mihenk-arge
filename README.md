# MİHENK — Araştırma, Ürün Keşfi ve Proje Yönetimi

> **Durum:** Sistem haritası v1.0 ve Wireframe v0.5 ürün sahibi tarafından kabul edildi; uygulama eşleme/teknik kabul aşamasına geçiliyor.  
> **Güncelleme:** 15 Kasım 2026  
> **İlk teslimat:** 56.12 kontrollü uzman pilotu  
> **Wireframe durumu:** v0.5 kabul edildi — uygulama, bilirkişi, UYAP ve bağımsız güvenlik testleri açık

MİHENK, bilirkişilerin görevlendirme, materyal inceleme, bulgu ve rapor hazırlama işlerini tek bir çalışma alanında daha güvenli ve düzenli yürütmesini hedefleyen bir üründür. Proje sahibi ilk kullanılabilir teslimatın 56.12 — Ses Kayıtlarının Metne Dönüştürülmesi kontrollü uzman pilotu olmasını istemiştir. Bu, tüm bilirkişilik alanları için genel platform MVP'sinin veya nihai ürün tasarımının tamamlandığı anlamına gelmez; v0.5 wireframe hâlâ taslaktır.

Bu depo **araştırma, mevzuat, anonimleştirilmiş saha sentezleri, gereksinimler, ürün/mimari kararları ve proje yönetimi** içindir. Uygulama kaynak kodu burada tutulmaz.

## Depo ayrımı

| Depo | Sorumluluk | 13.11.2026 durumu |
|---|---|---|
| [mihenk-arge](https://github.com/azmisahin-gov/mihenk-arge) | Araştırma, ürün keşfi, gereksinim, mevzuat, risk ve karar belgeleri | Aktif belge deposu |
| [mihenk](https://github.com/azmisahin-gov/mihenk) | MİHENK masaüstü uygulamasının kodu, testleri, CI ve release süreçleri | Prototip/önizleme geliştirmesi mevcut; 0.1.0-53 kullanıcının denediği sürümdür, ilk kullanılabilir pilot kabul edilmemiştir |

İlk teslimat kapsamının 56.12 kontrollü pilotu olması yönünde ürün kararı vardır. Wireframe, resmî rapor/UYAP biçimi ve gerçek uzman kabulü henüz tamamlanmadığından ilk pilotun kullanıma hazır olduğu söylenemez. Genel platformun tüm uzmanlıkları kapsayan kapsamı ve uzun vadeli yayın/lisans tercihleri ayrıca olgunlaştırılacaktır. Uygulama deposunun public olması, kaynak kodun herkese açık olacağı anlamına gelir; bu tercih bilinçli değilse ilk kaynak kodu eklenmeden önce private yapılması değerlendirilmelidir. Public görünürlük tek başına açık kaynak lisansı seçildiği anlamına gelmez.

## MİHENK sıfırdan tasarlanacak

Önceki iki proje yalnızca geçmişteki denemeleri ve kullanıcı deneyimini anlamak için referanstır:

- [forensic-transcriber](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next](https://github.com/azmisahin-gov/forensic-transcriber-next)

Bu projelerden kod, mimari, veri modeli, bağımlılık, arayüz bileşeni, model veya paket taşınmayacaktır. Bunlar MİHENK'in teknik başlangıç noktası değildir.

## İlk saha çalışmasının mevcut anlamı

İlk deneme, bir bilirkişinin 56.12 kapsamındaki örnek ses-kayıt işi ve UYAP Bilirkişi Portal ekran akışı üzerinden yürütüldü. İlk gözlemler, tek başına transkripsiyon üretmenin yeterli olmadığını; materyal kabulü, güvenli envanter, inceleme, düzeltme, raporun biçimlendirilmesi ve teslim öncesi kontrollerin de işin parçası olduğunu düşündürüyor. Bunlar henüz doğrulanması gereken ürün hipotezleridir.

56.12, proje sahibinin talimatıyla ilk kullanılabilir teslimatın odak uzmanlık modülüdür. Bu karar, MİHENK'in uzun vadede yalnızca 56.12 olacağı anlamına gelmez; platformun diğer uzmanlık modüllerine genişlemesi hedeflenir. 56.11 ile kapsamı karıştırılmayacaktır. 56.12 wireframe v0.5 güncel değerlendirme taslağıdır; kullanıcı tarafından henüz kabul edilmemiştir.

## Güncel devam noktası — 15 Kasım 2026

- İlk teslimat yönü: 56.12 ses kayıtlarının metne dönüştürülmesi kontrollü uzman pilotu.
- Önceki kullanıcı deneyimi taslağı: [Wireframe v0.3](docs/02-urun/56-12-wireframe-v0.3.md) ve [SVG ekran panosu](docs/02-urun/56-12-wireframe-v0.3.svg). **Kabul edilmedi.**
- Önceki taslak: [Wireframe v0.4](docs/02-urun/56-12-wireframe-v0.4.md). **Kabul edilmedi; tarihsel taslak olarak korunuyor.**
- Kabul edilen tasarım: [Wireframe v0.5](docs/02-urun/56-12-wireframe-v0.5.md): [01 modül/motor hiyerarşisi](docs/02-urun/wireframe-v0.5-01-modul-ve-motor-hiyerarsisi.svg) · [02 yeni görevlendirme](docs/02-urun/wireframe-v0.5-02-yeni-gorevlendirme-akisi.svg) · [03 görev çalışma alanı](docs/02-urun/wireframe-v0.5-03-gorev-calisma-alani.svg) · [04 ses inceleme tezgâhı](docs/02-urun/wireframe-v0.5-04-ana-ses-inceleme-tezgahi.svg) · [05 tek rapor/A4](docs/02-urun/wireframe-v0.5-05-tek-rapor-a4.svg) · [06 daraltılabilir ana menü](docs/02-urun/wireframe-v0.5-06-daraltilebilir-ana-menu.svg). **Proje sahibi kabul etti; uygulama ve 56.12 alan uzmanı testleri açık.**
- Ürün sözleşmesi: [56.12 ilk teslimat sözleşmesi](docs/02-urun/56-12-ilk-teslimat-urun-sozlesmesi.md).
- Kalite/denetim: [56.12 Kalite Güvencesi ve Denetim Modeli v1.0](docs/02-urun/56-12-kalite-ve-denetim-modeli-v1.0.md) — bilirkişi öz kontrolü, bağımsız dosya incelemesi ve MİHENK ürün denetimi.
- Yeni oturum başlangıcı: [Uygulama devir noktası](docs/00-yonetim/yeni-oturum-baslangic-noktasi.md).
- Sistem tasarımı: [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](docs/02-urun/mihenk-sistem-ve-kullanici-akisi-v1.0.md). Bu belge ana gezinme, ekran kataloğu, ayar sahipliği, ASR yönetimi, rapor ve hata akışlarının referansıdır.
- Yeni oturum için tek başlangıç belgesi: [Oturum devam noktası](docs/00-yonetim/yeni-oturum-baslangic-noktasi.md).
- Wireframe v0.5 proje sahibi tarafından kabul edildi. Sıradaki adım mevcut uygulama main/feature dallarını ve issue'larını denetlemek, var olan çalışan özellikleri korumak ve kabul edilen tasarıma eşlemek.
- 0.1.0-53 masaüstü önizlemesinde bilinen kullanıcı blokajları: uygulamanın X ile kapanması, kasa açılışında kayıtlı sesin seçilmesi/oynatmaya hazır hâle gelmesi, dayanak seçicisinin düzeni ve güncelleme hatalarının tanılanması.
- Resmî UYAP Editör uyumu gerçek Windows Editör aç/kaydet/yeniden aç testi olmadan ilan edilmeyecek.

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
- `docs/02-urun/`: kullanıcılar, yolculuklar, gereksinimler, 56.12 ilk teslimat sözleşmesi ve wireframe taslakları
- `docs/03-uzmanlik-modulleri/`: uzmanlık bazlı araştırma; ilk teslimat odağı 56.12, diğer modüller sonraki aşamalar
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
