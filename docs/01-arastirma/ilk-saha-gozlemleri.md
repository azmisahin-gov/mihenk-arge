# İlk Saha Gözlemleri — Görevden Rapor Teslimine İlk Uçtan Uca Test

> **Durum:** İLK GÖZLEM — bağımsız kullanıcı doğrulaması ve meslekî inceleme bekliyor  
> **Güncelleme:** 13 Kasım 2026  
> **Veri ilkesi:** Katılımcı profili, dosya bilgisi, gerçek kayıt ve ekran görüntüsü public belgede tutulmaz.

## 1. Kapsam ve kanıt düzeyi

Bu belge, proje sahibinin tek bir bilirkişiyle yaptığı örnek görev denemesi hakkındaki anlatımın anonimleştirilmiş sentezidir. Ham görüşme kaydı, birebir alıntı veya gerçek dava dosyası değildir. Tek kullanıcı ve tek görev tüm bilirkişileri temsil etmez. Bulgular, sonraki görüşmelerle sınanacak ilk gözlemler olarak değerlendirilmelidir.

İlk örnek görev 56.12 ses kaydını metne dönüştürme senaryosudur. Bu, MİHENK'in seçilmiş tek uzmanlık modülü veya MVP kararı değildir.

## 2. Gözlemlenen görev akışı

### 2.1 Görevlendirme ve fiziki teslim
1. Bilirkişi görevlendirmeyi UYAP Bilirkişi Portalında gördü ve portal üzerinden görevlendirmeyi kabul etti.
2. İlgili mahkeme daha sonra telefonla arayarak dosyanın fiziken teslim alınmasını bildirdi.
3. Bilirkişi fiziki dosyayı, ekleri ve USB belleği mahkemeden imza karşılığında teslim aldı.
4. Ofise döndüğünde dosya içindeki görevlendirme/talep bölümünü bulup okudu.
5. Dosyanın geri kalanının tamamını bu ilk inceleme sırasında envanterleyip tek tek okuduğu aktarılmadı; bu nedenle fiziksel dosyada hangi eklerin bulunduğu ile dijital ortama aktarılan materyalin tam eşleşmesi doğrulanmış değildir.

Bu gözlem, her belgeyi mutlaka baştan sona okumak gerektiği sonucunu doğurmaz. Ancak teslim alınan materyalin içerikleriyle birlikte listelenmesi, görev kapsamı ve yeterlilik değerlendirmesi için önemli bir kontrol noktasıdır.

### 2.2 USB'den çalışma kopyası alma
1. USB bellek fiziksel dosyanın içindeki bir zarf içerisinden çıkarıldı.
2. Bilgisayara takıldı ve içerik, kullanıcının belge klasörü altında açtığı görev klasörüne kopyalandı.
3. Kopyalama sonrasında USB tekrar zarfa yerleştirildi; fiziksel dosyanın geri kalanı yeniden incelenmedi.
4. USB'den sekiz ses dosyası çıktığı ve her birinin yaklaşık yirmi dakika olduğu, toplam sürenin yaklaşık 160 dakika olduğu bildirildi.

Bu anlatımda kopyalama sırasında hash alındığı, yazma koruması uygulandığı, dosya manifesti düzenlendiği veya kaynak ve kopya bütünlüğünün karşılaştırıldığı belirtilmedi. Bunların yapılmadığı kesinleştirilmiş değildir; sonraki görüşmede sorulmalıdır.

