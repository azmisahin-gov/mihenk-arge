# 56.12 – Kontrollü Ses Kayıt Protokolü ve Türkçe Metin Seti

> **Durum:** Sentetik/kontrollü test kaydı tasarımı; gerçek kayıt alınmadı  
> **Tarih:** 13 Kasım 2026  
> **İlgili belgeler:** [Test planı](56-12-test-plani-ve-basari-olcutleri.md), [test senaryoları](56-12-test-senaryolari.md), [veri kümeleri kaydı](56-12-veri-kumesi-kayitlari.md), [anotasyon kuralları](56-12-transkripsiyon-anotasyon-kurallari.md)

## 1. Amaç

Açık veri kümeleri okunmuş konuşma ve belirli doğal konuşma örnekleri sağlar; ancak 56.12 için ihtiyaç duyulan bütün koşulları tek bir kaynak karşılamaz. Bu protokol, MİHENK'in kendi kontrollü Türkçe test kayıtlarını nasıl tasarlayacağını tanımlar.

Bu metin bir kayıt oturumu talimatıdır; ses dosyası, insan anotasyonu veya model sonucu içermez. Gönüllü katılımcı, kayıt izni, saklama ve kullanım metinleri hukuk/mahremiyet incelemesinden geçmeden kayıt alınmamalıdır.

## 2. Test kayıtlarının veri sınıfları

| Sınıf | Açıklama | Ne için kullanılır? |
|---|---|---|
| SENTETİK-METİN | Kurgusal Türkçe cümleler ve diyalog yönlendirmeleri | Kontrollü telaffuz, ek, sayı, özel ad ve hata sınıfları |
| GÖNÜLLÜ-OKUMA | Katılımcının sentetik metni doğal hızında okuması | Referans metinli temiz konuşma ve dilsel zorluklar |
| GÖNÜLLÜ-DOĞAL | Katılımcıların kurgusal konu hakkında serbest konuşması | Dolgu kelimeleri, tekrar, kesinti, doğal hız ve diyalog |
| KONTROLLÜ-KARIŞIM | Aynı anda iki veya daha fazla gönüllünün konuştuğu gerçek akustik karışım | Diarization, örtüşme ve kısa araya girme |
| TÜREV-SES | İzinli temiz ana kayıttan üretilen kontrollü gürültü/codec/örnekleme kopyaları | Gürültü, telefon bandı ve dönüştürme regresyonu |

Metinlerin sentetik olması, sesin sentetik TTS olması anlamına gelmez. Öncelikli test, gerçek gönüllülerin kendi sesleriyle yaptığı kontrollü kayıttır. TTS ile üretilen sesler ayrı sentetik regresyon sınıfında tutulur.

## 3. Katılımcı, izin ve gizlilik

- Katılım gönüllü olmalı; kayıt, test, saklama, paylaşım ve varsa ticari kullanım kapsamı önceden açıkça bildirilmelidir.
- Katılımcının imzaladığı izin belgesi ses dosyasından ayrı ve erişim kontrollü saklanır; public depoya eklenmez.
- Test konuşmalarında gerçek kişi, dosya numarası, mahkeme adı, adres, telefon, e-posta, gerçek olay veya hassas bilgi kullanılmaz.
- Örnek adlar, kodlar ve yerler tamamen kurgusal olarak belirtilir.
- Anonim kayıt etiketi kullanılır; gerçek isim veya katılımcı kimliği manifest/log içine yazılmaz.
- Yaş, cinsiyet, etnik köken, biyometrik özellik veya başka demografik alanlar bu test için zorunlu değildir ve varsayılan olarak toplanmaz.
- Konuşmacı etiketleri her kayıt için yeniden SPK-01, SPK-02 biçiminde atanır; kayıtlar arası ses/kimlik eşleştirmesi yapılmaz.
- İzin kapsamı public paylaşımı açıkça içermiyorsa ses ve transkript public GitHub deposuna konulmaz.
- İzin iptali, saklama süresi, silme ve erişim geri alma süreçleri kayıt öncesinde belirlenir.

## 4. Kayıt düzeni

### 4.1 Temel ses formatı

