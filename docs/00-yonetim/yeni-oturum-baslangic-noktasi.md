# MİHENK — Yeni Oturum Başlangıç ve Devir Noktası

> **Son güncelleme:** 15 Kasım 2026  
> **Bu belge yeni oturumda ilk okunacak belgedir.**  
> **Ana amaç:** MİHENK'in ilk kullanılabilir 56.12 teslimatını netleştirmek; wireframe'i kullanıcıyla birlikte olgunlaştırmak; sonra mevcut uygulamayı bu tek hedefe göre ilerletmek.

## 1. Şu an neredeyiz?

Proje sahibi, yeni oturumda araştırma deposunu tekrar paylaşarak çalışmaya devam etmek istiyor. Bu belge, 14–15 Kasım 2026 oturumlarında alınan karar ve geri bildirimleri korumak için hazırlandı.

- **Araştırma deposu:** [azmisahin-gov/mihenk-arge](https://github.com/azmisahin-gov/mihenk-arge)
- **Uygulama deposu:** [azmisahin-gov/mihenk](https://github.com/azmisahin-gov/mihenk)
- **İlk teslimat yönü:** 56.12 — Ses Kayıtlarının Metne Dönüştürülmesi kontrollü bilirkişi pilotu.
- **Uzun vadeli ürün:** farklı uzmanlık modüllerini ortak çekirdekte sunan MİHENK platformu.
- **Güncel wireframe:** v0.3; **kullanıcı tarafından kabul edilmedi**.
- **Sistem tasarımı:** [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](../02-urun/mihenk-sistem-ve-kullanici-akisi-v1.0.md) hazırlandı; v0.4 wireframe'in ana referansıdır.
- **Bu oturumdaki uygulama kodu:** değiştirilmedi. Yeni MSI üretilmedi.
- **Önizleme sürümü:** proje sahibinin son bildirdiği gerçek kurulum 0.1.0-53'tür.

## 2. Proje sahibinin asıl istediği ürün

Teknik araçların sayısı veya model çeşitliliği amaç değildir. Amaç, bilirkişinin dosyayı aldığında MİHENK'in mümkün olan güvenli ve tekrarlı işleri otomatik yürütmesi ve bilirkişiye **tek, bütünlüklü, resmî rapor hazırlığına yönelik bir ana doküman** sunmasıdır.

Hedeflenen kullanıcı yolu:

1. Bilirkişi MİHENK'i ilk kez açar; yerel kasasını oluşturur ve kendi meslekî profilini bir kez tanımlar.
2. Bilirkişi profilinde ad-soyad, sicil numarası, meslekî unvan/sıfat ve uzmanlık alanları gibi raporda gerekebilecek bilgileri tutar. Profil UYAP hesabı değildir; uygulama UYAP parolası/e-imza PIN'i istemez.
3. Kullanıcı Görevlerim alanından **Yeni görevlendirme** başlatır ve mahkeme/merci görevlendirme belgesini, ek talimatları ve varsa teslim/dizi pusulasını ekler.
4. **Önce MİHENK belgeyi okur.** Merci, dosya referansı, süre, konu/kapsam, cevaplanacak sorular, istenen materyaller ve teslim koşullarını kaynak sayfa iziyle çıkarır. Kullanıcı baştan uzun bir form doldurmaz; yalnızca belirsiz, çelişkili veya okunamayan alanları doğrular.
5. Her görevlendirme ayrı bir çalışma alanıdır. Aynı görevde birden çok ses kaydı, başka belge ve birden çok soru olabilir. Görevlerin materyalleri, yanıtları ve raporları birbirine karışmaz.
6. MİHENK ses materyallerini envanterler; teknik bilgileri ve bütünlük değerlerini tutar; yerel ASR ile makine transkript taslağı üretir. Bilirkişi metni sesle karşılaştırır, düzeltir ve belirsiz kısımları işaretler.
7. Görevlendirme soruları tek tek gelir. Bilirkişi yanıtları aynı görevin kaynak materyal ve zaman aralıklarına bağlanır.
8. Kullanıcı **Tek raporu oluştur** dediğinde o göreve ait tüm materyal, yöntem, uzman tarafından doğrulanmış bulgu, soru-cevap ve ekler tek ana raporda birleştirilir. Raporun tamamı uygulama içinde önizlenir.
9. Bilirkişi son kontrolü yapar. UYAP Doküman Editörü, Adalet e-İmza ve Bilirkişi Portalı üzerinden resmî imza/teslim işlemlerini kendisi tamamlar.

**Önemli sınır:** MİHENK bilirkişinin teknik kanaatini veya hukuki değerlendirmesini uydurmaz; otomatik UYAP giriş/teslim veya e-imza işlemi yapmaz. MİHENK rapor hazırlığını otomatikleştirir ve insan kararını korur.

## 3. Kavramları birbirine karıştırma

| Kavram | Anlamı |
|---|---|
| Yerel kasa | Profil ve görev verilerini koruyan şifreli yerel veri alanı |
| Bilirkişi profili | Kullanıcının meslekî kimlik bilgileri; bir kez tanımlanır |
| Uzmanlık alanı | Bilirkişinin profilinde beyan ettiği temel/alt uzmanlık |
| Uzmanlık modülü | MİHENK'in o uzmanlık için sunduğu yazılım iş akışı/araçları |
| Görevlendirme | Mahkeme/merci tarafından verilen tek iş |
| Görev Profili | Belge ve talimatlardan çıkarılan o göreve özel kapsam, sorular, süre, materyal ve teslim koşulları |
| Materyal | Aynı göreve teslim edilen bir veya çok ses/dosya |
| Görev sorusu | Aynı görevlendirmede cevaplanması istenen bir veya çok soru |
| Tek rapor | Bir görevlendirmenin tüm bulgu ve yanıtlarını içeren tek ana rapor |

İlk teslimatta kullanılabilir uzmanlık modülü 56.12'dir. Kullanıcının profilinde birden çok uzmanlık alanı bulunması, bütün modüllerin yazılımda hazır olduğu anlamına gelmez.

İlk sürüm varsayımı olarak bir yerel kasa/bir bilirkişi profili düşünülmektedir; çoklu yerel kullanıcı desteği henüz kesin tasarım değildir.

## 4. Wireframe v0.3 durumu ve kullanıcı geri bildirimi

Dosyalar:
- [Wireframe v0.3 ekran açıklamaları](../02-urun/56-12-wireframe-v0.3.md)
- [Wireframe v0.3 SVG panosu](../02-urun/56-12-wireframe-v0.3.svg)
- [İlk teslimat ürün sözleşmesi](../02-urun/56-12-ilk-teslimat-urun-sozlesmesi.md)

Proje sahibi v0.3'ün önceki sürümlere kıyasla daha iyi olduğunu söyledi; ancak:
- Tasarımı kabul ettiğini söylemedi.
- Bazı tasarımsal/görsel sorunlar olduğunu belirtti.
- İlk kez kullanan bilirkişinin nereden başlayacağı ve ekranların neyi temsil ettiği tam olarak netleşmeli.
- Sol menünün ChatGPT benzeri daraltılıp genişletilmesini önerdi.
- Avatar/profil alanından profil sayfasına, ayrı bir yerden kasa/güvenlik ve uygulama ayarlarına gidilebileceğini düşündü.
- “Ayarlar”, “kasa”, “profil”, “uzmanlık alanı” ve “uzmanlık modülü” bilgilerinin iyi ayrıştırılmasını istedi.
- Genel Bakış'ın dashboard mu, görev listesi mi olduğu çok net olmalı; Görevlerim ayrı sayfa olmalı.
- Görevlendirme belgesini kullanıcının baştan okuyup elle forma girmesi yerine önce uygulamanın okumasını, kullanıcıya yalnız belirsiz alanları sormasını istiyor.
- Bir görevlendirmede birden çok ses/materyal ve birden çok soru olduğu ekranda anlaşılır biçimde gösterilmeli.
- “Tek rapor” bölümü ve gerçekçi sayfa önizlemesi beklenen çıktının merkezinde olmalı. Kullanıcı ayrı ayrı rapor formatları arasında seçim yapmak istemiyor.
- UI tasarımının ilk açılıştan tek raporun önizlenmesine kadar daha gerçekçi, kullanılabilir ve görsel olarak tutarlı hâle getirilmesini istedi.

**Yeni oturumda v0.3'ü nihai kabul gibi savunma.** Onu sadece başlangıç taslağı olarak kullan; gerekirse v0.4 veya yeniden tasarlanmış v0.3 üret. Kullanıcıya aceleyle onay verdirmeye çalışma.

## 5. Araştırma deposundaki güncel yön ve kaynak belgeler

Önce aşağıdaki belgeler yeniden açılıp birbirleriyle karşılaştırılmalı:

1. [Bu oturum devam belgesi](yeni-oturum-baslangic-noktasi.md)
2. [Karar kaydı](../08-karar-ve-acik-konular/karar-kaydi.md) — ADR-032–038
3. [56.12 ilk teslimat ürün sözleşmesi](../02-urun/56-12-ilk-teslimat-urun-sozlesmesi.md)
4. [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](../02-urun/mihenk-sistem-ve-kullanici-akisi-v1.0.md) — yeni sistem tasarımı ve v0.4 ekran kataloğu
5. [56.12 wireframe v0.3](../02-urun/56-12-wireframe-v0.3.md)
6. [Görevlendirme belgesi ve Görev Profili](../02-urun/gorevlendirme-belgesi-ve-gorev-profili.md)
7. [Alan modeli](../04-mimari/alan-modeli.md)
8. [Bütünleşik uzmanlık modülü mimarisi](../04-mimari/butunlesik-uzmanlik-modul-mimarisi.md)
9. [56.12 minimum sürüm kapsamı ve 12 kabul kapısı](../03-uzmanlik-modulleri/ilk-pilot/56-12-minimum-surum-kapsami.md)
10. [56.12 test planı ve senaryoları](../03-uzmanlik-modulleri/ilk-pilot/56-12-test-plani-ve-basari-olcutleri.md) ve [test senaryoları](../03-uzmanlik-modulleri/ilk-pilot/56-12-test-senaryolari.md)
11. [Resmî UYAP/görevlendirme akışı](../01-arastirma/uyap-is-akisi.md)
12. [Otomasyon matrisi](../02-urun/otomasyon-matrisi.md)
13. [Yol haritası](../07-yol-haritasi/asamalar.md)
14. [Açık sorular](../08-karar-ve-acik-konular/acik-sorular.md) ve [risk kaydı](../08-karar-ve-acik-konular/risk-kaydi.md)

### Rapor konusunda önemli araştırma notu

16.06.2025 tarihli konsolide Bilirkişilik Yönetmeliği m.55, raporda inceleme yöntemi ile bilimsel ve teknik dayanakların bulunmasını ister. 06.04.2026 tarihli Adalet Bakanlığı rehberi raporun somut nedenlere dayalı, denetlenebilir, anlaşılır ve gereksiz ayrıntıdan uzak olmasını; soruların tek tek cevaplanmasını vurgular. Resmî rapor şablonları merci/yargı türüne göre ayrı aileler hâlinde yayımlanır; MİHENK tek bir sabit şablonu her göreve zorlamaz.

ASR gerçekten kullanılmışsa, MİHENK ürün politikası olarak motor/model adı ve sürümünü inceleme yöntemi/teknik araçlar bölümünde kısa ve anlaşılır biçimde açıklar. Tam runtime/build/parametre/checksum ve kayıt bazındaki model eşlemesi teknik işlem kaydında, gerektiğinde teknik ekte tutulur. Yönetmelik belirli bir ASR marka/model adını açıkça zorunlu kılmaz; bu açıklama MİHENK'in denetlenebilirlik ve şeffaflık önerisidir. Makine çıktısı bilirkişi kontrolü olmadan nihai transkript gibi gösterilmez.

Kaynaklar:
- [16.06.2025 konsolide Bilirkişilik Yönetmeliği](https://rayp.adalet.gov.tr/resimler/494/dosya/bilirkisilik-yonetmeligi16-06-20254-49-pm.pdf)
- [Bilirkişilerin Uyacağı Rehber İlkeler ve Bilirkişi Raporlarında Bulunması Gereken Standartlar — 06.04.2026](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260406170009026Bilirkişilerin%20Uyacağı%20Rehber%20İlkeler%20ve%20Bilirkişi%20Raporlarında%20Bulunması%20Gereken%20Standartlar.pdf)
- [Bilirkişi Rapor Şablonları — Bilirkişilik Daire Başkanlığı](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisi-rapor-sablonlari14032022105509)
- [Bilirkişiler İçin Kontrol Listesi](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisiler-icin-kontrol-listesi14032022105444)
- [SWGDE Best Practices for Forensic Audio](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)

## 6. Mevcut masaüstü uygulaması: kullanıcıdan gelen gerçek bulgular

Proje sahibi MSI'ı manuel indirerek geliştirme önizlemesini takip ediyor:
- Kullanıcı 0.1.0-47 sürümünü denemiş ve ekran görüntüleri ile sorun bildirmişti.
- 0.1.0-51'den 52'ye otomatik güncelleme başarılı olmuştu.
- Kullanıcı sonrasında 53'e güncellendiğini bildirdi.
- X düğmesiyle normal kapatma hâlâ çalışmıyor; bazen Windows Görev Yöneticisi/sonlandırma gerekmiş.
- Daha önce “Güncelleme kurulamadı” mesajı görülmüş; sonraki güncelleme başarılı olmuş olsa da hata nedeni kanıtlanmış değil.
- Kasa açılışında kayıtlı ses listede görünse bile seçili/oynatmaya hazır olmayabiliyor; süre 00:00 kalabiliyor.
- Dayanak segmenti seçicisi dar alanda bozuluyor; metin dikeyleşiyor/yatay kaydırma oluşuyor.
- UI uzun ve tek sayfaya yayılan bir yapı gibi görünüyor; kullanıcı iş adımlarının ne işe yaradığını kolayca anlayamıyor.

Bunlar gerçek kullanıcı kabulünde P0/P1 önceliğinde ele alınmalı. Özellikle uygulamanın güvenli kapanması ve kayıtlı görev/ses bağlamının geri yüklenmesi, görsel ince ayarlardan önce gelmeli. Bu oturumda uygulama deposunda kod değiştirilmedi.

## 7. Güncel depo ve dal durumu — 15.11.2026 canlı kontrolü

Araştırma ve uygulama depoları ayrı tutulur. Araştırma deposuna uygulama kodu veya gerçek vaka dosyası eklenmez.

### Araştırma deposu: mihenk-arge

- Yetkili dal: main.
- Son canlı dal kontrolünde **yalnızca main** kaldığı doğrulandı.
- PR #1–#9 ve #11 birleştirilmiştir; PR #10 v0.2 taslağı birleştirilmeden kapatılmıştır.
- Açık PR: 0; açık issue: 0.
- Son doğrulanan main commit: e5461e8 (15.11.2026 oturum kontrolü).

Bu nedenle eski araştırma dallarının silinmesi işi tamamlanmış görünüyor; yeni oturumda yine canlı GitHub durumu esas alınmalıdır.

### Uygulama deposu: mihenk

Son canlı kontrolde dört dal vardı:
- main
- feat/56-12-report-question-answers
- feat/56-12-transcript-review-queue
- feat/56-12-transcript-revision-history

İçerik karşılaştırması:
- Soru-cevap/dayanak işinin güncel uygulama dilimi PR #42 ile main'e birleştirildi. Eski feat/56-12-report-question-answers dalı 16 commit önde ve 4 commit geride, yani ayrışmış eski bir geliştirme hattıdır; silinmemeli, PR #41 birleştirilmeden kapatılmıştır.
- Ham ASR metni ve transkript revizyon geçmişinin temel uygulama dilimi PR #40 ile main'e birleştirildi. Eski feat/56-12-transcript-revision-history dalı 33 commit önde ve 5 commit geride, yani ayrışmıştır; silinmemeli, PR #39 birleştirilmeden kapatılmıştır.
- feat/56-12-transcript-review-queue main'den 6 commit önde ve 0 commit geridedir. PR #45 birleştirilmeden kapatılmıştır; dört filtreli transkript inceleme kuyruğu main'e alınmamıştır. Bu özellik v0.4 tasarım/backlog değerlendirmesine taşınmalıdır.

Uygulama deposunda açık PR: 0. Son kontrol sırasında açık issue'lar #29–#34 ve #3 idi. Bunların bir kısmında eski “mevcut durum” metni sonradan birleştirilen PR'ları yansıtmamaktadır; issue'lar kapanmış sayılmamalı, tamamlanan dilimler ve kalan kabul maddeleri güncellenmelidir.

**Dal yönetimi sınırı:** Uygulama deposundaki üç eski özellik dalı main ile karşılaştırılmadan silinmemelidir. Bu oturumda dal silme/birleştirme yapılmadı. Araştırma deposu main dışında dal içermemektedir.

## 8. Yeni oturumda izlenecek kesin sıra

**Aşama A — Depo ve kaynak doğrulaması**
1. Araştırma deposunun main dalını ve uygulama deposunun main/dal/PR/issue durumunu canlı GitHub'dan kontrol et.
2. Bu devir belgesini, sistem tasarımı v1.0'ı, karar kaydını ve ürün sözleşmesini güncel repo içeriğiyle karşılaştır.
3. Araştırma ve uygulama depolarını ayrı tut; eski uygulama dallarını karşılaştırmadan silme.

**Aşama B — Sistem tasarımı ve v0.4 wireframe**
1. [MİHENK Sistem Haritası ve Uçtan Uca Kullanıcı Akışı v1.0](../02-urun/mihenk-sistem-ve-kullanici-akisi-v1.0.md) belgesini ana sistem tasarım referansı olarak kullan.
2. S-01–S-30 ekran kataloğunu, bilgi mimarisini ve bütün normal/boş/hata/çevrimdışı/kurtarma durumlarını v0.4 wireframe'e aktar.
3. ASR yönetimi ile görev içi ASR kuyruğu ayrımını özellikle göster.
4. Raporun tek ana çıktı olmasını; ASR/model bilgisinin yöntem bölümündeki şeffaf açıklama ve teknik provenance katmanını tasarla.
5. Kullanıcıyla v0.4 ekranlarını değerlendir; tasarım kabul edilmeden uygulama UI koduna geçme.

**Aşama C — Onay sonrası mevcut uygulamaya bağla**
1. Onaylanan ekranları gereksinimlere ve uygulama backlog'una eşle.
2. Önce P0 kullanıcı blokajlarını ele al: X ile güvenli kapanma, kayıtlı sesin seçili/oynatılabilir geri yüklenmesi, dayanak seçicisi düzeni, güncelleme hatasının tanılanması.
3. Profil/kasa/modül ve görev oluşturma ayrımını mevcut kod üzerinde uygula; gerekçesiz yeniden yazım yapma.
4. Sentetik görevlendirme belgesiyle otomatik çıkarım ve istisnaları test et.
5. Çoklu ses/materyal, yerel ASR kuyruğu, transkript/revizyon, çoklu soru/dayanak ve tek raporu uçtan uca bağla.
6. Güncel Windows UYAP Editör'de aç/kaydet/yeniden aç ve ilgili Portal evrak türünü doğrula.
7. Temiz kurulum, güvenli kapanma, kasa yedek/geri yükleme, güncelleme/geri alma ve E2E testlerini tamamla.
8. 56.12 uzmanıyla izinli/sentetik kontrollü pilot yap.

## 9. Öncelik verilmeyecek işler

Kullanıcı hedefiyle doğrudan bağlantı kurulmadan yeni ASR model ekleme, gelişmiş diarization, konuşmacı kimliklendirme, ses manipülasyon analizi (56.11 kapsamı), vektör arama/LLM ile kanaat yazma, genel uzmanlık modüllerini birden açma veya görsel cilalama önceliklendirilmemeli.

SEDA mevcut uygulamada entegre ilk yerel ASR denemesidir; “en iyi motor” olarak kesin seçilmemiştir. En az iki adayın aynı izinli insan referanslı Türkçe veriyle karşılaştırılması araştırma kararıdır. Kullanıcı tek bir program deneyimi ister; alt motorlar MİHENK tarafından yönetilir.

## 10. Oturuma yeniden başlamak için kullanıcı mesajı

Yeni oturumda kullanıcı araştırma reposunu verdiğinde şu şekilde başlanmalı:

> Önce docs/00-yonetim/yeni-oturum-baslangic-noktasi.md dosyasını ve orada bağlantısı verilen karar/ürün belgelerini oku. Bu devir belgesini özet olarak değil, repo içindeki güncel kaynaklarla karşılaştırarak doğrula. Wireframe v0.3 kabul edilmiş değildir; onu başlangıç taslağı olarak ele al. İlk hedef, 56.12 bilirkişisinin ilk açılıştan tek rapor önizlemesine kadar en kolay ve gerçekçi kullanıcı deneyimini birlikte netleştirmektir. Bu netleşmeden UI koduna geçme.

---

**Kapanış ölçütü:** Yeni oturum başladığında ilk iş tekrar “MİHENK ne yapacak?” sorusunu sıfırdan sormak değil; bu belgede kayıtlı hedefi doğrulamak, wireframe'i iyileştirmek ve kalan açık kararları kapatmaktır.
