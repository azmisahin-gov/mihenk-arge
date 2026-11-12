# Adalet Bakanlığı, UYAP ve Pardus Resmî Yazılım Araştırması

> **Durum:** Resmî kaynak incelemesi — sürüm ve destek bilgisi dağıtım öncesi yeniden kontrol edilmeli  
> **Araştırma tarihi:** 13 Kasım 2026

## 1. Araştırma sorusu

MİHENK, yargı ve bilirkişilik iş akışında kullanılan yazılımları seçerken önce Adalet Bakanlığı/UYAP'ın resmî olarak sunduğu veya desteklediği araçlara bakmalıdır. Resmî kurumun yayımlamadığı bir araç, yalnızca yaygın veya açık kaynak olduğu için Bakanlıkça onaylı sayılmaz.

Bu belge üç sınıfı birbirinden ayırır:
1. **Resmî ve Bakanlık kaynaklı:** UYAP/Adalet Bakanlığı tarafından geliştirilen veya resmî indirme/destek kanalıyla sunulan uygulamalar.
2. **Açık kaynak, fakat Bakanlık onayı doğrulanmamış:** MİHENK'te ayrıca lisans, güvenlik, veri kökeni ve test kapılarından geçmesi gereken bileşenler.
3. **MİHENK tarafından geliştirilecek:** Özgün iş akışı, görev yönetimi, kontrol, rapor bağlantısı, denetim izi ve kullanıcı arayüzü.

## 2. UYAP Doküman Editörü

Adalet Bakanlığı UYAP Editör Yardım sayfası, UYAP Doküman Editörü'nü Adalet Bakanlığı Bilgi İşlem Dairesi Başkanlığı tarafından geliştirilen ve UYAP Bilişim Sistemiyle entegre çalışabilen kelime işlemci olarak tanımlıyor.

Resmî indirme sayfası Windows, macOS, Pardus ve Debian tabanlı sistemler için paket yayımlıyor; ayrıca Android ve iOS uygulamalarına yönlendiriyor. 13.11.2026 tarihinde arama motorunun güncel sayfa önizlemesi Windows ve Pardus/Debian için v5.4.20, macOS için bazı mimarilerde v5.4.21 gösteriyordu. Aynı sayfanın önbelleğe alınmış metninde daha eski v5.4.17 göründüğü için sürüm numarası bu belgeye sabitlenmemelidir. Güncel paket yalnızca resmî sayfadan alınmalıdır.

Resmî yardım, UDF'nin varsayılan kayıt biçimi olduğunu; UDF dışında DOC, PDF, ODT, RTF ve çeşitli görsel biçimlere kaydetme seçenekleri bulunduğunu söylüyor. Bu durum UDF'yi UYAP akışında önemli kılar; ancak MİHENK'in tüm iç belge verisini UDF olarak tutması gerektiği anlamına gelmez.

### MİHENK için sonuç

- UYAP Doküman Editörü birincil resmî belge/son doğrulama aracıdır.
- MİHENK resmî editörün yerini aldığını veya onun tarafından onaylandığını iddia etmez.
- UYAP Editörü'nün kaynak kodu ve yeniden dağıtım lisansı kamuya açık kaynaklarda doğrulanmadı. Bu nedenle editörün ikili dosyaları MİHENK yükleyicisine dahil edilmeyecek veya uygulamanın içine gömülmüş gibi sunulmayacaktır.
- MİHENK kendi belge modelini, rapor üretimini, kalite kontrolünü ve doğrulanmış dışa aktarma adaptörlerini sunacaktır.
- UDF çıktısı ve imza davranışı sentetik belgelerle güncel resmî editörde doğrulanmadan üretim kabul kriteri sayılmayacaktır.
- Kullanıcı nihai aşamada resmî UYAP Editörü/e-İmza akışına geçebilir. Yetkilendirilmiş API veya belgelenmiş entegrasyon bulunmadan MİHENK bu işlemi taklit etmeyecektir.

## 3. Adalet e-İmza

Adalet Bakanlığı Bilgi İşlem Genel Müdürlüğünün 15.05.2026 tarihli duyurusu, Adalet e-İmza uygulamasının UYAP Avukat Portal girişinde 13.05.2026 tarihinde devreye alındığını belirtiyor. UYAP'ın 11.06.2026 tarihli duyurusu, ArkSigner üzerinden girişin 01.06.2026 tarihinde sonlandırıldığını; e-Devlet veya Adalet e-İmza Uygulaması yolunun kullanılacağını ve UYAP Doküman Editörü'nün güncel tutulması gerektiğini açıklıyor.

Bu duyurular portal girişinde e-imza doğrulamasını anlatır; her bilirkişi raporunun imzalanma veya gönderilme adımlarını bütünüyle açıklamaz. Bilirkişi Portal'ın güncel rehberi ve izinli test ortamı ayrıca doğrulanmalıdır.

**Karar:** MİHENK e-imza özel anahtarını, PIN'i veya kart sürücüsünü saklamaz; imza üretmez/taklit etmez. Raporun içeriği ve ekleri tamamlandıktan sonra resmî imza akışını destekleyen çıktı hazırlar. İmzalı belge değişirse imzanın geçersiz olabileceğini gösterir.

## 4. Pardus ile UYAP arasındaki gerçek ilişki

