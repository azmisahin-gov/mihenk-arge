# 56.12 – Türkçe Anotasyon ve Referans Transkript Protokolü

> **Durum:** İlk anotasyon standardı taslağı; 56.12 uzmanı incelemesi bekliyor  
> **Tarih:** 13 Kasım 2026  
> **İlişkili belgeler:** [Test Planı ve Başarı Ölçütleri](56-12-test-plani-ve-basari-olcutleri.md), [Test Senaryoları](56-12-test-senaryolari.md)

## 1. Amaç

Bu belge, MİHENK 56.12 testlerinde ASR ve konuşmacı ayrımı sonuçlarını karşılaştırabilmek için insan tarafından hazırlanacak referans transkriptin ve zaman/konuşmacı anotasyonlarının nasıl üretileceğini tanımlar.

Buradaki referans, bilirkişilik raporu değildir. Bir ses test örneğine ilişkin, ölçüm amacıyla hazırlanmış ve sürümlenmiş anotasyon kaydıdır. Gerçek görevin transkripti ve nihai raporundaki meslekî yöntem ve sunum biçimi, görevlendirme ve uzman değerlendirmesine tabidir.

## 2. Anotasyon katmanları

Birbirinden farklı üç metin katmanı tutulmalıdır:

1. **Duyulan biçim (verbatim):** Kayıtta duyulan kelimeleri, tekrarları, dolgu ifadelerini, yarım kalmış sözleri ve konuşma akışını mümkün olduğunca koruyan anotasyon.
2. **Puanlama biçimi (normalized):** WER/CER gibi ölçümler için önceden ilan edilmiş normalizasyon kurallarından üretilen metin. Bu katman duyulan biçimin üzerine yazılmaz.
3. **Sunum biçimi (display):** İnsan tarafından okunabilir gösterim için noktalama, satır/paragraf düzeni ve rapor yazım tercihlerinin uygulandığı sunum katmanı. İçerik değiştiren redaksiyon değildir.

Her katman kendi sürüm ve üretim kuralına bağlanır. Normalizasyon veya sunum metni, ham anotasyonun yerine geçmez.

## 3. Temel yazım ilkeleri

- Yalnızca duyulabilen içerik yazılır; bağlamdan tahminle kelime eklenmez.
- Konuşmacının dilbilgisi, anlatımı veya kelime seçimi düzeltilmez.
- Tekrarlar, yarım ifadeler, kendini düzeltmeler ve duyulabilen dolgu ifadeleri korunur.
- “Daha düzgün” veya “daha anlamlı” cümle oluşturmak için kelime çıkarılmaz/eklenmez.
- Kişi/yer/kurum adı, kayıt dışı bilgiyle tahmin edilerek tamamlanmaz.
- Türkçe karakterler duyulan ve doğrulanabilen biçimde yazılır; modelin ASCII çıktısı otomatik olarak doğru kabul edilmez.
- Sayıların sözcük veya rakamla yazımı verbatim katmanda tek bir kararlı kurala göre uygulanır; alternatif sayısal normalizasyon ayrı puanlama profilinde tutulur.
- Anlaşılmayan kelime, sessizlik veya gürültüden farklı bir anotasyon olayıdır.
- Türkçe dışındaki kelime veya dil değişimi duyulduğu biçimde korunur; kendiliğinden çeviri yapılmaz.
- Ses dışı olaylar (ör. kapı sesi, telefon zili) konuşma transkripti içine kelimeymiş gibi yazılmaz; ayrı olay anotasyonu olarak tutulur.

## 4. Anotasyon olayları ve belirsizlik kodları

Önerilen olay sözlüğü:

