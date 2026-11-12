# İlk Saha Gözlemleri — Tek Uzmanla Görev Testi

> **Durum:** İLK GÖZLEM — bağımsız kullanıcı doğrulaması bekliyor  
> **Güncelleme:** 13 Kasım 2026  
> **Veri ilkesi:** Katılımcı kimliğini/profilini açığa çıkarabilecek ayrıntılar bu public belgede tutulmaz.

## Kapsam ve kanıt düzeyi

Bu not, proje sahibinin tek bir bilirkişiyle yaptığı ilk deneme ve ekran incelemesi hakkındaki anlatımının genelleştirilmiş sentezidir. Katılımcıyla yapılan ham görüşme kaydı veya birebir alıntı değildir. Proje sahibinin yorumu ile bilirkişinin doğrudan ifadesi her noktada ayrışmadığından, aşağıdaki bulgular **ilk gözlem/hipotez** olarak ele alınmalıdır. Tek kişi ve tek görev tüm bilirkişileri temsil etmez.

İlk örnek görev, resmî listede 56.12 olarak tanımlanan ses kaydını metne dönüştürme senaryosudur. 56.12'nin resmî istisnası ve 56.11'den farkı ayrıca korunmalıdır.

## Deneme sırasında aktarılan deneyim

### Önceki örnek uygulamalarla test
- Uygulamaları ilk kez indirip çalıştırma adımı, daha önce tanınmayan masaüstü uygulamasıyla karşılaşınca beklenenden daha fazla açıklama/rehberlik gerektirdi.
- Daha basit arayüzlü ikinci örnekte bir çalışma oluşturup ses dosyasını metne dönüştürmek kolay bulundu.
- Ancak üretilen metin, UYAP'a teslim edilecek raporun kendisi değildi. İçeriğin UYAP Doküman Editörü ve ilgili rapor yapısına aktarılması, düzenlenmesi ve eklerle tamamlanması ek manuel iş yarattı.
- Önceki daha kapsamlı örnekte dinleme ve hızlı düzeltme gibi yararlı etkileşimler bulunduğu; buna karşılık kullanımın daha ağır/karmaşık olduğu ve çıktının yine uzman tarafından düzenlenmesi gerektiği aktarıldı.

Bu iki eski uygulama yalnızca geçmiş kullanıcı deneyimi için referanstır. MİHENK'e kod, mimari, veri modeli, bağımlılık veya bileşen taşınmayacaktır.

## İlk problem hipotezleri

1. **Kurulum ve ilk kullanım:** Tanınmayan uygulama, kurulum ve ilk çalıştırma eşiğinde kullanıcıyı kaybedebilir. İndirme, kurulum, ilk açılış, cihaz gereksinimi ve hata mesajları ürünün parçasıdır.
2. **Tek işlev yerine görev bütünlüğü:** Transkripsiyon gibi tek bir işlem başarılı olsa bile bilirkişinin işi raporun resmî biçime hazırlanması ve portal teslimine kadar bitmez.
3. **Materyal yoğunluğu:** Çok sayıda dosyada dosya envanteri, doğru materyalle çalışma, odaklanma ve gözden kaçırma riski önem kazanabilir.
4. **Rapor hazırlama:** Makine çıktısını rapor şablonuna, açıklamalara, yöntem/araç bilgisine ve eklere dönüştürmek ayrı bir iş yükü olabilir.
5. **Son kontrol:** Hazırlanmış raporda eksik alan, ek, görev sorusu, dosya referansı ve teslim kontrolü için sistematik bir kontrol kapısı değer yaratabilir.
6. **Karmaşıklık:** Daha çok özellik, otomatik olarak daha iyi deneyim değildir. Kullanıcıyı adım adım yönlendiren, gereksiz kararları azaltan akış gerekir.

## Ortak çekirdek için aday ihtiyaçlar

- Görev/proje alanı ve manuel görev bilgisi.
- Materyal/evrak envanteri ve teslim kaynağı.
- Dosya bütünlüğü, orijinal-kopya ayrımı ve işlem geçmişi.
- Görev türüne göre yapılandırılabilir iş akışı ve kontrol listesi.
- İnceleme notları, taslak ve eklerin ilişkilendirilmesi.
- Raporun biçimsel/tamlık kontrolleri.
- İnsan tarafından yapılması gereken son kontrollerin görünür listesi.
- Dışa aktarma ve resmî portala kullanıcı tarafından yükleme adımları.
- Yedekleme, geri yükleme ve yerel veri güvenliği.

