# 56.12 – Türkçe Transkripsiyon ve Anotasyon Kuralları

> **Durum:** İlk referans anotasyon standardı önerisi; 56.12 uzmanı tarafından doğrulanmalıdır  
> **Tarih:** 13 Kasım 2026

## 1. Amaç ve sınır

Bu belge MİHENK 56.12 testlerinde ASR çıktılarının karşılaştırılabilmesi için insan referans transkriptinin nasıl hazırlanacağını tarif eder. Resmî bilirkişilik rapor formatı veya bağlayıcı bir adli transkripsiyon standardı olduğu iddia edilmez. Gerçek dosyalarda uygulanmadan önce 56.12 alan uzmanı ve hukuk/mahremiyet incelemesinden geçmelidir.

Temel ilke: **Referans, kayıtta duyulanı temsil eder; duyulmayanı tahmin etmez ve konuşmayı dilbilgisel olarak düzeltmez.**

## 2. Birbirinden ayrı tutulacak üç katman

1. **Kaynak ses:** Alınan orijinal kayıt ve teknik olarak gerekli salt okunur kopyası. Asla metin düzenleme veya normalizasyon amacıyla değiştirilmez.
2. **Sözcüğü sözcüğüne referans transkript:** Duyulabilen kelimeler, tekrarlar, dolgu ifadeleri, yarım kalan sözler ve belirsizlikler; kaynağın zaman aralıklarına bağlıdır. İnsan anotasyonunun esas çıktısıdır.
3. **Okunabilir sunum/rapor görünümü:** Uzman tarafından açıkça seçilmiş noktalama, biçim ve görev gereği sunum düzenlemeleri. Referans transkriptin üzerine yazmaz; hangi segmentlerden türetildiği izlenebilir olmalıdır.

MİHENK veya bir LLM, referans transkripti sessizce “düzeltip” temiz metin hâline getiremez. Her dönüştürülmüş görünüm ayrı sürüm ve işlem kaydı taşır.

## 3. Anotasyon birimi ve zaman kuralları

- Ana birim, tek konuşmacıya ait kesintisiz konuşma segmentidir.
- Her segment için kayıt başlangıcına göre start_ms ve end_ms tutulur.
- Zaman birimi tam sayı milisaniyedir; start_ms, end_ms değerinden küçük olmalıdır.
- İki konuşmacı üst üste konuşuyorsa iki ayrı segment saklanır; zaman aralıkları birbiriyle çakışabilir.
- Konuşmacı bilinmiyorsa speaker_label boş/null veya UNKNOWN olur. Tahmini konuşmacı atanmaz.
- Kaynakta ayrı kanal varsa channel_id konuşmacı etiketinden ayrı tutulur. Kanal kimliği otomatik olarak kişi kimliği değildir.
- Cümle/ifade segmenti ana referans birimidir. Kelime düzeyi zaman damgası, zaman hizalama testi için seçilmiş alt kümede ek anotasyon olarak hazırlanabilir.
- Zaman damgası toleransı test planında belirlenir; anotatörün tahmini milisaniye kesinliği iddia edilmez.
- Sesin başındaki sıfır zamanı ve kesit kullanılmışsa ana dosyaya ofset açıkça kaydedilir.

## 4. Söyleneni yazma kuralları

### 4.1 Sözcüğü sözcüğüne kayıt

- Duyulan kelimeler konuşulduğu sırayla yazılır.
- Kelime tekrarı, kendini düzeltme, yarım ifade ve cümle kesilmesi duyulabiliyorsa korunur.
- “Eee”, “ıı”, “şey”, “yani”, “hı hı” gibi dolgu/geri bildirimler, anotasyon politikasında kararlaştırılan biçimde korunur.
- Konuşmacının dilbilgisi, sözcük seçimi veya telaffuzu editör gibi düzeltilmez.
- Konuşmacının söylediği kelime başka bir kelimeye benzetilse dahi yalnızca bağlamdan hareketle değiştirilmez.
- Ağız/konuşma biçimi farklılığı için fonetik alfabe kullanılmaz; anlaşılır kelime, duyulan biçimi en iyi temsil eden tutarlı yazımla kaydedilir. Belirgin belirsizlik ayrıca işaretlenir.
- Konuşma başka bir dile geçerse duyulan ifade korunur; çevrilmez.

### 4.2 Noktalama ve büyük/küçük harf

- Noktalama işaretleri sesin kendisi değildir; okunabilirlik için anotatör tarafından eklenebilir.
- Noktalama, ASR'nin kelime hata oranını değiştirip yapay olarak yükseltmemesi için ana WER token karşılaştırmasından ayrı tutulur.
- Ham metin ve noktalama eklenmiş görünüm saklanır.
- Özel adlarda standart büyük harf yazımı uygulanabilir; bunun ses kanıtı değil, yazım katmanı olduğu bilinmelidir.

### 4.3 Sayılar ve tarihler