Önerilen başlangıç ana kayıt:
- WAV kapsayıcı.
- PCM sıkıştırmasız.
- 48 kHz örnekleme.
- 24-bit örnek derinliği.
- Mikrofon ve kayıt cihazı modeli ile yazılım sürümünün kaydı.
- Otomatik gürültü azaltma, otomatik gain, echo cancellation ve voice enhancement kapalı; açılamayan işlevler ayrıca kayda alınır.

Bu öneri MİHENK'in test referans kaydına yöneliktir; bilirkişi dosyalarının özgün formatını dönüştürme talimatı değildir. Kaynak kaydın doğal formatı her durumda ayrıca korunur.

### 4.2 Tek konuşmacı

- Katılımcı, okuma metnini kendi doğal hızında seslendirir.
- Her cümle ayrı dosya olmak zorunda değildir; ancak cümle başlangıç/bitiş işaretleri kayıt notunda bulunur.
- Katılımcı hata yaparsa kaydı durdurup yeniden başlamak zorunda değildir; hatalı tekrar ve düzeltme olduğu gibi korunabilir.
- Metin okunurken kelime, noktalama veya sayı değiştirilirse anotatör metni değil, gerçekten söyleneni yazar.

### 4.3 İki konuşmacı ve gerçek akustik karışım

Diarization testinde ana test girdisi, iki kişinin sesinin aynı miks/mono kanalda gerçekten karıştığı kayıt olmalıdır.

Önerilen kurulum:
- Ortak ortam mikrofonu ile iki konuşmacının gerçek karışık sesi kaydedilir; bu dosya diarization motoruna verilecek ana girdidir.
- Mümkünse her katılımcı için ayrı referans mikrofon/kanal da kaydedilir. Bu izler, ana mix içindeki konuşma sınırlarının ve kimin ne söylediğinin insan anotasyonuna yardım eder.
- Bütün kayıt kanalları ortak saatle senkronize edilir.
- Ayrı mikrofon izleri saklanır ama tek kanal diarization testi yerine geçmez.
- Yalnızca bir stereo dosyanın sol kanalına bir, sağ kanalına diğer konuşmacıyı kaydetmek, tek kanala karışmış konuşma ile aynı test değildir.
- Konuşma üst üste geldiğinde iki konuşmacı da kendi sözünü sürdürür; anotasyon zaman aralıkları çakışır.

### 4.4 Kontrollü kayıt koşulları

Aynı metin/konuşma mümkün olduğunda aşağıdaki koşullarda ayrı kaydedilir:
- Sessiz oda, mikrofona yakın.
- Aynı oda, mikrofondan daha uzak.
- Kontrollü arka plan konuşması/gürültüsü.
- Yankılı ortam.
- Kontrollü telefon/VoIP bağlantısı.
- Fısıltı ve alçak ses.
- Hızlı fakat doğal konuşma.
- İki konuşmacı arasında kısa araya girme ve örtüşme.

Her koşulda mümkün olduğunca tek bir değişken değiştirilir. Örneğin hem uzaklık hem codec hem gürültü aynı anda değiştirildiğinde hangi unsurun hataya sebep olduğu anlaşılamaz.

### 4.5 Türev sesler

- Ana kayıt checksum ile sabitlenir ve salt okunur korunur.
- Gürültü ekleme, band sınırlama, yeniden örnekleme, codec dönüştürme, gain veya downmix yalnız türev çalışma kopyasında uygulanır.
- Her türev; kaynak dosya hash'i, işlem, araç/sürüm, parametre, tarih ve çıktı hash'i ile ilişkilendirilir.
- Türev ses, orijinal ana kayıt gibi etiketlenmez.
- Test için oluşturulmuş bir gürültülü/telefon kopyası, gerçek telefonla kaydedilmiş sesle aynı veri sınıfı olarak sunulmaz.

## 5. Kontrollü okuma metni paketi

Aşağıdaki cümleler yalnızca test metnidir. Bunlar gerçek kişi, kurum veya dava kaydı değildir. Ses kaydı alınırsa referans metni bu metne körü körüne eşitlenmez; katılımcının gerçekten söylediği biçim bağımsız anotasyonla doğrulanır.

