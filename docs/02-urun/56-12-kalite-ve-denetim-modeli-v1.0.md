# MİHENK 56.12 — Kalite Güvencesi ve Denetim Modeli v1.0

> **Durum:** Wireframe v0.5'in kabulüyle ürün tasarımına eklenen kalite/denetim sözleşmesi. Uygulamada henüz tamamlanmış bir özellik veya bağımsız denetim onayı değildir.  
> **Tarih:** 15 Kasım 2026  
> **İlk kapsam:** 56.12 — Ses Kayıtlarının Metne Dönüştürülmesi kontrollü bilirkişi pilotu.

## 1. Neden iki ayrı denetim gerekir?

MİHENK'te iki farklı nesne denetlenir:

1. **Bilirkişinin görevi ve raporu:** Görevlendirme, materyal, ses, transkript, bulgu, soru yanıtları ve nihai raporun kaynağına bağlı ve eksiksiz olup olmadığı.
2. **MİHENK yazılımının kendisi:** Uygulamanın güvenli, tekrarlanabilir, çevrimdışı, doğru sürümlenmiş ve belirtilen kabul koşullarını gerçekten yerine getirip getirmediği.

Bunlar birbirinin yerine geçmez. Bir raporun bilirkişi tarafından onaylanması MİHENK'in güvenlik/kalite denetimini geçtiği anlamına gelmez. Yazılım testlerinin geçmesi de raporun meslekî olarak doğru veya hukuken yeterli olduğunu kanıtlamaz.

Bu nedenle üç katmanlı model uygulanır:

| Katman | Kim yapar? | Denetlenen şey | Kanıt/çıktı |
|---|---|---|---|
| A — Bilirkişinin kendi kontrolü | Görevlendirilmiş bilirkişi | Tek görev, kayıtlar, transkript, sorular ve rapor | Görev kontrol listesi ve bilirkişi onay olayı |
| B — Bağımsız dosya/rapor incelemesi | İkinci bilirkişi veya yetkili denetçi; gerektiğinde | Kaynak ses ve rapor arasındaki iz, işlemler, düzeltmeler, yanıtlar ve rapor sürümü | Salt okunur denetim paketi ve ayrı inceleme sonucu |
| C — MİHENK ürün denetimi | Ürün ekibi + bağımsız teknik, güvenlik, hukuk ve alan uzmanları | Yazılım, model/bağımlılık, güvenlik, kullanılabilirlik ve kabul testleri | Sürümlü kalite dosyası, test kanıtları, bulgu/risk kaydı |

Bu katmanlar aynı görev ekranında karıştırılmamalıdır. A ve B görev/rapor bağlamında, C ise ürün sürümü ve pilot kabulü bağlamında yürür.

## 2. Katman A — Bilirkişinin kendi görev ve rapor kontrolü

Tek Rapor ekranında rapor önizlemesinden ayrı bir **Görev Kontrolü** paneli bulunur. Bu panel belge biçim denetimi değildir; kaynaktan rapora kadar olan meslekî iş akışını tamamlamaya yardımcı olur.

### 2.1 Görev kapsamı ve materyal kontrolü

- Görevlendiren merci, dosya numarası, görevlendirme tarihi, süre ve inceleme kapsamı kaynak belgeyle karşılaştırılır.
- Görevlendirmedeki her soru ayrı satırda görünür; her biri için yanıt durumu ve dayanaklar gösterilir.
- Beklenen ve teslim alınan materyaller karşılaştırılır. Eksik, fazladan, okunamayan veya iade edilen materyal saklanır ve açıklaması görünür.
- Her materyal için dosya kimliği, orijinal dosya, byte boyutu, ölçülebilen teknik metadata ve hesaplanmış hash gösterilir. Hash, yalnızca ölçüm anındaki byte eşitliğini gösterir; sesin özgünlüğünü tek başına ispatlamaz.
- Görev başka bir görevin materyaline, transkriptine veya raporuna sessizce bağlanamaz.

### 2.2 Ses ve transkript kontrolü