- Sözcüğü sözcüğüne katmanda konuşmacının söylediği biçim yazılır: “yirmi altı”, “iki bin yirmi altı”, “on üç Kasım” gibi.
- Konuşmacı rakam dizisini tek tek okumuşsa bu biçim korunur.
- Sayının rakamla yazıldığı ikinci bir gösterim gerekiyorsa bu, ayrı normalize katmanda yapılır.
- Sayının anlamı değişiyorsa veya birden fazla okuma mümkünse otomatik normalizasyon uygulanmaz.
- Telefon, dosya numarası, tarih, saat, miktar ve ölçü gibi kritik unsurlar WER'den ayrı hata sınıfları olarak ölçülür.

### 4.4 Özel adlar ve terimler

- Yalnızca sesin desteklediği ölçüde yazılır.
- Görev belgesinden veya internetten kişi/yer adını tahmin ederek belirsiz sesi tamamlamak yasaktır.
- Kısmen anlaşılabilen özel ad için duyulan parça korunur, geri kalanı belirsiz olarak işaretlenir.
- Anotatörün emin olmadığı sözcük, ses tekrar dinlenerek de çözülemiyorsa “anlaşılmayan bölüm” durumuna geçer.

## 5. Belirsizlik ve ses dışı olaylar

Aşağıdaki durumlar farklı sınıflar olarak saklanır:

| Durum | Gösterim | Metin alanı |
|---|---|---|
| Anlaşılır konuşma | speech | Duyulan sözcükler |
| Kısmen anlaşılabilir konuşma | partially_unintelligible_speech | Yalnızca kesin duyulan sözcükler; belirsiz aralık ayrı |
| Anlaşılmayan konuşma | unintelligible_speech | null; tahmin yok |
| Konuşma dışı sesli tepki | vocalization | Gülme, öksürme vb. olay etiketi |
| Çevresel/işitsel olay | audio_event | Kapı sesi, darbe, alarm vb. olay notu; konuşma metni değil |
| Üst üste konuşma | speech + ortak overlap_group_id | Her konuşmacının duyulabilen sözleri ayrı segmentte |

- “Anlaşılmıyor” etiketi, konuşmacının gerçekten söylediği bir kelime değildir. WER metnine kelime gibi eklenmez.
- Belirsiz aralıklar ana kelime hata hesabından çıkarılacaksa dışlanan süre ve oranı ayrıca raporlanır.
- Kısmen anlaşılabilen cümlede anlaşılır kelimeler silinmez; yalnızca çözülemeyen kısım belirsizlik olarak işaretlenir.
- Gülme veya öksürme, test anotasyon şemasında konuşma dışı olay olarak tutulur; uzman raporunun biçimine göre ayrıca sunulabilir.
- Çevresel ses, konuşma olarak ASR referansına eklenmez.

## 6. Konuşmacı etiketleme kuralları

- Etiketler kişi kimliği değil, yalnızca o kayıt içindeki konuşmacı kümeleridir.
- Her kayıt baştan numaralanır: SPK-01, SPK-02 vb.; ilk duyulma sırası esas alınır.
- Etiketler farklı kayıtlar arasında eşleştirilmez. Aynı kişinin farklı dosyalarda bulunabileceği varsayımıyla kimlik bağı kurulmaz.
- Kaydın bir bölümünde konuşmacı güvenilir biçimde ayrıştırılamıyorsa UNKNOWN kullanılır.
- Sesin tınısından yaş, cinsiyet, etnik köken, kimlik veya başka biyometrik özellik çıkarılmaz.
- Stereo/çok kanalda kanal bilgisi ayrıca yazılır; aynı kanalın tek kişi olduğu varsayılmaz.
- Diarization anotasyonu yapılırken ASR metin hatası ile konuşmacı atama hatası ayrı değerlendirilir.

## 7. İnsan anotasyon ve uzlaşma süreci

1. Test örneği anonim bir kimlik alır; anotatörlere model çıktısı gösterilmez.
2. İki anotatör kaydı birbirinden bağımsız dinleyerek transkript ve segment zamanlarını üretir.
3. Anotatörler sözcük, belirsizlik ve konuşmacı segmentlerinde uyuşmazlıkları işaretler.
4. Anlaşmazlıklar kaynak ses üzerinden birlikte incelenir; çözülemezse üçüncü yetkin değerlendirici/adjudikatör karar verir.
5. Referans sürümü kilitlenir ve checksum ile kaydedilir.
6. Model çıktıları ancak referans kilitlendikten sonra puanlanır.
7. Referansta sonradan düzeltme gerekiyorsa yeni sürüm yayımlanır; etkilenen bütün motorlar aynı yeni sürüme göre yeniden puanlanır.

Anotatörlerin model metnini önceden görmesi, modelin yanlış kelimesine yönlendirme/anchoring oluşturabilir. Bu nedenle referans hazırlama ve model değerlendirme aşamaları ayrılmalıdır.

## 8. WER/CER için Türkçe normalizasyon

Ham metinler değiştirilmeden saklanır. Puanlama için sürümlü ve tekrar üretilebilir normalizasyon uygulanır.

### 8.1 WER-TR-1 (ana kelime skoru)