TÜBİTAK'ın Pardus kurumsal sayfası Pardus'u Debian GNU/Linux temelli, özgür ve açık kaynak işletim sistemi olarak tanımlıyor ve geliştirme/idame faaliyetlerinin TÜBİTAK BİLGEM Yazılım Teknolojileri Araştırma Enstitüsü bünyesinde sürdürüldüğünü belirtiyor.

UYAP'ın kendi sitesinde Doküman Editörü Adalet Bakanlığı Bilgi İşlem Dairesi Başkanlığının geliştirdiği yazılım olarak tanımlanıyor. Resmî indirme sayfasında Pardus ve Debian tabanlı sistemler için ayrı sürüm var. Pardus Yazılım Merkezi de UYAP Editörü'nü Adalet Bakanlığı uygulaması olarak listeliyor.

Bu bulguların desteklediği sonuç:
- **Pardus, UYAP Editörü değildir; UYAP da Pardus projesi değildir.**
- **UYAP Editörü Adalet Bakanlığı yazılımıdır; Pardus/Debian üzerinde çalışacak paket resmî olarak sunulmaktadır.**
- İncelenen güncel kaynaklar, UYAP ile Pardus'un tek bir ortak ürün olarak birlikte geliştirildiğini göstermiyor. Desteklenen ilişki, UYAP Editörü'nün Pardus/Debian uyumluluğudur.

### UYAP'ta açık kaynak ofis geçmişi

UYAP'ın Altyapı sayfası, geçmişte adli ve idari yargı birimleri ile Bakanlık bilgisayarlarında Microsoft Office kaldırılarak açık kaynak OpenOffice 2.4 kurulduğunu belirtiyor. Sayfadaki donanım tablosu 2000–2009 dönemini içeriyor. Dolayısıyla bu bilgi **tarihsel bir kullanım örneğidir; 2026'da aynı sürümün veya aynı ofis paketinin kullanıldığının kanıtı değildir**.

Bu tarihsel örnek, açık kaynak ofis yazılımının kamu adalet altyapısında geçmişte kullanılmış olduğunu gösterir. Güncel MİHENK teknoloji seçimi için doğrudan onay veya Bakanlık sertifikası sayılmaz.

## 5. Bakanlık tarafından onaylandığı doğrulanabilen araçlar

| Araç | Resmî kaynakta doğrulanabilen rol | MİHENK kararı |
|---|---|---|
| UYAP Doküman Editörü | Adalet Bakanlığı tarafından geliştirilmiş resmî kelime işlemci; UYAP ile entegre; UDF ve başka belge biçimleri | Son belge/uyumluluk/imza aşaması için esas alınacak resmî araç |
| Adalet e-İmza | Bakanlık Bilgi İşlem Genel Müdürlüğünün sunduğu resmî e-imza uygulaması | Resmî imza doğrulama akışı; özel anahtar/PIN MİHENK'e alınmaz |
| UYAP Bilirkişi Portal | Adalet Bakanlığınca sunulan görevlendirme, dosya inceleme, rapor gönderme ve iletişim hizmeti | Resmî görev ve teslim sistemi; yetkili API olmadan otomatikleştirilmez |
| Pardus | TÜBİTAK BİLGEM tarafından sürdürülen Debian tabanlı açık kaynak işletim sistemi | Desteklenen platformlardan biri; kullanıcının mevcut işletim sistemini değiştirmesi zorunlu değildir |

**Açık ASR/konuşma tanıma aracı konusunda**, incelenen kamuya açık Adalet Bakanlığı, UYAP ve Bilirkişilik Daire Başkanlığı kaynaklarında 56.12 için Bakanlıkça onaylanmış bir otomatik konuşma tanıma modeli veya yazılımı doğrulanamadı. Bu, kurum içinde veya kamuya açık olmayan kanallarda başka araç bulunmadığını kanıtlamaz. MİHENK'te açık kaynak ASR kullanılırsa bunun Bakanlıkça onaylandığı söylenmeyecek; MİHENK'in kendi teknik, hukukî ve uzman kabul testlerinden geçmiş bir yardımcı motor olduğu açıkça belirtilecektir.

## 6. Kaynaklar

- [UYAP Editör — resmî indirme sayfası](https://www.uyap.gov.tr/UYAP-Editor)
- [UYAP Editör Yardım — Bakanlıkça geliştirildiği ve UDF biçimi](https://uyap.gov.tr/Uyap-Editor-Yardim)
- [UYAP Doküman Editörü güncellendi — 11.06.2026](https://www.uyap.gov.tr/uyap-dokuman-editoru-guncellendi)
- [Adalet e-İmza Uygulaması Kullanıma Sunuldu — 15.05.2026](https://bigm.adalet.gov.tr/Home/SayfaDetay/adalet-e-imza-uygulamasi-kullanima-sunuldu15052026094330)
- [UYAP Bilirkişi Portal](https://kurum.uyap.gov.tr/main/bilirkisi.jsp)
- [Pardus Hakkımızda — TÜBİTAK](https://pardus.org.tr/hakkimizda/)
- [Pardus Tarihçesi — TÜBİTAK](https://pardus.org.tr/pardus-tarihce/)
- [Pardus Yazılım Merkezi — UYAP Editör](https://store.pardus.org.tr/app/uyapeditor)
- [Pardus Katkılarınızla Güçleniyor — UYAP Editör](https://pardus.org.tr/pardus-katkilarinizla-gucleniyor/)
- [UYAP Altyapı — tarihsel OpenOffice 2.4 kullanımı](https://uyap.gov.tr/Altyapi)
