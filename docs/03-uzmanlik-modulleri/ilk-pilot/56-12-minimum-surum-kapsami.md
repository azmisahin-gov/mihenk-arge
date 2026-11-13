# 56.12 – Minimum Sürüm Kapsamı ve Kabul Kapıları

> **Durum:** İlk pilot için önerilen asgari kapsam; alan uzmanı ve hukuk/veri koruma incelemesiyle kesinleşecek  
> **Tarih:** 13 Kasım 2026  
> **Karar amacı:** 56.12'yi gerçek bir bilirkişi iş akışında işe yarar hâle getirmek için zorunlu olanları, sonraki araştırma konularından ayırmak.

## 1. Ürün hedefi

56.12'nin ilk sürümü, bilirkişinin aldığı ses kayıtlarını tek bir MİHENK çalışma alanında açmasını, dinlemesini, yerel ASR ile ilk transkript taslağını üretmesini, metni sesle karşılaştırarak düzeltmesini ve görevine bağlı rapor çıktısı hazırlamasını sağlamalıdır.

İlk sürümün başarısı çok sayıda model barındırmak değil, **uzmanın tekrar tekrar yaptığı dinleme, yazma, arama ve rapora aktarma işlerini güvenli biçimde azaltmasıdır.**

Bu kapsam yalnızca **56.12 – Ses Kayıtlarının Metin Hâline Dönüştürülmesi** içindir. Ses özgünlüğü/manipülasyonu, adli ses karşılaştırması ve kişi kimliklendirmesi 56.11 veya ilgili başka uzmanlık kapsamlarında ayrıca ele alınır.

## 2. İlk sürümde zorunlu işlevler

| No | Zorunlu işlev | Asgari kabul |
|---|---|---|
| M-01 | Göreve bağlı çalışma alanı | Her kayıt ve çıktı tek bir Görev Profili altında tutulur; başka görevin verisi karışmaz. |
| M-02 | Sesleri içe alma ve envanter | Birden çok dosya alınır; dosya kimliği, ad, boyut, süre, biçim ve kanal bilgisi gösterilir. Desteklenen biçimler uygulama testinde kesinleştirilir. |
| M-03 | Bütünlük ve orijinal koruma | İçe aktarılan orijinal dosyanın hash'i alınır ve dosya değiştirilemez tutulur. Gerekli dönüştürmeler yalnızca ilişkilendirilmiş çalışma kopyasında yapılır. |
| M-04 | Tek entegre ses çalışma alanı | Oynat/duraklat, zaman çizgisi, ileri/geri sarma, seçili aralığı tekrar dinleme ve mümkünse kanal seçimi sağlanır. |
| M-05 | Yerel transkripsiyon | En az bir lisansı ve yerel çalışma koşulları doğrulanmış ASR motoru, ses için makine taslağı üretir. Vaka sesi bulut servisine gönderilmez. |
| M-06 | Sesle bağlantılı transkript | Metin bölümleri sesin zaman aralığına bağlıdır; metinden ilgili ses bölümüne ve sesten ilgili metne geçilebilir. İlk sürümde kelime düzeyinde forced alignment şart değildir. |
| M-07 | Uzman düzeltmesi | Uzman metni dinleyerek düzenler; makine çıktısı, uzman düzeltmesi ve değişiklik geçmişi birbirinden ayrılır. |
| M-08 | Belirsizlik ve konuşmacı etiketi | Duyulmayan kısım tahminle tamamlanmaz; belirsiz olarak işaretlenir. Gerekirse konuşmacılar yalnızca “Konuşmacı 1” gibi manuel ve anonim etiketlenir. |
| M-09 | Uzun ve çoklu kayıt | Birden çok kayıt kuyruğa alınır; ilerleme görünür olur; kesinti sonrası tamamlanan çalışma kaybolmaz veya yanlışlıkla yinelenmez. |
| M-10 | Rapor çıktısı | Göreve ait onaylı şablondan yeni rapor/transkript taslağı oluşturulur; kaynak kayıt ve zaman aralıkları eklerle ilişkilendirilir. DOCX/PDF gibi çalışma çıktıları test edilir. |
| M-11 | Gizlilik ve görev yalıtımı | Varsayılan çalışma yerel/ağsızdır; görevler birbirinden ayrıdır; gerçek vaka materyali public depo veya CI sistemine konmaz. |
| M-12 | Uzman onayı ve teslim sınırı | Nihai metin, rapor, e-imza ve resmî UYAP gönderimi bilirkişinin kontrolündedir. MİHENK hazırlık yapar; kullanıcı yerine imza/başvuru yapmaz. |