- Unicode NFC uygulanır.
- Türkçeye uygun harf dönüşümü kullanılır: I → ı, İ → i. Genel dil bağımsız lower() davranışı varsayılmaz.
- Noktalama, puanlama kuralında kararlaştırılmış şekilde token karşılaştırmasından çıkarılır; ham metinde korunur.
- Fazladan boşluklar birleştirilir.
- ç, ğ, ı, ö, ş, ü gibi Türkçe harfler başka harflere dönüştürülmez.
- Kelime ekleri, olumsuzluk, kişi ve zaman ekleri silinmez.
- Kesme işareti ve kısaltma tokenizasyonu sürümlü kural ile sabitlenir. Kural test başladıktan sonra değiştirilmez.

### 8.2 WER-TR-2 (sayı/biçim ek normalizasyonu)

WER-TR-1'e ek olarak, yalnızca anlamı kesin eşdeğer olduğu tanımlanmış sayı/tarih/saat biçimleri kanonikleştirilebilir. Kullanılan sözlük ve kural sürümü raporlanır. WER-TR-2 ana WER skorunun yerine geçmez; ek karşılaştırma olarak gösterilir.

### 8.3 CER-TR-1

- Unicode NFC ve Türkçeye özel harf dönüşümü uygulanır.
- Boşluk ve noktalama politikası önceden sabitlenir.
- Türkçe harfler korunur; aksan/diakritik kaldırılarak anlamlı farklar silinmez.

### 8.4 Ayrı raporlanacak kritik unsurlar

- Kişi/kurum/yer adı.
- Sayı, tarih, saat, tutar ve ölçü.
- Olumsuzluk ve kip/eylem yönünü değiştiren ekler.
- Kısaltma ve harf harf okunan diziler.
- Görevde özel olarak sorulmuş kelime/ifadeler.

Bu unsurlar için WER yanında tür bazlı doğru/yanlış/kararsız sayısı tutulur. Kritik hata tek toplam puana gömülmez.

## 9. Zaman damgası doğrulama

- Referans zamanları kayıt başlangıcına göre milisaniye olarak saklanır.
- Kesit dosyası kullanıldıysa ana kaynak ofseti kaydedilir.
- Her segmentin başlangıç ve bitiş zamanı ayrı değerlendirilir.
- Sınır toleransı test başlamadan önce belirlenir; tüm modellerde aynıdır.
- Kelime düzeyinde hizalama varsa, otomatik forced alignment sonucu insan referansı olarak kabul edilmez; örneklem üzerinde dinlenerek kontrol edilir.
- Transkript satırına tıklayınca MİHENK'in açtığı zaman aralığı kaynak dosya ve segment kimliğiyle aynı olmalıdır.

## 10. Önerilen anotasyon kaydı

Makine tarafından okunabilir segment alanları için 56-12-anotasyon-kaydi-sablonu.json kullanılır. En az şu alanlar bulunmalıdır:

- recording_id: anonim örnek kimliği.
- source_audio_sha256: yerel test ortamında kaynak dosya hash'i; public test paylaşımında yalnız izin verilen açık veri için.
- annotation_policy_version: uygulanan anotasyon kuralı sürümü.
- segments: zaman aralığı ve konuşmacı etiketi taşıyan segmentler.
- segment_type, intelligibility, text_verbatim, overlap_group_id.
- annotator_id ve adjudication_status.
- normalization_profile: puanlama sırasında kullanılan profil.

Şablondaki örnek yalnızca kurgusal metindir; gerçek ses veya kişi bilgisi içermez.

## 11. Kalite denetimi

Referans kümesi kilitlenmeden önce:
- Sesin tamamının dinlenebilir olduğu doğrulanır.
- Boş veya süre dışı segment bulunmadığı kontrol edilir.
- Eşzamanlı konuşmaların örtüşme olarak korunduğu kontrol edilir.
- Anlaşılmayan bölümün kelime olarak tahmin edilmediği kontrol edilir.
- Konuşmacı etiketlerinin kayıt içinde tutarlı olduğu kontrol edilir.
- İki anotatör uyuşmazlıkları ve adjudikasyon gerekçeleri kaydedilir.
- Metin katmanları ve zaman damgaları kaynak ses ile örneklem bazında karşılaştırılır.
- Referans metinleri model çıktısına göre geriye dönük değiştirilmez.

## 12. Açık uzman kararları

1. Dolgu sesleri ve çok kısa geri bildirimlerin yazım biçimi.
2. Yarım kelime/kesilen söz için gösterim kuralı.
3. Noktalama ve büyük harf biçiminin rapor transkriptine etkisi.
4. Örtüşen konuşma segmentlerinin raporda gösterimi.
5. Zaman damgası için kelime mi, ifade mi, cümle mi temel alınmalı.
6. 56.12 görevlerinde sözcüğü sözcüğüne ve okunabilir sunum metninin hangi şartlarda birlikte sunulacağı.
7. Anlaşılmayan bölümün rapor ekinde gösterim biçimi.

Bu kararlar 56.12 uzmanıyla doğrulandıktan sonra standart sürümü yayımlanır. Önceki anotasyon sürümü silinmez; yeni sürüm değişiklik kaydıyla ilerler.