### 2.3 Önceki transkripsiyon örnekleriyle test
- Daha basit arayüzlü örnekte görev/dosya bilgisi girildi ve sekiz ses dosyası tek tek içeri alınarak transkripsiyon işlemleri başlatıldı. Kullanıcı her dosyanın işlemini bekledi.
- Daha kapsamlı eski örnekte de sekiz dosya ayrı ayrı işlendi; kullanıcı uygulamanın sunduğu gruplama üzerinden dinleme yaptı, hatalı kısımları düzeltti ve önemli bölümleri işaretledi.
- Kapsamlı örneğin ürettiği rapor kullanıcının beklentisini karşılamadı; daha düzenli ve göreve uygun bir rapor için önemli miktarda manuel düzenleme gerekti.
- Makine tarafından doğru görünen bölümlerin bile eksiksizliği kontrol edilmek istendiğinde kaydın yeniden dinlenmesi gerekiyordu. Sekiz kaydın toplamı yaklaşık 160 dakika olduğundan, bir tam dinleme ve bir tam tekrar dinleme 320 dakika (5 saat 20 dakika) saf oynatma süresine ulaşır. Tekrar edilen cümleler, duraklatmalar, not alma, düzeltme ve rapor yazımı bu süreye eklenir.
- Kullanıcı, anlaşılmayan bir cümleyi birkaç kez (örneğin beş kez) dinlemek zorunda kaldığını; fısıltı ve düşük sesin anlamayı zorlaştırdığını aktardı.
- Kullanıcının deneyiminde, bu işi kesintisiz sürdürmenin çok uzun bir çalışma günü gerektirebileceği, aralıklı sürdürülürse birkaç güne yayılabileceği belirtildi. Bu süre henüz bağımsız biçimde ölçülmüş bir performans metriği değildir.

### 2.4 Rapor hazırlama ve son kontrol
- Geleneksel süreçte konuşmalar UYAP Doküman Editörü veya başka bir belge düzenleyici içinde elle yazılabiliyor.
- Rapor, görevlendirme yazısındaki talep ve sorulara göre düzenleniyor; önemli görülen konuşma bölümleri hâkimin bulguyu kolay bulabilmesi için işaretleniyor.
- Kullanıcı, önceki davadan kalan bilgi riskini azaltmak için her görevde yeni rapor belgesi oluşturmayı tercih ettiğini; hazır şablon/kopyalama kullanıldığında eski dosyaya ait bilgi kalabilmesinden endişe ettiğini aktardı.
- Bu testte sistematik bir son kontrol listesi kullanılmadığı bildirildi.
- Rapor dışa aktarma ve dosyaya yükleme öncesinde, belge düzeni, görev sorularının cevaplanması, eklerin eşleşmesi ve eski dosyadan kalmış alanlar için güvenilir bir kontrol kapısı ihtiyacı ortaya çıktı.

## 3. İlk problem hipotezleri

1. **Görev ve materyal envanteri kopukluğu:** Fiziki dosya, ekler ve USB içeriği ayrı kaynaklardan gelir. Teslim alınan her materyalin listesi, içeriği ve inceleme durumu birbirine bağlanmazsa eksik dosya gözden kaçabilir.
2. **Tek işlem değil, uçtan uca iş yükü:** Transkripsiyon başarılı olsa dahi sesin doğrulanması, önemli bölümlerin seçilmesi, raporun göreve göre hazırlanması ve teslim kontrolleri tamamlanmış olmaz.
3. **Uzun doğrulama süresi:** Makine çıktısı kullanıcının dinleme yükünü ortadan kaldırmıyor; yanlış güven oluşmadan, dinleme ve düzeltme işinin daha izlenebilir ve hızlı yürütülmesi gerekiyor.
4. **Raporun dosyaya özgü hazırlanması:** Şablon seçimi, zorunlu alanlar ve eski görevden bilgi kalması riski otomatik biçim/tamlık kontrolleri için aday problem alanıdır.
5. **Önemli bölümün bulunabilirliği:** İşaretlenen her alıntı kaynak ses dosyasına ve zaman konumuna geri bağlanmalıdır; bağlamdan kopuk seçki yeni hata riski doğurabilir.
6. **Kurulum ve ilk kullanım:** Daha önce tanınmayan uygulamanın indirilmesi, kurulması ve ilk kez çalıştırılması ürün deneyiminin parçasıdır.
7. **Kontrol listesi kullanmama:** Kullanıcı testinde sistematik kontrol listesi kullanılmadığı aktarılmıştır. Resmî bilirkişi kontrol listelerinin uygulamada hangi sıklıkta ve nasıl kullanıldığı ayrıca doğrulanmalıdır.