- Her kaydın ASR işlem durumu ve uzman inceleme durumu ayrıdır.
- Makine taslağı ile uzman tarafından düzeltilmiş metin ayrıdır; ham çıktı üzerine yazılmaz.
- Kontrol kuyruğu nedenini açıklar: düşük model güven işareti, düşük ses, gürültü, üst üste konuşma, konuşma/metin boşluğu, kesilme veya elle işaretlenen aralık.
- Model işaretleri doğruluk yüzdesi gibi sunulmaz; bilirkişi her kaydı baştan sona dinleyebilir.
- Anlaşılamayan kısım “anlaşılamadı/belirsiz” kalabilir; sistem kelime tahminiyle kapatmaz.
- Konuşmacı etiketleri kayıt içi anonim gruplardır. Uzmanın düzeltme ve birleştirme işlemleri olay geçmişinde izlenir.
- Orijinal ses değişmeden korunur. Filtreleme/iyileştirme yalnız türetilmiş kopyada yapılır; hangi araç ve ayarın uygulandığı tutulur.
- Nihai transkriptin tüm kayıtları kapsadığı ve rapor dökümüne giren paragrafların uzman tarafından kontrol edildiği görünür olmalıdır. Kapsam dışı bırakılan aralıklar gerekçesiyle kaydedilir.

### 2.3 Rapor kontrolü

- Görevlendirmedeki bütün sorular, aynı sırada ayrı ayrı görünür ve yanıt alanına bağlanır.
- Her yanıtın dayanağı kaynak materyal, kayıt, zaman aralığı/segment, sayfa veya teknik ek gibi uygun konuma geri bağlanır.
- Yöntem ve teknik araçlar bölümüne yalnız gerçekten kullanılan motor/model ve sürüm otomatik aktarılır. Kullanılmayan bir araç rapora yazılmaz.
- Merci/dosya türü için seçilen rapor referans iskeleti, sürüm/tarih ve eşleştirme gerekçesi görünür.
- Raporun bütün A4 sayfaları, başlık/altbilgi, tablo, sayfa numarası, ekler, Türkçe karakterler ve imza alanı bilirkişi tarafından gözden geçirilir.
- Yanıtsız soru, kontrol edilmemiş rapora girecek transkript, kopuk dayanak veya doğrulanmamış çıktı formatı açık uyarı/engel olarak gösterilir.
- Son karar bilirkişidedir. MİHENK hiçbir otomatik kontrolü meslekî onay veya hukukî uygunluk sertifikası olarak adlandırmaz.

### 2.4 Bilirkişi kontrol sonucu

Kontrol sonucu en az şu durumlardan biri olmalıdır:

- **Tamamlandı:** Kontrol listesi gözden geçirilmiş ve bilirkişi son onayı kaydedilmiştir.
- **Uyarıyla tamamlandı:** Açıkça belirtilmiş sınırlılık veya çözülemeyen bölüm vardır; bilirkişi bunun raporda nasıl sunulduğunu teyit etmiştir.
- **Tamamlanamadı:** Kritik soru, kaynak, kayıt, materyal veya çıktı sorunu devam etmektedir.

MİHENK'in “kontrol tamamlandı” durumu bilirkişi imzası veya resmî teslim yerine geçmez. E-imza ve UYAP Portal işlemi bilirkişinin yetkili resmî süreçte yaptığı ayrı işlemlerdir.

## 3. Katman B — Bağımsız dosya/rapor incelemesi

Bağımsız incelemeyi yapacak kişi, bilirkişinin ana transkriptini veya raporunu doğrudan değiştirmemelidir. İnceleme ayrı bir kayıt ve ayrı sonuç üretir.

### 3.1 Denetim paketi

Bilirkişi, görev bağlamında **Denetim Paketi Hazırla** eylemiyle paketin içeriğini önizler. Paket varsayılan olarak dışarı aktarılmaz; kullanıcı hangi hassas dosya ve alanların dahil olacağını görür ve açıkça onaylar.

Denetim paketi, görevin türü ve hukuki/kurumsal gerekliliklere göre yapılandırılır; aşağıdaki öğelerden uygun olanları içerir:

1. Görevlendirme belgesi ve çıkarılan görev profilinin kaynak sayfa/alan bağlantıları.
2. Materyal envanteri, dosya kimlikleri, ölçülebilen teknik metadata, orijinal materyal hash'leri ve türev/orijinal ilişkisi.
3. Her ses dosyası için gerçek ASR motor/model adı, revision/sürüm, runtime/decoder sürümü ve gerçekten kullanılan parametreler.
4. Ham ASR çıktısı, uzman tarafından düzeltilmiş sürümler, değişiklik geçmişi ve belirsizlik işaretleri.
5. Segment kimlikleri, zaman aralıkları, konuşmacı etiketleri ve rapor paragraflarıyla eşleme.
6. Kullanılmışsa ses işleme/iyileştirme işlemi, işlenmiş kopya hash'i, araç sürümü ve parametreleri.
7. Görevlendirme sorusu → bilirkişi yanıtı → dayanak kaynağı bağlantı matrisi.
8. Rapor şablonu/referans iskelet adı ve sürümü, oluşturulan raporun revizyonu ve dışa aktarılan dosyanın hash'i.
9. Uygulama sürümü, modül sürümü, işlem zaman çizelgesi, yeniden denemeler ve hata/kurtarma olayları.
10. Bilirkişinin kendi kontrol sonucu ve rapor üzerinde verdiği son onay olayı.