| Kod | Anlam | Kullanım |
|---|---|---|
| **speech** | Anlaşılabilir konuşma | Duyulan kelime/ifade segmentleri |
| **unintelligible_speech** | Konuşma var, kelimeler anlaşılamıyor | Tahmin edilemeyen konuşma aralığı |
| **partially_intelligible** | İfadenin bir kısmı anlaşılabiliyor | Anlaşılan kelimeler ayrı segment, belirsiz aralık ayrıca işaretlenir |
| **overlapping_speech** | Birden fazla konuşmacı eşzamanlı konuşuyor | Her konuşmacı için ayrı, örtüşen segmentler |
| **non_speech_vocalization** | Konuşma olmayan vokal olay | Gülme, öksürme, iç çekme gibi; gerekiyorsa alt tür |
| **non_speech_sound** | Konuşma dışı çevresel ses | Kapı, alarm veya arka plan olayı; yalnız görev için anlamlıysa |
| **cut_off** | Kayıt veya söz kesildiği için tamamlanmamış bölüm | Duyulabilen kısım korunur, kesilme ayrıca işaretlenir |
| **silence** | Konuşma olmayan sessizlik | Yalnız VAD/sessizlik testlerinde anotasyonlanır |
| **uncertain_boundary** | Başlangıç/bitiş zamanı kesin değil | Zaman belirsizliğinin nedeni not edilir |

Ekranda [ANLAŞILAMADI] gibi bir gösterim yapılabilir; ancak bu ifade konuşmacının söylediği gerçek kelime değildir. Veri yapısında olay türü ayrı alanda tutulmalıdır.

### 4.1 Kısmen anlaşılabilen ifade

Örnek (tamamen kurgusal):

- Duyulan: “Toplantı yarın [anlaşılamayan bölüm] yapılacak.”
- Anotasyon: “Toplantı yarın” ve “yapılacak” anlaşılabilir konuşma segmentleri; aradaki zaman aralığı **unintelligible_speech**.
- Yasak: Tahmin edilen bir yer veya saat bilgisini cümleye eklemek.

### 4.2 Dolgu, tekrar ve geri bildirim

EEE, III, “yani”, “şey”, “hı hı”, “evet” gibi duyulan ifadeler, önceden ilan edilen yazım sözlüğüne göre kaydedilir. Bunlar otomatik olarak atılmaz. Özellikle kısa “evet/hı hı” geri bildirimleri, konuşmacı sırası ve zamanlama açısından anlamlı olabilir.

## 5. Konuşmacı kimliği değil, kayıt içi etiket

- Her kayıt kendi içinde **spk_01**, **spk_02** gibi anonim etiketlerle başlar.
- Etiket sırası, ilk belirgin konuşma başlangıcına göre atanabilir; bu kural bütün test setinde aynı olmalıdır.
- Etiketler kayıtlar arasında kişi eşleştirmek için kullanılmaz.
- Gerçek ad, kullanıcı adı, kurum, yaş, cinsiyet, aksan kökeni veya biyometrik kimlik çıkarımı yapılmaz.
- Konuşmacının kimliği belirsizse **speaker_id: null** veya **speaker_uncertain** kullanılır; tahminle etiket verilmez.
- Diyalogda aynı anda iki kişi konuşuyorsa zaman aralıkları örtüşebilir; tek satıra zorla birleştirilmez.
- Kanal bilgisi (**channel_1**, **left**, **right** gibi) konuşmacı kimliğiyle aynı alan değildir. Çok kanallı kayıt varsa kanal ve anonim konuşmacı ayrı tutulur.

## 6. Zaman damgası standardı

- Zaman, ilgili ses dosyasının başlangıcına göre saniye cinsinden ondalıklı sayıyla tutulur.
- Saklama hassasiyeti en az milisaniye gösterimini desteklemelidir; bu, anotasyonun milisaniye düzeyinde kesin olduğu iddiası değildir.
- Segment aralığı [start, end) olarak yorumlanır: başlangıç dahil, bitiş hariç.
- **start** sıfır veya pozitif; **end** ise **start** değerinden büyük ve dosya süresinden küçük/eşit olmalıdır.
- Aynı zaman aralığında örtüşen konuşma segmentleri geçerlidir.
- ASR'ın ürettiği zaman damgası referans zaman damgası değildir. İnsan anotasyonu veya insan tarafından doğrulanan hizalama ayrı saklanır.
- Zaman anotasyonu kelime, ifade veya konuşma sırası seviyesinde olabilir; kullanılan çözünürlük manifestte belirtilir.
- Birden çok türev ses kullanıldığında bütün zaman damgaları kaynak/orijinal zaman eksenine dönüştürülmüş olmalıdır; dönüşüm kaydedilir.