## 4. Ortak çekirdek için aday ihtiyaçlar

- Görev ve süre kaydı; görev kapsamı ve soruların açıkça saklanması.
- Fiziki/dijital teslim kaynağı, tarih ve teslim/iade bilgisi.
- Fiziki evrak, ek ve dijital materyal envanteri.
- Beklenen materyal ile alınan/aktarılmış/işlenmiş materyalin karşılaştırılması.
- Orijinal, çalışma kopyası ve türetilmiş çıktı ayrımı.
- Dosya özeti, hash, format/okunabilirlik ve kötü amaçlı dosya kontrolü.
- Her materyal için durum: alınmadı, envanterlendi, işleme hazır, inceleniyor, incelendi, kapsam dışı bırakıldı, sorunlu.
- Göreve/mahkemeye uygun rapor şablonu ve zorunlu alan kontrolü.
- Rapor bölümleri, ekler ve kaynak materyal arasında izlenebilir ilişki.
- Eski görevden kalmış metin/alan/ek riskini azaltan temiz belge üretimi.
- Son kontrol listesi ve kullanıcı tarafından yapılan resmî teslimin doğrulanması.

Bunlar ortak ürün adaylarıdır; MVP özelliği olarak kesinleştirilmemiştir.

## 5. 56.12'ye özgü olabilecek ihtiyaçlar

- Birden fazla ses kaydını tek görevde toplu içe alma ve dosya başına işlem durumu.
- Kaynak sesle eş zamanlı metin gösterimi, zaman damgasına atlama, bölümü döngüde dinleme ve oynatma hızı kontrolü.
- Anlaşılmayan, fısıltılı, örtüşen veya gürültülü bölümü açıkça işaretleme.
- Makine taslağı, uzman düzeltmesi ve nihai kabul edilen metni ayrı tutma.
- Kişileri tanımlamadan, ayırt edilebilen ses sıralarına nötr “Konuşmacı 1”, “Konuşmacı 2” gibi etiketler verme.
- Konuşmacı ayrımı yapılamayan veya seslerin üst üste geldiği bölümleri “belirsiz/örtüşen konuşma” olarak işaretleme.
- Önemli bölümleri kaynak dosya ve başlangıç/bitiş zamanına bağlama.
- Her kayıt için uzman inceleme ve kabul durumunu ayrı gösterme.

Konuşmacı etiketi kişinin gerçek kimliğini, cinsiyetini, yaşını veya çocuk/yetişkin olduğunu kanıtlamaz. Bu tür nitelendirmeler otomatik çıkarım olarak rapora eklenmemelidir. Konuşmacı karşılaştırması/kimlik tespiti ve sesin özgünlüğü/manipülasyon incelemesi, transkripsiyondan ayrı uzmanlık ve yöntem gerektirebilir.

## 6. Otomasyon sınırı

