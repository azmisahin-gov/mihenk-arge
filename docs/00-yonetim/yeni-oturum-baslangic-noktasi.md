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
- **Güncel wireframe:** v0.3; **kullanıcı tarafından kabul edilmedi**. Yalnızca daha önceki taslaklara göre daha iyi bulunan bir çalışma taslağıdır.
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
2. [Karar kaydı](../08-karar-ve-acik-konular/karar-kaydi.md) — ADR-032–035
3. [56.12 ilk teslimat ürün sözleşmesi](../02-urun/56-12-ilk-teslimat-urun-sozlesmesi.md)
4. [56.12 wireframe v0.3](../02-urun/56-12-wireframe-v0.3.md)
5. [Görevlendirme belgesi ve Görev Profili](../02-urun/gorevlendirme-belgesi-ve-gorev-profili.md)
6. [Alan modeli](../04-mimari/alan-modeli.md)
7. [Bütünleşik uzmanlık modülü mimarisi](../04-mimari/butunlesik-uzmanlik-modul-mimarisi.md)
8. [56.12 minimum sürüm kapsamı ve 12 kabul kapısı](../03-uzmanlik-modulleri/ilk-pilot/56-12-minimum-surum-kapsami.md)
9. [56.12 test planı ve senaryoları](../03-uzmanlik-modulleri/ilk-pilot/56-12-test-plani-ve-basari-olcutleri.md) ve [test senaryoları](../03-uzmanlik-modulleri/ilk-pilot/56-12-test-senaryolari.md)
10. [Resmî UYAP/görevlendirme akışı](../01-arastirma/uyap-is-akisi.md)
11. [Otomasyon matrisi](../02-urun/otomasyon-matrisi.md)
12. [Yol haritası](../07-yol-haritasi/asamalar.md)
13. [Açık sorular](../08-karar-ve-acik-konular/acik-sorular.md) ve [risk kaydı](../08-karar-ve-acik-konular/risk-kaydi.md)

### Rapor konusunda önemli araştırma notu

Bilirkişilik Daire Başkanlığının sayfasındaki örnek rapor aileleri incelenmeli; ancak Mayıs 2025 Bilirkişilik Temel Eğitimi Kaynak Kitabı raporlar için özel ve değişmez tek bir şablon olmadığını, örneklerin ihtiyatla kullanılmasını ve kopyala-yapıştır yapılmamasını belirtiyor. MİHENK merci/yargı türüne ve görevlendirme içeriğine uygun rapor yapısı önermeli; sabit formu zorla uygulamamalı. UYAP Editör uyumluluğu gerçek Windows Editör'de aç/kaydet/yeniden aç testiyle kanıtlanmalı.

Kaynaklar:
- [Bilirkişi Rapor Şablonları — Bilirkişilik Daire Başkanlığı](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisi-rapor-sablonlari14032022105509)
- [Bilirkişilik Temel Eğitimi Kaynak Kitabı, Mayıs 2025](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/15052025204011Bilirkis%CC%A7ilik%20Temel%20E%C4%9Fitimi%20Kaynak%20Kitab%C4%B1.pdf)
- [Bilirkişiler İçin Kontrol Listesi](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20i%C3%A7in%20Kontrol%20Listesi.pdf)
- [UYAP Doküman Editörü resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)

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

## 7. Uygulama deposu ve çalışma dalları hakkında

Araştırma ve uygulama depoları ayrı tutulmaya devam etmeli. Araştırma deposundaki uygulama kodu/gerçek vaka dosyası eklenmemeli.

Bu oturumun başında araştırma deposunda:
- PR #1–#9: **birleştirilmiş**; bunlara ait branch isimleri eski squash-merge dalları olarak duruyor.
- PR #10: v0.2 ürün taslağı; **birleştirilmeden kapatıldı**, v0.3 ile supersede edildi.
- PR #11: v0.3 taslakları, ürün sözleşmesi, README/yol haritası/ADR ve bu devir belgesiyle birlikte **15.11.2026 tarihinde ana dala squash-merge edildi**.
- Son doğrulamada araştırma deposunda **açık PR ve açık issue yok**.
- Araştırma deposunun ana dalı: 1ece361d244cc02b508a534df99b0745317454ab.

Uygulama deposunda görülen dallar: main, feat/56-12-report-question-answers, feat/56-12-transcript-review-queue ve feat/56-12-transcript-revision-history. PR #45 yeni ürün akışı netleşene kadar kapatılmış, birleştirilmemişti. Bu eski uygulama dalları bir sonraki oturumda içerik ve PR ilişkileriyle birlikte ayrıca denetlenmeli; araştırma deposu dal temizliğiyle karıştırılmamalı. Son kontrolde uygulama deposunda açık PR görünmüyordu.

**Dal temizliği sınırı:** Araştırma deposunda 11 dal adı duruyor. Silinmeye aday, PR içeriği ana dala alınmış eski dallar şunlardır:
- PR #1: decision/from-scratch-and-repo-separation
- PR #2: discovery/first-field-findings-and-repo-split
- PR #3: research/field-workflow-and-quality-gates
- PR #4: research/case-specific-rules-and-turkish-docs
- PR #5: product/gorev-profili-and-intake-rules
- PR #6: product/synthetic-assignment-fixture-and-decisions
- PR #7: research/butunlesik-moduller-ve-belge-araclari
- PR #8: research/bakanlik-pardus-asr-ve-56-12-araclari
- PR #9: docs/56-12-teknik-is-akisi
- PR #11: docs/56-12-ilk-teslimat-plani