## 7. Referans transkript oluşturma SOP'si

### Adım 1 – Hazırlık

- Veri örneğinin kaynağı, lisans/izin durumu, split ve örnek kimliği doğrulanır.
- Sesin hash'i ve oynatma özellikleri kaydedilir.
- Anotatöre model adı/çıktısı gösterilmeden ilk bağımsız dinleme yapılır.
- Anotatör yönerge sürümü ve kullandığı araç kaydedilir.

### Adım 2 – Bağımsız birinci anotasyon

Anotatör A sesi dinler, verbatim metni ve belirsiz zaman aralıklarını yazar. Gerektiğinde tekrar dinleyebilir; dış kaynaklardan kişi/olay bilgisi araştırarak kelime tamamlama yapmaz.

### Adım 3 – Bağımsız ikinci anotasyon

Anotatör B, A'nın metnini ve ASR çıktısını görmeden aynı sesi bağımsız biçimde anotasyonlar.

### Adım 4 – Farkların çıkarılması

Sistem şu farkları çıkarır:
- Kelime farkları.
- Anlaşılmayan bölüm farkları.
- Segment başlangıç/bitiş farkları.
- Konuşmacı etiketi ve örtüşme farkları.
- Ses dışı olay ve konuşma olayı farkları.

### Adım 5 – Uzlaşma / hakem anotasyonu

Uyuşmayan yerler kaynak ses üzerinden tekrar dinlenir. Uzlaşma sağlanamıyorsa üçüncü yetkin anotatör/hakem karar verir veya segment çözümlenmemiş olarak bırakılır. Belirsizlik zorla tek kelimeye çevrilmez.

### Adım 6 – Referansın kilitlenmesi

- Referans sürümüne benzersiz kimlik verilir.
- Metin, olay ve zaman verileri birlikte sürümlenir.
- Değişiklik gerekçesi, önceki sürüm ve hakem kaydı korunur.
- Kilitlenmiş test referansı model geliştirme/parametre ayarı için kullanılmaz.

### 7.1 Mevcut veri kümesi referansları için ek kural

Hazır veri kümelerindeki yayımlanmış transkriptler otomatik olarak kusursuz altın standart kabul edilmez. Kaynak yazım hatası veya normalizasyon tercihi olabilir. Kaynak referansı değiştirilmeden saklanır; yapılan insan düzeltmesi ayrı, gerekçeli **reference_revision** olarak tutulur. Kaynak metinle düzeltilmiş metin ayrı raporlanabilir.

## 8. Puanlama için normalizasyon profilleri

Normalizasyon profilleri sürümlü olmalı; model çıktısı ve referans aynı kod/sürümden geçirilmelidir.

### mihenk-tr-wer-surface-v1

- Unicode NFC.
- Türkçe locale'e uygun küçük harfe dönüştürme: **I → ı**, **İ → i**.
- Baş/son ve yinelenen boşlukları temizleme.
- Noktalama işaretlerini önceden tanımlı tabloya göre kaldırma.
- Kelime içindeki kesme işaretini koruma.
- Kelime sıralamasını, ekleri, olumsuzlukları ve tekrarları koruma.
- Sayıları rakama/sözcüğe dönüştürmeme.

### mihenk-tr-wer-number-v1

surface-v1 üzerine, yalnızca önceden belirlenmiş sayı kalıplarını Türkçe sözcük biçimine veya ortak sayısal temsile dönüştürme eklenir. Tarih, saat, ondalık, para ve sıra sayısı için kurallar ayrı tanımlanır. Sayı normalizasyonu, sayının anlamını değiştiren dönüşüme izin vermez.