Paketin kapsamı gereksiz kişisel veri ve hassas materyal taşımayacak biçimde sınırlandırılır. Paket hazırlanmadan önce kullanıcı içeriği görür; denetim amacı için zorunlu olmayan alanları çıkarmayı veya maskelemeyi değerlendirebilir. Hukukî/kurumsal saklama yükümlülüğü ayrıca doğrulanır.

### 3.2 Denetçi inceleme görünümü ve sonuç

İlk sürümde ayrı bir çok kullanıcılı denetçi hesabı vaat edilmez. İlk uygulanabilir biçim, yetkili bilirkişinin kontrollü olarak dışa aktardığı salt okunur pakettir. Denetçi kendi uygun ortamında kaynağa ve işlem izine bakar; inceleme sonucunu bağımsız bir rapor/tespit olarak verir.

İnceleme sonucu şu alanları içermelidir:

- İncelenen paket kimliği ve hash'i.
- İncelemeyi yapan yetkili/uzman, tarih ve kapsam.
- Kontrol edilen kayıtlar, zaman aralıkları, sorular ve rapor revizyonu.
- Uygun bulunan noktalar, eksiklikler, itirazlar ve açıklama istekleri.
- Sonuç: uygun / açıklama gerekli / yeniden inceleme gerekli / kapsam dışı.
- Denetçinin imzası ve kurumsal kayıt işlemi, MİHENK'in dışında ve yetkili usule göre.

Denetçi yorumu bilirkişinin orijinal kaydını veya raporunu değiştirmez. Bilirkişi bir değişiklik yaparsa yeni transkript/rapor revizyonu oluşturulur; önceki sürüm ve denetçi sonucu korunur. Denetim sonucuna göre yeni sürüm hazırlanmışsa yeni sürümün önceki denetimle ilişkisi açıkça gösterilir.

### 3.3 İzlenebilirlik ve değişiklik kaydı

- İşlem olayları görev, materyal, segment ve rapor kimliğiyle ilişkilendirilir.
- Her değişiklikte olay türü, önceki/yeni sürüm referansı, zaman ve işlemi yapan profil kaydı tutulur.
- Olay kaydı olağan kullanıcı düzenlemesiyle sessizce geriye dönük değiştirilemez. Bu beklenti uygulamada append-only kayıt tasarımı, bütünlük kontrolü, yedek/geri yükleme ve yetki testleriyle doğrulanmalıdır.
- Kriptografik imzalı veya hash-zincirli denetim izi ancak tasarım ve güvenlik testleri tamamlandığında iddia edilebilir; önceden “değiştirilemez” denmez.
- Denetim paketi, oluşturulduğu anda sabitlenmiş görev/rapor revizyonuna işaret eder. Sonradan yapılan değişiklikler eski paketi sessizce güncellemez.

## 4. Katman C — MİHENK ürününün kendi denetimi

MİHENK ekibinin kendi çalışmasını denetlemek için her sürümde bir **Ürün Kalite Dosyası** hazırlanır. Bu dosya vaka içeriğinden ayrıdır; GitHub'da yalnız sentetik test kimlikleri, test raporları ve hassas olmayan teknik özetler tutulur.

### 4.1 Sürüm bazında kalite dosyası

- Sürüm numarası, commit SHA, paket hash'leri ve hedef platform.
- Kapsam ve gereksinim → uygulama → test → kanıt eşlemesi.
- Birim, entegrasyon, E2E, çevrimdışı, güvenlik ve kullanılabilirlik testi sonuçları.
- Model, runtime, decoder ve üçüncü taraf bağımlılık sürümleri/lisansları; model dosyası hash'leri.
- ASR benchmark sonucu: insan referans metni, veri lisansı/izin durumu, WER/CER ve kritik kelime hata analizi; ölçüm koşulları ve donanım.
- Materyal bütünlüğü, görev yalıtımı, kasa/backup/restore, çökme kurtarma ve başarısız güncelleme kanıtları.
- UYAP Editör aç/kaydet/yeniden aç ve hedef evrak türü çıktı kabul kanıtı.
- Bilirkişi kullanılabilirlik denemesi ve rapor biçimi alan uzmanı değerlendirmesi.
- Bağımsız teknik/güvenlik/hukuk/meslekî inceleme bulguları.
- Açık hata, risk, istisna ve kabul edilmiş sınırlılıklar; sorumlu ve kapatma koşulu.