Bu PR'ların içerikleri ana dala alınmıştır; PR #10 aynı son dal üzerinde kapatılmış eski v0.2 taslağıdır ve yeni v0.3/ürün belgeleri PR #11 ile ana dala taşınmıştır. Açık PR/issue bulunmuyor. Bu oturumda bağlı GitHub araçları dalı okuma/güncelleme ve PR birleştirme/kapatmayı destekliyor; fiziksel branch silme eylemi sunmuyor. Bu nedenle silinmiş gibi gösterilmediler. Repo sahibinin GitHub [Branches ekranında](https://github.com/azmisahin-gov/mihenk-arge/branches) main dışındaki bu 10 eski branch'i silmesi son temizlik olacaktır.

Uygulama deposu ayrı tutulur. Son kontrolde şu üç eski uygulama dalı duruyordu: feat/56-12-report-question-answers, feat/56-12-transcript-review-queue, feat/56-12-transcript-revision-history. Uygulama deposunda açık PR yoktu; PR #45 kapalı ve birleştirilmemişti. Bu dallar, kod kaybı yaratmamak için yeni oturumda app main ile karşılaştırılmadan silinmemelidir.

## 8. Yeni oturumda izlenecek kesin sıra

**Aşama A — Depoyu yeniden doğrula**
1. Kullanıcının yeniden verdiği araştırma deposunu ve main dalını aç.
2. Bu devir belgesini ve yukarıdaki kaynak belgeleri oku.
3. README, ADR, yol haritası, açık sorular, risk kaydı, tüm PR ve branch durumlarını gerçek GitHub verisiyle doğrula.
4. Eski branch/PR durumlarını tekrar tahmin etme; canlı durumdan başla.

**Aşama B — Ürün akışını gerçekten netleştir**
1. İlk açılış, yerel kasa, profil ve uzmanlık alanı/modülü akışını tasarla.
2. Daraltılabilir sol menü, avatar menüsü, profil, kasa/güvenlik ve uygulama ayarlarını ayrıştır.
3. Genel Bakış dashboard'unu Görevlerim listesinden ayır.
4. Yeni görevlendirmede belgeyi otomatik okuma, kaynak izi, istisna doğrulaması ve bir görevin çoklu materyal/soru ilişkisini netleştir.
5. Görev içi sekmeler ile uygulama genel menüsünün farkını görsel olarak açıkla.
6. Tek rapor oluşturma, gerçek belge sayfası önizlemesi, bölüm listesi ve kontrol durumunu gerçekçi tasarla.
7. Boş durumlar, belge okuma başarısızlığı, desteklenmeyen modül, ASR hatası, kayıtlı sesi geri yükleme, rapor eksikleri, çevrimdışı kullanım ve kullanıcı geri dönüşünü de göster.
8. v0.3'ü kullanıcıyla birlikte gözden geçir; kabul edilmedikçe nihai tasarım sayma.

**Aşama C — Onay sonrası uygulamaya bağla**
1. Onaylanan ekranları gereksinimlere ve uygulama backlog'una eşle.
2. Önce P0 kullanıcı blokajlarını ele al: güvenli X ile kapanma, kayıtlı sesin doğru geri yüklenmesi/oynatılması, dayanak seçicisi düzeni, güncelleme hatasının tanılanması.
3. Profil/kasa/modül ve görev oluşturma ayrımını mevcut kodun üzerine uygula; gerekçesiz yeniden yazım yapma.
4. Otomatik görevlendirme okuma/çıkarımını sentetik belgeyle test et.
5. Çoklu ses/materyal, ASR kuyruğu, transkript, çoklu soru/kanıt ilişkisi ve tek raporu bir uçtan uca senaryoda birleştir.
6. Raporu güncel Windows UYAP Editör'de gerçek aç/kaydet/yeniden aç testiyle doğrula.
7. Temiz Windows MSI kurulumu, güncelleme/geri dönüş, kasa yedek ve kurtarma testlerini tamamla.
8. 56.12 uzmanı ile izinli/sentetik kontrollü pilot yap.

## 9. Öncelik verilmeyecek işler

Kullanıcı hedefiyle doğrudan bağlantı kurulmadan yeni ASR model ekleme, gelişmiş diarization, konuşmacı kimliklendirme, ses manipülasyon analizi (56.11 kapsamı), vektör arama/LLM ile kanaat yazma, genel uzmanlık modüllerini birden açma veya görsel cilalama önceliklendirilmemeli.

SEDA mevcut uygulamada entegre ilk yerel ASR denemesidir; “en iyi motor” olarak kesin seçilmemiştir. En az iki adayın aynı izinli insan referanslı Türkçe veriyle karşılaştırılması araştırma kararıdır. Kullanıcı tek bir program deneyimi ister; alt motorlar MİHENK tarafından yönetilir.

## 10. Oturuma yeniden başlamak için kullanıcı mesajı

Yeni oturumda kullanıcı araştırma reposunu verdiğinde şu şekilde başlanmalı:

> Önce docs/00-yonetim/yeni-oturum-baslangic-noktasi.md dosyasını ve orada bağlantısı verilen karar/ürün belgelerini oku. Bu devir belgesini özet olarak değil, repo içindeki güncel kaynaklarla karşılaştırarak doğrula. Wireframe v0.3 kabul edilmiş değildir; onu başlangıç taslağı olarak ele al. İlk hedef, 56.12 bilirkişisinin ilk açılıştan tek rapor önizlemesine kadar en kolay ve gerçekçi kullanıcı deneyimini birlikte netleştirmektir. Bu netleşmeden UI koduna geçme.

---

**Kapanış ölçütü:** Yeni oturum başladığında ilk iş tekrar “MİHENK ne yapacak?” sorusunu sıfırdan sormak değil; bu belgede kayıtlı hedefi doğrulamak, wireframe'i iyileştirmek ve kalan açık kararları kapatmaktır.