| Kimlik | Test odağı | Kurgusal okuma cümlesi |
|---|---|---|
| OKU-001 | Türkçe harfler | Iğdır'dan İzmir'e giden araç, öğleden sonra Çınarlı durağında bekledi. |
| OKU-002 | I/İ ve kesme işareti | İpek, Kıvılcım-7 kodlu kaydı İzmir'de değil, Iğdır'da açtığını söyledi. |
| OKU-003 | Sayıların söylenişi | Toplam tutar bin iki yüz elli lira yetmiş beş kuruş olarak belirtildi. |
| OKU-004 | Rakam dizisi | Kayıt kodu KRM-4021; harfleri ve rakamları tek tek okuyorum. |
| OKU-005 | Tarih ve saat | Deneme oturumu on üç Kasım iki bin yirmi altı tarihinde saat dokuz kırk beşte başlayacak. |
| OKU-006 | Ondalık ve büyük sayı | Ölçüm sonucu sıfır virgül sıfır yedi değil, sıfır virgül yetmiş olarak okundu. |
| OKU-007 | Olumsuzluk | Bunu istemiyorum demedim; yalnızca bugün yapılmasını istemediğimi söyledim. |
| OKU-008 | Dilbilgisi eki | Dosyayı klasörlerden birine değil, klasörlerin hiçbirine kaydetmedim. |
| OKU-009 | Kısaltma | Deneme metninde T.C., UYAP ve PDF kısaltmaları ayrı ayrı geçiyor. |
| OKU-010 | Benzer sesli kelime | Yüz lira ile yüz sayfa aynı cümlede farklı anlamlarda kullanıldı. |
| OKU-011 | Tekrar | Hayır, hayır, önceki cümleyi değil, ondan sonraki cümleyi dinleyelim. |
| OKU-012 | Kendini düzeltme | Saat sekizde, hayır, saat sekizi on geçe başlayacağını söyledi. |
| OKU-013 | Dolgu ifadesi | Şey, bu dosyanın, yani ikinci dosyanın sonunda kısa bir sessizlik var. |
| OKU-014 | Yarım ifade | Eğer kayıt tamamlanmış olsaydı, belki de sonucu daha önce açıklardık… |
| OKU-015 | Harf harf kod | V-4-7 kodunu önce ve, sonra dört, sonra yedi diye okuyorum. |
| OKU-016 | Yabancı terim | Test raporunda gerçek zaman katsayısı ve word error rate ayrı gösterilecek. |
| OKU-017 | Sayı karşılaştırması | Birinci ölçüm on iki nokta altı; ikinci ölçüm on iki virgül altı olarak kaydedildi. |
| OKU-018 | Soru ve vurgu | Bu dosya mı eksik, yoksa yalnızca ek listesi mi güncellenmemiş? |

Bu paket Türkçe kelime/ek, sayı, tarih, olumsuzluk, kısaltma ve noktalama davranışını kapsayan başlangıç malzemesidir. Kapsamlı dil testi veya gerçek konuşmanın temsili olduğu iddia edilmez.

## 6. Doğal diyalog yönerge kartları

Katılımcılar aşağıdaki kurgusal konulardan birini seçerek 5–10 dakikalık serbest görüşme yapabilir. Bu süreler pilot kayıt tasarımı için öneridir; tüm görevlerde standart süre değildir.

### DIY-001 – Kurgusal teslimat planı

İki katılımcı, K-204 kodlu kurgusal bir paketin teslim saati ve teslim noktası üzerinde anlaşmaya çalışır. Biri saati yanlış hatırlar, diğeri düzeltir. Bir noktada kısa onay/geri bildirimler ve söz kesme doğal biçimde gerçekleşir.

### DIY-002 – Teknik sorun anlatımı

Bir katılımcı, çalışmayan kurgusal bir cihazı tarif eder. Diğeri sorular sorarak sorunun ne zaman başladığını, hangi adımların denendiğini ve hangi adımın işe yaramadığını öğrenir. Tekrarlar, kendini düzeltmeler ve belirsiz ifadeler doğal biçimde korunur.

### DIY-003 – İki seçenek arasında karar

Katılımcılar, kurgusal A-17 ve B-08 seçenekleri için tarih, saat, sayı ve koşul karşılaştırması yapar. Bir konuşmacı önce olumlu bir ifade kurup sonra düzeltir; diğeri itiraz eder veya aynı anda kısa bir söz ekler.