### 4.2 İç kalite kapısı

- Her gereksinim GEÇTİ / KALDI / ENGELLENDİ olarak kanıtla işaretlenir. Test edilmemiş bir özellik “GEÇTİ” olamaz.
- CI/derleme başarısı tek başına uygulama kabulü sayılmaz.
- Uzman kabulü, teknik test ve bağımsız güvenlik incelemesi ayrı imza/onay alanlarıdır.
- Açık kritik güvenlik veya görev/veri karışması bulgusu varken gerçek vaka pilotu başlatılmaz.
- Kritik olmayan kalan bulgular için kapsam, risk sahibi ve kapatma tarihi/kapısı kaydedilir.
- Ürün sahibi tasarım kabulü, bilirkişi meslekî kabulü veya hukuk/güvenlik uygunluk kararı yerine geçmez.

## 5. Wireframe ve uygulama yerleşimi

v0.5'in kabul edilen ana gezinme yapısı korunur:

- **Görev → Tek Rapor:** Katman A görev kontrolü, rapor önizleme ve “Denetim Paketi Hazırla” eylemi aynı görev bağlamında bulunur. Denetim, yeni ve karmaşık bir ana menüye dönüştürülmez.
- **Görev → Denetim Geçmişi:** Hazırlanan paketler, bilirkişi onayları, bağımsız inceleme sonuçları ve rapor revizyon ilişkileri gösterilir. İlk uygulama dilimi yalnız kayıt/önizleme olabilir; tam denetçi portalı bu sürümün zorunlu kapsamı değildir.
- **MİHENK geliştirme/CI alanı:** Ürün Kalite Dosyası kullanıcı görev ekranında gösterilmez; sürüm ve geliştirme yönetişiminde tutulur.

## 6. Uygulama aşamalarına ayırma

### Pilot öncesi zorunlu

1. Bilirkişinin görev/rapor son kontrol listesi.
2. Raporun kaynak, materyal, transkript, soru ve gerçek teknik araçlarla izlenebilirliği.
3. ASR ham çıktı/uzman sürümü ayrımı ve revizyon geçmişi.
4. Kullanılan motor/model/sürüm/parametre kaydının doğru olması.
5. Uygulama sürümü ve dışa aktarılan rapor revizyonunun belirlenmesi.
6. Ürün kalite dosyasında K-01–K-12 kanıtlarının durumu ve açık risklerin gösterilmesi.

### Kontrollü pilotta / ikinci dilimde

1. Denetim paketi dışa aktarımının gizlilik ve erişim kontrolüyle uygulanması.
2. Salt okunur denetçi incelemesi ve ayrı bulgu/yanıt dosyası.
3. Denetim paketi bütünlük doğrulaması ve rapor revizyonuyla ilişki.
4. Olay geçmişi bütünlüğünün bağımsız güvenlik incelemesi.

### Açık teknik doğrulama

- Denetim olay günlüğü için append-only depolama ve hash/bütünlük yaklaşımı.
- Denetim paketi şeması, imzalama ve uzun dönem okunabilirlik.
- Kişisel veri minimizasyonu, maskeleme, saklama ve aktarım koşulları.
- İkinci bilirkişi/denetçi rolü, erişim yetkisi ve denetim ortamı.
- UYAP/kurum iş akışlarında denetim dosyası veya eklerinin kabul koşulu.

## 7. Açık sınırlar

- MİHENK resmî bilirkişi denetim makamı veya yetkili hukukî denetçi değildir.
- Denetim paketi, elektronik imza veya resmî UYAP teslimi yerine geçmez.
- Hash, model güven puanı, test başarısı veya otomatik kalite göstergesi tek başına materyalin özgünlüğünü ya da raporun doğruluğunu kanıtlamaz.
- İkinci bilirkişinin inceleme sonucu kendi meslekî sorumluluğuyla ve yetkili usule göre düzenlenir.
- Gerçek vaka sesleri, raporları veya kişisel veriler GitHub issue/PR/CI/artifact içine konmaz.

---

**Tasarım kararı:** Bilirkişinin kendi kontrolü, bağımsız dosya/rapor incelemesi ve MİHENK ürün kalite denetimi ayrı katmanlar olarak tasarlanır. İlk UI diliminde rapor içi kontrol listesi ve izlenebilirlik önceliklidir; tam bağımsız denetçi hesabı/portal vaadi verilmez.
