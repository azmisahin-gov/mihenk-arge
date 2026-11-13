# 56.12 – Test Veri Kümesi Kataloğu ve Manifest Yönetimi

> **Durum:** Araştırma/kayıt tasarımı; veri kümeleri henüz MİHENK test deposuna alınmadı  
> **Tarih:** 13 Kasım 2026  
> **İlişkili belgeler:** [Test Planı ve Başarı Ölçütleri](56-12-test-plani-ve-basari-olcutleri.md), [Anotasyon ve Referans Protokolü](56-12-anotasyon-ve-referans-protokolu.md)

## 1. Amaç

Bu belge, MİHENK 56.12 değerlendirmesinde kullanılabilecek Türkçe ses veri kaynaklarını ve her kaynağın sınırlamalarını kaydeder. Kaynak listesinin bulunması, veri kümesinin indirildiği, kullanıldığı, lisansının tüm amaçlar için onaylandığı veya MİHENK'e dahil edildiği anlamına gelmez.

Veri kaydı iki katmanda tutulur:

1. **Kamuya açık kaynak kataloğu:** Veri kümesi adı, yayıncı, kaynak bağlantısı, sürüm, beyan edilen lisans, erişim koşulu, kullanım amacı ve sınırlama. Gerçek ses, transkript, yerel dosya yolu, konuşmacı anahtarı veya dosya özeti içermez.
2. **Korumalı yerel örnek manifesti:** İzinli test ortamında kullanılan her örneğin yerel kimliği, dosya özeti, korumalı konumu, anotasyon sürümü, split/grup token'ı ve test çalıştırmalarıyla ilişkisi. Bu dosya public GitHub'a, CI loglarına veya rapor eklerine konmaz.

Kamuya açık manifest için JSON Schema ve boş şablon:
- [Manifest şeması](../../../../templates/56-12-test-veri-manifesti.schema.json)
- [Manifest şablonu](../../../../templates/56-12-test-veri-manifesti-sablonu.json)

## 2. Veri kaynağı değerlendirmesi

### 2.1 Mozilla Common Voice – Turkish 27.0

- Mozilla Data Collective kataloğunda “Common Voice Scripted Speech 27.0 – Turkish”, Türkçe dili, ASR görevi, MP3 biçimi ve CC0-1.0 lisansıyla listeleniyor.
- Temel niteliği, gönüllülerin önceden yazılmış cümleleri okumasıdır.
- **Önerilen rol:** Temiz/okunmuş Türkçe konuşmada başlangıç ASR karşılaştırması.
- **Sınırlamalar:** Doğal mahkeme/telefon diyaloğu, örtüşen konuşma, fısıltı veya serbest konuşma performansını tek başına temsil etmez. Modelin eğitim verisiyle konuşmacı/veri çakışması ihtimali ayrıca incelenmelidir.
- **Bölme kuralı:** İndirilen sürümün kendi train/validation/test ayrımı aynen kaydedilir. Nihai test bölmesi model/parametre seçimi için kullanılmaz.
- **Kullanım notu:** Veri kartının ve güncel indirme sayfasının sürüm/lisans bilgisi snapshot tarihinde tekrar kaydedilir; CC0 kaydı konuşmacı kimliklendirmesi veya biyometrik çıkarım için izin olarak yorumlanmaz.