| İş | İlk değerlendirme | İnsan rolü |
|---|---|---|
| Görev ve dosya alanı açma | Kullanıcı girişiyle otomatik | Görev bilgisini doğrular |
| Teslim edilen materyal ve içerik envanteri | Dosya listesini otomatik çıkarma; fiziksel teslimi kullanıcı kaydeder | Envanterin dosyayla eşleştiğini onaylar |
| Dosya sayısı, format, süre, boyut, okunabilirlik, hash | Deterministik otomasyon | Uyarıları/istisnaları değerlendirir |
| Orijinal ve çalışma kopyası oluşturma | Onaylı, izlenebilir işlem | Yöntem ve çalışma kopyasını onaylar |
| Ses transkripsiyonu | Makine taslağı | Kaydı dinler, düzeltir ve kabul eder |
| Zaman damgası ve konuşmacı sırası | Sistem önerir/etiketler | Yanlış etiket ve belirsizliği düzeltir |
| Önemli bölüm seçimi | Sistem arama/işaretleme yardımı sunabilir | Neyi rapora alacağına uzman karar verir |
| Rapor şablonu ve alan kontrolleri | Kural tabanlı otomasyon | Doğru şablonu ve içeriği onaylar |
| Konuşmacı kimliği, ses karşılaştırması, özgünlük/manipülasyon kanaati | Otomatikleştirilmemeli | Görev kapsamına uygun uzman |
| Nihai teknik kanaat ve rapor onayı | Otomatikleştirilmemeli | Bilirkişi |
| UYAP'a resmî gönderim ve fiziki iade | Yetkili entegrasyon olmadan otomatikleştirilmemeli | Bilirkişi |

## 7. Başlıca riskler

- Fiziki dosya, ek ve USB içeriği arasında envanter eşleşmesinin kurulmaması.
- USB içeriği kopyalanırken kaynak/kopya bütünlüğünün ve işlem adımlarının kaydedilmemesi.
- İlk alınan hash'in geçmişteki düzenleme/manipülasyonu kanıtladığının sanılması.
- Makine transkriptinin doğru kabul edilmesi veya düşük güven skorunun tüm hataları yakaladığı varsayımı.
- Uzmanın uzun kayıtları ikinci kez dinlemek zorunda kalması; yorgunluk ve dikkat kaybı.
- Konuşmacı etiketi ile gerçek kişi kimliğinin karıştırılması.
- Sesin özgünlüğü veya montajı hakkında yetki/yöntem dışı sonuç yazılması.
- Yanlış rapor şablonu seçimi ya da önceki görevden kalan ad, tarih, dosya numarası ve eklerin yeni rapora sızması.
- Otomatik kontrol listesinin mesleki incelemenin tamamlandığı garantisi gibi algılanması.
- Gerçek vaka verisinin public depo, telemetri, log veya haricî servise çıkması.

## 8. Sonraki doğrulama adımları

1. Fiziki teslimde mahkemenin verdiği envanter/listenin bulunup bulunmadığını ve uzman tarafından nasıl saklandığını sor.
2. USB'de görülen dosyalar ile fiziki dosyada belirtilen eklerin nasıl eşleştirildiğini öğren.
3. Kopyalama anında hangi araç/işlem kullanıldığını, hash veya yazma koruması uygulanıp uygulanmadığını sor.
4. Sekiz dosyanın hepsinin görev kapsamına girip girmediğini, dosya başına dinleme/düzeltme/rapor süresini ayrı ölç.
5. Hangi rapor şablonunun seçildiğini, hangi bölümlerin görev için zorunlu olduğunu ve dosyaya özel hangi içeriklerin üretildiğini öğren.
6. Konuşmacı etiketlerinin mevcut meslekî yöntemde nasıl verildiğini, kimlik ve ses karşılaştırmasının görev kapsamına girip girmediğini sor.
7. Son kontrol listesi kullanılmamasının alışkanlık, zaman baskısı veya uygun şablon/araç eksikliği kaynaklı olup olmadığını ayır.
8. Farklı bir uzmanlık alanından en az bir kullanıcıyla ortak çekirdek ihtiyaçlarını sınamaya çalış.

## 9. Notların yayımlanması

Public depoda katılımcı adı, kurum, sicil, tam uzmanlık/deneyim kombinasyonu, dosya numarası, gerçek ses, evrak, hash manifesti veya UYAP ekran görüntüsü tutulmaz. Tek katılımcı kodu da tek başına anonimlik sağlamaz. Yalnızca yeniden kimliklendirme riski azaltılmış, genelleştirilmiş bulgular yayımlanır.