### mihenk-tr-cer-v1

Unicode NFC ve Türkçe küçük harf kuralları uygulanır; karakter ölçümünden önce boşluk/punktuasyon politikası açıkça belirtilir. Yüzeysel karakter farkı ile içeriksel hata ayrıştırılmaz; CER tek başına kullanılmaz.

### Her koşulda ayrı raporlanacak kritik öğeler

- Özel adlar.
- Sayılar, tarihler, saatler ve miktarlar.
- Olumsuzluk bildiren kelimeler/ekler.
- Kısaltmalar.
- Hukuki/teknik terimler.
- Konuşmacı değişiminin olduğu kısa ifadeler.

Kritik öğe listesi anotatör tarafından duyulan içeriğe göre etiketlenir; model çıktısına bakarak sonradan seçilmez.

## 9. Referans kalite kontrolü

- İki anotatörün her biri için anlaşma ve fark oranları raporlanır.
- WER/CER yalnız model hatası olarak yorumlanmaz; referans anotasyon belirsizliği de ayrıca raporlanır.
- Uzlaşma sonrası çözülemeyen segmentler ayrı tutulur ve ana skora dahil edilip edilmeyeceği önceden kararlaştırılır.
- Zaman anotasyonunda ölçülebilir sınır belirsizliği varsa başlangıç/bitiş aralığı veya tolerans açıklanır.
- Konuşmacı etiketlerinde kişi kimliği yerine yalnız kayıt içi tutarlılık kontrol edilir.
- Her referans güncellemesi, etkilenen bütün model koşularının yeniden puanlanmasını gerektirebilir; eski sonuçlar silinmez.

## 10. Anotasyon veri yapısı – kurgusal örnek

Aşağıdaki örnek gerçek ses veya gerçek vaka bilgisi içermez; yalnızca alanların nasıl kullanılacağını gösterir.

~~~json
{
  "recording_id": "SENTETIK-ORNEK-001",
  "annotation_version": "1.0.0",
  "timebase": "source_audio_seconds",
  "interval_convention": "start_inclusive_end_exclusive",
  "segments": [
    {
      "segment_id": "seg-001",
      "start": 0.420,
      "end": 1.850,
      "event_type": "speech",
      "speaker_id": "spk_01",
      "channel_id": "channel_1",
      "verbatim_text": "Bugün saat dokuzda başlayalım.",
      "normalization_profile": "mihenk-tr-wer-surface-v1",
      "review_status": "adjudicated"
    },
    {
      "segment_id": "seg-002",
      "start": 1.920,
      "end": 2.450,
      "event_type": "unintelligible_speech",
      "speaker_id": "spk_02",
      "channel_id": "channel_1",
      "verbatim_text": null,
      "display_label": "[ANLAŞILAMADI]",
      "review_status": "adjudicated"
    }
  ]
}
~~~

Bu örnekteki zamanlar, kelimeler ve kimlikler yalnızca şema gösterimidir. Kamuya açık test verisi veya referans anotasyonu olarak kullanılmamalıdır.

## 11. Açık kararlar

1. Verbatim transkriptte dolgu sesleri ve tekrarların yazım sözlüğü.
2. Kısmen anlaşılan kelime için segmentleme ve gösterim standardı.
3. Ses dışı olayların 56.12 raporuna hangi koşullarda alınacağı.
4. Kelime seviyesi zaman anotasyonunun gerekli olup olmadığı; ifade seviyesi çözünürlüğün yeterliliği.
5. İnsan anotatör yeterlilik/uzlaşma prosedürünün bilirkişi uzmanı tarafından onayı.
6. Kritik kelime/sayı/olumsuzluk etiketlerinin raporlama biçimi.

Bu kararlar kesinleşmeden performans sonuçları üzerinde tek bir WER veya CER eşiği ilan edilmemelidir.