Bunlar doğrulanmış MVP özellikleri değil; farklı uzmanlık alanlarında test edilecek ortak ihtiyaç adaylarıdır.

## 56.12 senaryosuna özgü olabilecek ihtiyaçlar

- Ses dosyalarını envanterleme ve oynatıcıdan inceleme.
- Zaman konumuna bağlı transkript taslağı ve düzeltme.
- Anlaşılamayan/emin olunmayan bölümleri açıkça işaretleme.
- Makine çıktısı ile bilirkişinin düzelttiği/nihai kabul ettiği metni ayırma.
- Kaynak ses, transkript, düzeltme ve rapor arasındaki izlenebilir ilişki.
- Birden fazla kayıt için toplu çalışma ve her kayıt için ayrı kalite durumu.

Bu liste, başka uzmanlık modüllerine otomatik olarak uygulanamaz. Sesin kimliğini, özgünlüğünü, montajı veya görüntüyü incelemek 56.12 transkripsiyon işiyle aynı kabul edilmemelidir.

## Otomasyon sınırı

| İş | İlk değerlendirme | İnsan rolü |
|---|---|---|
| Dosya listesi, türü, boyutu ve okunabilirlik kontrolü | Deterministik otomasyona uygun | Uyarı ve istisnayı inceler |
| Hash, kopya ve orijinal/çalışma ayrımı | Deterministik otomasyona uygun | Teslim kaynağı ve zinciri doğrular |
| Gerekli alan/ek/format kontrolü | Kural tabanlı otomasyona uygun | Görev için doğru kural/şablonu onaylar |
| Transkripsiyon | Makine destekli taslak üretimi | Dinler, düzeltir, kabul eder/reddeder |
| Belirsiz ses bölümü | Sistem işaretleme ve önceliklendirme yapabilir | Teknik değerlendirme ve nihai metin uzmanda |
| Rapor düzeni | Şablon ve tamlık yardımı | İçerik, yöntem ve sonuç değerlendirmesi uzmanda |
| Nihai teknik kanaat/kanıt yorumu | Otomatikleştirilmemeli | Tamamen bilirkişinin sorumluluğunda |
| E-imza ve UYAP teslimi | Yetkili resmî entegrasyon olmadan otomatikleştirilmemeli | Bilirkişi portalda imzalar/gönderir ve doğrular |

## Başlıca riskler

- Transkriptte kelime, isim, sayı, tarih veya konuşmacı hatası.
- Makine güven puanının gerçek doğruluk veya hukuki yeterlilik sanılması.
- Yanlış dosya/kopya üzerinde çalışma veya orijinal materyalin değişmesi.
- Çok dosyalı görevde eksik materyal, tekrar veya yanlış eşleştirme.
- Rapor şablonunun görev türü/yargı birimi için yanlış seçilmesi.
- Otomatik kontrol listesinin “inceleme eksiksizdir” garantisi gibi algılanması.
- Yetkisi doğrulanmamış UYAP otomasyonu.
- Bulut/haricî servis kullanılırsa dosyanın cihaz dışına aktarılması.

## Sonraki doğrulama adımları

1. Aynı kullanıcıyla gerçek bir görevi hassas dosya içeriği paylaşmadan baştan sona süreç adımları şeklinde yeniden haritala.
2. Hangi işlemlerin UYAP'ta, hangilerinin masaüstü uygulamada, hangilerinin UYAP Doküman Editörü/diğer ofis araçlarında yapıldığını tek tek ayır.
3. Raporun hangi resmî şablon ve dosya biçimiyle teslim edildiğini güncel yetkili kaynaktan doğrula.
4. Birden fazla dosya ve fiziksel materyal kabulünde hangi kayıtların tutulduğunu öğren.
5. Mümkün olduğunda ikinci bir bilirkişiden, farklı uzmanlıkta benzer görev yaşam döngüsünü al.
6. Katılımcı ifadesi, ekran gözlemi ve proje sahibinin yorumunu her yeni notta ayrı tut.

## Notların yayımlanması

Bu public depoda katılımcı adı, kurum, sicil, kimlik, kesin uzmanlık/deneyim kombinasyonu, dosya numarası, gerçek ses, evrak veya ekran görüntüsü tutulmaz. Tek katılımcı kodu da tek başına anonimlik sağlamaz. Yalnızca yeniden kimliklendirme riski azaltılmış, genelleştirilmiş bulgular yayımlanır.