### DIY-004 – Rota ve zaman planı

Katılımcılar, hayalî iki yer arasında hareket planlar. Uydurma durak adları, saatler, sıra ve süreler kullanılır. Gerçek adres veya gerçek kişi bilgisi verilmez.

### DIY-005 – Karşılıklı anlatım

Her katılımcı kurgusal bir etkinliği anlatır. Diğeri araya kısa sorular, “hı hı”, “evet”, “yani” gibi geri bildirimler ekler. Konuşma akışı doğal olmalı; kelimeler belirli bir metne bağlı kalmamalıdır.

Anotasyon, yönerge kartının beklenen cümlelerini referans olarak kullanmaz. Gerçek ses bağımsız olarak yazıya geçirilir; yönerge yalnız konuşma konusunu tanımlar.

## 7. Örtüşme ve konuşmacı ayrımı alt testi

- İki gönüllü doğal konuşma sırasında kısa araya girme, eşzamanlı cevap ve birbirinin sözünü tamamlama örnekleri üretir.
- Ortak miks/mono kayıt diarization motoruna verilir.
- Ayrı mikrofon referansları anotatöre yardımcı olur; motor çıktısına kişi etiketi enjekte edilmez.
- Referans segmentler her kayıt içinde anonim SPK-01/SPK-02 ile etiketlenir.
- Eşzamanlı konuşmanın başlangıç/bitiş zamanları bağımsız anotasyonla işaretlenir.
- Konuşma tanınmıyorsa konuşmacı etiketi UNKNOWN olur.
- Kayıtlar arasında aynı sesin tekrar bulunup bulunmadığına dair kimlik eşleştirmesi yapılmaz.

## 8. Referans anotasyon ve split

- Okuma metninden bağımsız olarak katılımcının fiilen söylediği kelimeler iki anotatör tarafından yazılır.
- Doğal konuşmada dolgu, tekrar, yarım cümle ve düzeltmeler korunur.
- Anotatörler ASR modelinin çıktısını görmez.
- Uyuşmazlıklar adjudikasyon ile çözülür ve referans sürümü kilitlenir.
- Aynı katılımcı veya aynı görüşme oturumu train/test ya da development/test arasında bölünmez.
- Küçük pilot kayıtlarla genel nüfus veya uzman kullanıcı başarımı iddiasında bulunulmaz.
- Kayıt sayısı, konuşmacı sayısı ve alt grup dağılımı testin amacı ve kaynaklarına göre belirlenir; sayı dolsun diye aynı konuşmacıdan çok sayıda klip eklenmez.

## 9. Oturum sonunda kaydedilecek metadata

- Anonim recording_id ve session_id.
- Test veri sınıfı ve yönerge kartı kimliği.
- Kullanılan kayıt cihazı, mikrofon, yazılım ve format.
- Örnekleme hızı, bit derinliği, kanal sayısı ve codec.
- Kayıt koşulları: oda, yaklaşık mikrofon uzaklığı, gürültü profili ve bağlantı tipi.
- Gönüllü izin kaydının ayrı korumalı belgeye referansı; kimlik bilgisi yazılmaz.
- Kaynak dosya hash'i ve türevler.
- Anotasyon politika sürümü ve adjudikasyon durumu.
- Kısıtlar, teknik hatalar ve kaydın testte kullanılabilirlik kararı.

## 10. Başarı ve sınır

Bu protokol tamamlandığında MİHENK'in elinde:
- İnsan sesiyle okunmuş kontrollü Türkçe örnekler.
- Doğal tek konuşmacı ve ikili konuşma örnekleri.
- Tek miks/mono diarization girdisi.
- Ayrı referans kanalları ve insan referans anotasyonları.
- Gürültü/telefon/codec türevleri ve bunların işlem kayıtları

oluşturmak için tekrarlanabilir bir yöntem bulunacaktır.

Bu kayıtlar yalnızca test yöntemini değerlendirmek içindir. 56.12 uzmanlarının gerçek iş akışını veya tüm Türkiye Türkçesi çeşitliliğini temsil ettikleri iddia edilemez; böyle bir genelleme için farklı uzmanlar, konuşma koşulları ve ek veri gereklidir.