**UYAP/UDF sınırı:** UYAP Editör ve Adalet e-İmza, gerekli resmî son adımlar için kullanıcı tarafından kullanılan araçlar olarak kalır. UDF üretimi, imzalama veya UYAP'a otomatik gönderim ilk sürüm kabul ölçütü değildir; resmî teknik biçim ve entegrasyon hakkı doğrulanmadan vaat edilmez.

## 3. İlk sürüm için gerekli olmayanlar

Aşağıdakiler araştırma açısından değerli olabilir; fakat 56.12'nin ilk kullanılabilir sürümünü başlatmak için bekletici değildir:

- Otomatik diarization motoru ve DER karşılaştırması. İlk sürümde anonim konuşmacı etiketleri elle verilebilir.
- Konuşmacı kimliklendirmesi, ses biyometrisi, özgünlük/manipülasyon incelemesi.
- Gürültü azaltma, source separation, de-reverberation ve ses iyileştirme zincirleri.
- Forced alignment ile kelime kelime zaman damgası.
- Whisper, Qwen, TurkMedSTT, Vosk, Parakeet ve başka ailelerden geniş model yarışması.
- Aynı modelin çok sayıda nicemleme, GPU, runtime ve işletim sistemi kombinasyonunun karşılaştırılması.
- Özel benchmark CLI/harness, otomatik dashboard ve istatistiksel model sıralaması.
- LLM ile otomatik rapor yazma, embedding, vektör arama, çok modlu model veya mobil uygulama.
- Otomatik e-imza, bilirkişi kanaati üretme veya UYAP'a otomatik giriş/gönderim.

Bir ihtiyaç gerçek pilotta ortaya çıkarsa, ayrı karar ve kabul ölçütüyle sonraki sürüme alınır.

## 4. Minimum doğrulama – 12 kabul kapısı

Aşağıdaki kapılar, 48 senaryoluk geniş katalogdan ilk pilot için seçilmiş gruplardır. Parantez içindeki kimlikler mevcut senaryo kataloğuna referanstır; her bir senaryoyu ayrı bir büyük test altyapısına dönüştürmek gerekmez.

| Kapı | Doğrulanacak sonuç | İlgili senaryolar |
|---|---|---|
| K-01 | Çoklu ses dosyasının alınması ve doğru envanterlenmesi | MAT-001 |
| K-02 | Kopya doğrulaması ve orijinal dosyanın değişmezliği | MAT-004, SES-001 |
| K-03 | Ses oynatma, zaman çizgisi ve metin-ses arasında atlama | ZAM-001, ZAM-002 |
| K-04 | Türkçe ASR taslağında temel konuşma, özel ad, sayı/tarih/olumsuzluk ve sessizlik davranışı | ASR-001, ASR-003, ASR-004, ASR-005 |
| K-05 | Duyulmayan/düşük sesli bölümün tahminle tamamlanmaması ve belirsiz işaretlenmesi | ASR-006, ZAM-004 |
| K-06 | Uzman düzeltmesinin ham ASR çıktısını ezmeden sürümlenmesi | ASR-009 |
| K-07 | Anonim konuşmacı etiketinin elle atanabilmesi; kanal bilgisinin korunması | SES-002, manuel kabul kontrolü |
| K-08 | Uzun ve çoklu kayıtların kuyrukta işlenmesi | PERF-001, PERF-002 |
| K-09 | Uygulama/işlem kesintisinden sonra güvenli devam | KUR-001 |
| K-10 | Ağ kapalıyken yerel çalışma ve dışarı veri çıkmaması | GUV-001 |
| K-11 | İki görev arasında dosya, metin, önbellek ve rapor verisi karışmaması | GUV-004 |
| K-12 | Yeni rapor oluşturma, kaynak/ek eşleşmesi ve uçtan uca görev kontrolü | RPR-001, RPR-003, RPR-004, E2E-001 |