Kaynak: [Mozilla Common Voice veri kataloğu](https://commonvoice.mozilla.org/bas/datasets).

### 2.2 Google FLEURS – Türkçe (tr_tr)

- Hugging Face veri kartında lisans CC BY 4.0 olarak listelenir.
- FLEURS, birden fazla dilde paralel/okunmuş cümlelerden oluşur; Hugging Face yükleme belgeleri dil konfigürasyonu ve train/valid/test bölmelerini gösterir.
- Türkçe yapılandırma tr_tr olarak kaydedilmelidir; indirilen gerçek revision ve split istatistikleri snapshot sırasında doğrulanır.
- **Önerilen rol:** Kontrollü/okunmuş konuşma için ASR karşılaştırması ve model değerlendirme hattının tekrarlanabilirliğini sınama.
- **Sınırlamalar:** Okunmuş cümle başarısı doğal diyalog başarısı değildir. CC BY 4.0 atıf koşulları korunmalıdır.
- **Bölme kuralı:** Resmî test bölmesi kilitli değerlendirme için ayrılır; model ayarı ve geliştirme için kullanılmaz.

Kaynak: [Google FLEURS veri kartı](https://huggingface.co/datasets/google/fleurs).

### 2.3 MediaSpeech – Türkçe

- Veri kartı Arapça, Fransızca, İspanyolca ve Türkçe için dil başına yaklaşık 10 saat medya konuşması bulunduğunu söyler.
- Kısa bölümler YouTube üzerinde bulunan medya videolarından otomatik çıkarılmış ve elle transkribe edilmiştir; kartta CC BY 4.0 beyanı bulunur.
- Görüntülenen Hugging Face yapısında tek train bölmesi gösterilir; Türkçe yapılandırmasının gerçek revision/split yapısı indirme öncesi doğrulanmalıdır.
- **Önerilen rol:** Yayın/medya tarzı konuşmada ikincil, alan dışı dayanıklılık testi.
- **Sınırlamalar:** Medya konuşması bilirkişi ses kaydı ile aynı akustik koşul değildir. Kaynağın video/ses kökeni ve dağıtım koşulları ayrıca incelenmelidir. Tek train bölmesi varsa bunu doğrudan model seçimi için tarafsız test kümesi saymak doğru değildir.
- **Bölme kuralı:** Kaynak kayıt/video/konuşmacı bazında sızıntısız ayırma mümkün değilse yalnız keşif amaçlı kullanılır; nihai kilitli test skoruna dahil edilmez.

Kaynak: [MediaSpeech veri kartı](https://huggingface.co/datasets/ymoslem/MediaSpeech).

### 2.4 Real-TurnTurk

- Kaynak kartı Apache 2.0 lisansı, altı doğal iki kişilik görüşme, altı konuşmacı, yaklaşık 1,94 saat toplam görüşme süresi, zaman hizalı transkript ve konuşma etkinliği anotasyonları bildirir.
- Her katılımcı ayrı kanalda kaydedilmiştir; kaynak açıklaması, bu sayede konuşmacı atamasının kanal üzerinden doğrudan anlaşılabildiğini ve diarization modeline gerek olmadığını belirtir.
- Veri kümesi ayrıca yüz/baş/göz gibi görüntüden türetilmiş özellikler içerir.
- **Önerilen rol:** Zaman hizası, konuşma etkinliği (VAD), konuşma sırası ve geri bildirim segmentleri için sınırlı yardımcı test.
- **Diarization sınırı:** Ayrı kanal kaydı, tek kanalda karışmış iki veya daha fazla konuşmacının diarization değerlendirmesi değildir. Kanallar birleştirilerek sentetik karışım üretilirse test “sentetik karışım” diye işaretlenmelidir.
- **Gizlilik/amaç sınırı:** MİHENK 56.12 testinde yüz özellikleri ve görüntü dosyaları kullanılmaz. Kişi eşleştirme veya kimlik çıkarımı yapılmaz. Ses ve transkriptin kullanım koşulları ayrıca değerlendirilir.
- **Lisans uyuşmazlığı:** TurkASR-Bench içindeki Real-TurnTurk satırı CC BY 4.0 gösterirken özgün Real-TurnTurk kartı Apache 2.0 gösteriyor. Kaynak sahipleri bu farkı açıklamadan alt küme için toplulaştırılmış lisans varsayımı yapılmaz.

Kaynak: [Real-TurnTurk veri kartı](https://huggingface.co/datasets/tugrulbayrak/Real-TurnTurk).

### 2.5 TurkASR-Bench

- Veri kartı yedi kaynaktan toplam 5.200 ifade ve 14,7 saatlik, kaynak bazında dengelenmiş bir ASR test seti bildirir.
- Sesler 16 kHz mono FLAC'a standardize edilmiştir.
- Her kaynak kendi lisansını korur; genel lisans mixed-per-source olarak belirtilir. Erişim için koşulların kabul edilmesi gerekir.
- Khan Academy alt kümesi CC BY-NC-SA 3.0 ve ticari olmayan; VoxForge alt kümesi GPL-3.0 olarak listelenmiştir. Bu alt kümeler ticari kullanım veya yeniden dağıtım açısından otomatik olarak uygun kabul edilemez.
- Veri kartı bazı referanslarda muhtemel yazım hataları olduğunu ve bunların elle doğrulanmadığını belirtir. Kaynağın İngilizce bölümünde 175 ifade/191 kelime olası yazım hatası olarak işaretlenmiştir.
- Veri kartı, Common Voice ile eğitilmiş bazı XLS-R modellerinin Common Voice alt kümesinde konuşmacı çakışmasından yararlanmış olabileceğini ayrıca not eder.
- **Önerilen rol:** Lisans/erişim koşulları kabul edilip her alt küme ayrı incelendikten sonra harici, çok alanlı değerlendirme. Kaynak metin ile insan tarafından denetlenmiş referans ayrı raporlanır.
- **Kullanım kuralı:** Model/parametre ayarı için değil; kilitli değerlendirme amacıyla kullanılır. Her örneğin kaynak lisansı korunur. Veri kartındaki konuşmacıyı tanımlamama koşuluna uyulur.
- **Önemli:** TurkASR-Bench kaynak sürümü Common Voice 17'yi kullanır. Bu veri, Common Voice 27 ile aynı sürüm gibi gösterilmez.

Kaynak: [TurkASR-Bench veri kartı](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench) ve [kaynak bazlı lisans tablosu](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench/blob/main/LICENSE.md).

## 3. İlk kullanım önceliği

| Kaynak | İlk kullanım | İlk karar |
|---|---|---|
| Common Voice Turkish 27.0 | Okunmuş konuşma temel ASR | Lisans/split snapshot'ı sonrası aday |
| FLEURS tr_tr | Okunmuş konuşma dış karşılaştırma | CC BY atfı ve test split kilidiyle aday |
| MediaSpeech Turkish | Yayın konuşması | Yalnız keşif/ikincil; split ve kaynak koşulu doğrulansın |
| Real-TurnTurk | VAD, zaman ve sıra kontrolü | Yalnız audio/transcript; diarization benchmark değil |
| TurkASR-Bench | Çok alanlı dış ASR kıyası | Kaynak lisansı/erişim şartları ve referans hataları ayrıştırıldıktan sonra |

İlk karşılaştırma veri kaynaklarının hepsini tek bir WER havuzunda birleştirmemelidir. Kaynak ve konuşma türü bazında ayrı sonuçlar raporlanır.

## 4. Split ve veri sızıntısı politikası

- Önceden tanımlı train/dev/test split'i bulunan kaynakta özgün split korunur.
- Nihai test/locked test örneği, model ayarı, eşik seçimi, prompt/decoder ayarı veya model fine-tuning için kullanılmaz.
- Özel MİHENK test setinde aynı konuşmacı veya aynı kayıt oturumundan gelen parçalar farklı split'lere dağılmaz. Mümkünse konuşmacı ve oturum grupları birlikte ayrılır.
- Kaynak veri setinde güvenilir konuşmacı/oturum kimliği yoksa speaker-disjoint iddiası verilmez; bu sınırlama raporlanır.
- Medya kaynağı bir video veya yayın ise aynı video/yayın içindeki kesitler farklı split'lere düşmemelidir.
- Modelin ön eğitim/ince ayar verisiyle örtüşme bilinmiyorsa “çakışma bilinmiyor” yazılır; “bağımsız test” iddiası kurulmaz.
- Bir test seti bir kez sonuçları görmek için açıldıysa “kilitli” statüsünü kaybeder; yeni sürüm/örnek kümesiyle yeni kilitli test oluşturulur.
- ASR ve diarization için split'ler ayrı tanımlanabilir; aynı kaynağın test örneği test verisi olmaktan çıkarılıp eğitimde kullanılamaz.

## 5. Manifest yapısı

### 5.1 Kamuya açık manifest

Kamuya açık manifest yalnızca kaynak düzeyi metadata ve toplu sayımlar içermelidir:

- Manifest sürümü ve veri kümesi kimliği.
- Kaynak adı, URL, yayıncı, snapshot tarihi, kaynak revision/commit veya sürüm.
- Beyan edilen lisans, lisans kapsamı (dataset geneli / örnek bazlı / karma), inceleme durumu.
- Ticari kullanım, çoğaltma/yeniden dağıtım ve atıf koşulu.
- İzin verilen test amaçları ve açık sınırlamalar.
- Split politikası, split adları ve her split için toplu kayıt/süre sayıları.
- Gizlilik alanları: public repoda ses/transkript/kişi eşleştirme anahtarı bulunmadığını belirten sabit kontroller.

Kamuya açık manifestte örnek bazlı SHA-256, gerçek dosya adı/yolu, transcript, konuşmacı token'ı, zaman segmentleri veya kişisel metadata bulunmaz.

### 5.2 Korumalı yerel örnek manifesti

Yerel, erişim kontrollü test alanında her örnek için:

- Rastgele üretilmiş MİHENK örnek kimliği.
- Kaynak veri kümesi/revision/orijinal split ve kaynak örnek kimliği.
- Yerel korumalı dosya referansı.
- Ses SHA-256, süre, kanal sayısı, örnekleme hızı, codec/kapsayıcı.
- Split rolü ve konuşmacı/oturum gruplarını sızıntı kontrolü için temsil eden, veri kümesi içinde anahtarlı takma token.
- Lisans kaydı kimliği ve kullanım amacı.
- Referans anotasyon kimliği/sürümü, normalizasyon profili, hakem durumu.
- Türev dosya/işlem kimlikleri.
- Test koşusu kimlikleri ve sonuç bağlantıları.

Yerel dosya yolları, hash değerleri ve konuşmacı takma token'ları da vaka veya veri kaynağı hakkında hassas bilgi açığa çıkarabilir; bu nedenle public issue/PR, CI logu veya ekran görüntüsüne kopyalanmaz.

## 6. Kaynak kabul kontrol listesi

Bir veri kaynağı ilk kez kullanılırken:

- [ ] Kaynak URL ve yayıncı doğrulandı.
- [ ] Kaynak revision/sürüm/snapshot tarihi kaydedildi.
- [ ] Lisans metni ve lisansın ses/transkript/metadata üzerindeki kapsamı incelendi.
- [ ] Ticari kullanım ve yeniden dağıtım şartları ayrı kaydedildi.
- [ ] Erişim kapısı/kullanım koşulu ve atıf şartları not edildi.
- [ ] Konuşmacı, yüz, video ve diğer kişisel veri benzeri alanların kapsamı belirlendi.
- [ ] Split yapısı ve örnek seçim yöntemi doğrulandı.
- [ ] Eğitim/test sızıntısı riski incelendi.
- [ ] Referans transkript kalitesi ve normalizasyon kuralı incelendi.
- [ ] Public depoya alınabilecek metadata ile yalnız yerelde tutulacak alanlar ayrıldı.
- [ ] Kullanım kararı ve inceleyen rolü manifestte kaydedildi.

Herhangi bir kritik izin/lisans sorusu belirsizse durum **beklemede** olur; veri indirilip test/ürün içine dahil edilmiş sayılmaz.

## 7. Sonraki adım

Önce Common Voice 27 ve FLEURS Türkçe test bölmeleriyle, yalnız kaynak koşulları ve splitleri doğrulanmış bir başlangıç seti hazırlanabilir. Ardından MediaSpeech ve TurkASR-Bench lisans/split sınırlamalarıyla ayrı ikincil testler planlanır. Diarization içinse Real-TurnTurk'ün tek başına uygun olmadığı kabul edilerek, kanal karışımı ve örtüşen konuşma anotasyonu bulunan ayrıca izinli bir veri kaynağı aranır.

## 8. Kaynaklar

- [Mozilla Common Voice – veri kataloğu](https://commonvoice.mozilla.org/bas/datasets)
- [Google FLEURS – Hugging Face veri kartı](https://huggingface.co/datasets/google/fleurs)
- [MediaSpeech – Hugging Face veri kartı](https://huggingface.co/datasets/ymoslem/MediaSpeech)
- [Real-TurnTurk – Hugging Face veri kartı](https://huggingface.co/datasets/tugrulbayrak/Real-TurnTurk)
- [TurkASR-Bench – Hugging Face veri kartı](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench)
- [TurkASR-Bench – kaynak bazlı lisans tablosu](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench/blob/main/LICENSE.md)

Kaynaklar bir araştırma envanteridir. Lisans/izin incelemesi ve örnek snapshot'ı tamamlanmadan hiçbir veri kümesi MİHENK'in ürün içeriğine veya public test fixture'ına eklenmiş sayılmaz.