K-01–K-12'nin tamamı uzman ve güvenlik incelemesiyle geçmeden ilk pilot “kullanıma hazır” sayılmaz. Sayısal WER/RTF eşikleri gerçek test ve uzman kararı olmadan uydurulmaz.

## 5. Model ve test yaklaşımı: yalnızca karar vermeye yetecek kadar

1. İlk teknik denemede bir yerel ASR motoruyla uçtan uca akış çalıştırılır. Amaç uygulama zincirinin çalıştığını görmektir; modelin üretim için seçildiği anlamına gelmez.
2. Üretim adayını seçmeden önce aynı küçük, kilitli ve insan referanslı Türkçe test setinde en fazla iki aday karşılaştırılır: bir temel Whisper varyantı ve lisans/çalıştırma koşulları doğrulanmış bir Türkçe aday (ör. TurkMedSTT M1).
3. Okunmuş konuşma ile doğal konuşma ayrı değerlendirilir. Gerçek vaka kaydı, açık izin ve yerel güvenli ortam olmadan testte kullanılmaz.
4. Sonuçta WER/CER yanında özel ad, sayı, tarih, olumsuzluk, atlanan konuşma, sessizlikte uydurma metin ve bilirkişinin düzeltme süresi incelenir.
5. Model/runtime sürümü, model dosyası checksum değeri, lisans ve cihaz bilgisi kaydedilir. Sadece gerçekten kullanılan tek çalışma biçimi ölçülür.
6. Model kalitesi ve uygulamanın güvenliği ayrı kabul kapılarıdır. İyi WER, delilin özgünlüğünü veya bilirkişi raporunun doğruluğunu kanıtlamaz.

**Özel benchmark yazılımı ilk adım değildir.** Mevcut JSON koşu kaydı şablonu ve kontrollü yerel test günlüğü yeterlidir. Tekrarlanan manuel iş belirgin yük oluşturursa küçük bir doğrulayıcı daha sonra yazılır.

## 6. İlk sürüme geçiş için kapanış listesi

- [ ] 56.12 kapsamı ve 56.11 sınırı alan uzmanı tarafından doğrulandı.
- [ ] B-01'in gerçek işinde kullanılan giriş ses biçimleri ve beklenen rapor/teslim biçimi doğrulandı.
- [ ] En az bir hedef bilgisayarda yerel ASR teknik denemesi çalıştı.
- [ ] Bir temel model ve en fazla bir alternatif, aynı insan referanslı örneklerde karşılaştırıldı.
- [ ] K-01–K-12 kabul kapıları test edildi; kalanlar açık risk olarak yazıldı.
- [ ] Uzman, mevcut iş akışına kıyasla dinleme/düzeltme/rapor hazırlama eforunu değerlendirdi.
- [ ] Veri saklama, yedekleme, silme/iade ve lisans koşulları onaylandı.
- [ ] İlk model ve çalışma biçimi, varsayılan hedef cihaz ve paketleme yöntemi ayrı karar kaydıyla seçildi.

## 7. Bu aşamada bilinçli olarak karara bağlanmayanlar

Hedef bilgisayarın donanımı, gerçek ses biçimleri, kurum/mahkeme teslim şablonları ve uzman onayı henüz tam doğrulanmadığı için RAM/VRAM alt sınırı, kesin dosya formatı listesi, minimum WER yüzdesi, zorunlu GPU, varsayılan diarization veya UDF üretimi belirlenmez.

Bu belgedeki kapsam öneridir; teknik çalışma bir alan uzmanının mesleki yöntemini veya hukuk/veri koruma incelemesini ikame etmez.
