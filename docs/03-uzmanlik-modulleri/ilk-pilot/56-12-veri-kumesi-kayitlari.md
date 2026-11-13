# 56.12 – Türkçe Test Veri Kümeleri Kaydı

> **Durum:** Kaynak araştırması ve ön uygunluk kaydı; yerel indirme/örnek doğrulaması tamamlanmış değildir  
> **Kontrol tarihi:** 13 Kasım 2026

## 1. Amaç

Bu kayıt, 56.12 ASR ve konuşmacı ayrımı testlerinde değerlendirilebilecek Türkçe ses veri kaynaklarını, lisanslarını, içerik özelliklerini ve sınırlamalarını birbirinden ayrı izler.

Bu belge indirme veya yeniden dağıtım izni değildir. Her veri kümesi kullanılmadan önce güncel kaynak koşulları ve indirilecek sürüm yeniden kontrol edilmelidir. Açık lisans, kişisel veri, ses kaydı, konuşmacı rızası, kaynak medya ve üçüncü taraf haklarına ilişkin tüm soruları otomatik olarak çözmez.

## 2. Ön değerlendirme özeti

| Kaynak | Lisans/kullanım kaydı | Veri türü | 56.12 testindeki rol | Durum |
|---|---|---|---|---|
| Mozilla Common Voice Turkish 27.0 | CC0-1.0; kaynak koşulları ayrıca korunur | Okunmuş Türkçe cümleler | Temel ASR ve kontrollü referans karşılaştırması | **Aday – kaynak sürümü sabitlenmeli** |
| Google FLEURS tr_tr | CC BY 4.0 | Okunmuş/standartlaştırılmış çok dilli konuşma | Temel ASR ve sabit test split'i | **Aday – önerilen başlangıç testlerinden biri** |
| MediaSpeech tr | Veri kartı CC BY 4.0; Türkçe alt küme erişimi/metadata doğrulanmalı | Medya yayınlarından kısa parçalar, elle yazılmış metin | Yayın tarzı konuşma için tamamlayıcı ASR testi | **Beklemede – Türkçe yapılandırma doğrulanmalı** |
| Real-TurnTurk | Veri kartı Apache 2.0 | Doğal ikili görüşmeler; konuşmacı başına ayrı ses kanalı ve zamanlı metin | Diyalog segmenti/zaman bilgisi keşfi; mono diarization ana testi değil | **Sınırlı aday – veri yapısı ve mahremiyet incelemesi** |
| TurkASR-Bench | mixed-per-source; erişim koşulları ve kaynak lisansları | Birleştirilmiş Türkçe ASR karşılaştırma kümesi | Lisansı uygun alt kümelerle keşifsel karşılaştırma | **Kısıtlı – varsayılan test kümesi değil** |

## 3. Kaynak bazında kayıtlar

### 3.1 Mozilla Common Voice – Turkish 27.0

- Kaynak: [Mozilla Data Collective – Common Voice veri kümeleri](https://commonvoice.mozilla.org/bas/datasets)
- Sürüm: Scripted Speech 27.0; dil kodu tr.
- Görünen lisans: CC0-1.0.
- Format: MP3; kaynak sayfasında Türkçe paket boyutu yaklaşık 2,79 GB olarak listeleniyor.
- İçerik: Katılımcıların yazılı cümleleri seslendirdiği okunmuş konuşma.
- Önerilen rol: Temel ASR ölçümü ve kontrollü konuşma örnekleriyle karşılaştırma.
- Sınırlama: Okunmuş cümleler doğal adli konuşma, kesintili diyalog, fısıltı, örtüşen konuşma veya telefon kaydını temsil etmez.
- Kullanım kuralı: Konuşmacı kimliği çıkarımı/eşleştirmesi yapılmaz. Kaynak veri sayfasındaki indirme, saklama ve yeniden paylaşım koşulları ayrıca okunur. Ses dosyaları MİHENK'in public deposuna kopyalanmaz.
- Test öncesi iş: İndirilen arşivin gerçek sürümü, dosya sayısı, split, konuşmacı/oturum çakışması, referans metin kalitesi ve checksum bilgisi yerel manifestte sabitlenir.

**Ön karar:** En kolay başlangıç adaylarından biri; ancak doğal diyalog başarısı için tek başına yeterli değildir.

### 3.2 Google FLEURS – Türkçe (tr_tr)

- Kaynak: [Google FLEURS veri kartı ve dosyaları](https://huggingface.co/datasets/google/fleurs)
- Sürüm: İndirme anındaki kaynak commit'i manifestte sabitlenecek; main tek başına kalıcı sürüm tanımı değildir.
- Yapılandırma: tr_tr.
- Lisans: CC BY 4.0.
- Örnekleme: Veri kartında ses örnekleri 16 kHz olarak tanımlanıyor.
- Veri kartındaki Türkçe split sayıları: train 2.526, validation 338, test 743 örnek.
- İçerik: FLEURS, FLoRes dev/devtest cümlelerinden oluşturulmuş çok dilli konuşma tanıma benchmark'ıdır; dil başına konuşma örnekleri kontrollü/okunmuş niteliktedir.
- Önerilen rol: İlk sabit ASR test kümesi; özellikle test split'i model karşılaştırmasında kullanılabilir.
- Sınırlama: Doğal diyalog ve adli kayıt çeşitliliği yerine geçmez. Model eğitiminde kullanılan FLEURS örnekleriyle test verisi çakışmamalıdır.
- Kullanım kuralı: CC BY 4.0 atıf koşulu ve kaynak veri kartı korunur. Test sesleri MİHENK uygulama paketine veya public depoya otomatik eklenmez.

**Ön karar:** Common Voice ile birlikte ilk ASR karşılaştırma tabanını oluşturması önerilir. İki kaynak ayrı sonuç sütunlarında raporlanır; tek toplam puanda kaynak farkı gizlenmez.

### 3.3 MediaSpeech – Türkçe (tr)

- Kaynak: [MediaSpeech veri kartı](https://huggingface.co/datasets/ymoslem/MediaSpeech)
- Lisans: Veri kartında CC BY 4.0.
- Veri kartı açıklaması, dört dil için 10'ar saatlik medya konuşması bulunduğunu; kısa seslerin YouTube'daki medya videolarından otomatik kesildiğini ve elle yazıya geçirildiğini belirtiyor.
- Türkçe tr yapılandırması, kaynak README'de listelenmiş olmakla birlikte, güncel Hugging Face sayfasının görünür dil/önizleme alanı Türkçe yapılandırmayı açık biçimde göstermiyor.
- Önerilen rol: Yayın tarzı konuşma için ek ASR stres testi.
- Sınırlama: YouTube kaynaklı içeriğin hakları, veri kümesi lisansı ve türetilmiş örneklerin yeniden kullanım koşulları ayrı hukukî inceleme gerektirir. Otomatik kesim ve metin işleme, zaman damgası/referans doğruluğu bakımından da kontrol edilmelidir.

**Ön karar:** Türkçe tr alt kümesi güncel sürümde gerçekten indirilebilir mi, lisans ve kaynak koşulları yeterli mi, örnek referanslar doğru mu soruları doğrulanana kadar ana test paketine alınmaz.

### 3.4 Real-TurnTurk

- Kaynak: [Real-TurnTurk veri kartı](https://huggingface.co/datasets/tugrulbayrak/Real-TurnTurk)
- Lisans: Veri kartında Apache 2.0.
- Veri kartı özeti: 6 doğal diyalog, 6 farklı konuşmacı (p01–p06), 12 konuşmacı-kanal ses dosyası, toplam 1,94 saat diyalog, 1.642 konuşma sırası, 2.502 transkript segmenti ve 16.027 kelime.
- Ses dosyaları: Konuşmacı başına izole edilmiş mono Opus/48 kHz dosyalar. Veri kartı, karşı konuşmacı sızıntısının kendi konuşmacısının seviyesinden 73–78 dB düşük olduğunu belirtiyor.
- Transkript: Başlangıç/bitiş zamanları, konuşmacı etiketi ve metin alanları.
- Ek içerik: Veri kümesinde konuşmacı/kişi bazlı görsel öznitelikler ve yüz hareketi özellikleri de var. 56.12 testinde bu görsel alanlara ihtiyaç yoktur.
- Önerilen rol: Konuşma sırası, geri bildirim (backchannel), zaman hizası ve segment anotasyon yapısını keşfetmek.
- Kritik sınırlama: Konuşmacı seslerinin ayrı kanallarda izole edilmesi, karışık tek mikrofon kaydında diarization başarısını ölçmez. Bu nedenle ana diarization kabul seti olarak kullanılmamalıdır.
- Gizlilik kuralı: p01–p06 kodlarının kayıtlar arasında kişi eşleştirmesine dönüştürülmesi yapılmaz. Yüz/baş/göz/ağız öznitelikleri ve animasyon görüntüsü MİHENK test kapsamına alınmaz. Yalnızca sesin kullanılabilirliği, kaynak koşulları ve gerekli izinler doğrulanır.

**Ön karar:** Keşifsel yardımcı kaynak. Konuşmacı ayrımı için asıl test, gönüllülerin açık rızasıyla kaydedilmiş, tek miks kanallı ve insan anotasyonlu sentetik/kontrollü diyalog olmalıdır.

### 3.5 TurkASR-Bench

- Kaynak: [TurkASR-Bench veri kartı](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench) ve [kaynak lisans tablosu](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench/blob/main/LICENSE.md).
- Veri kartı yaklaşık 5.200 ifade, 7 kaynak, 16 kHz FLAC ve hem ham hem normalize metin bilgisi veriyor.
- Lisans mixed-per-source; her örnek kendi kaynağının lisansını taşır.
- Erişim için veri kartındaki koşulları kabul etmek gerekir. Kart, araştırma/değerlendirme amacını ve konuşmacı kimliğini belirlememe şartını bildiriyor.
- Alt kaynaklar arasında CC0-1.0, CC BY 4.0, CC BY-NC-SA 3.0 ve GPL-3.0 gibi farklı şartlar yer alıyor.
- Kaynak lisans dosyasında Real-TurnTurk alt kümesi CC BY 4.0 olarak görünürken özgün Real-TurnTurk veri kartı Apache 2.0 göstermektedir. Bu fark açıklığa kavuşmadan bu alt küme kullanıma uygun sayılmaz.
- Veri kartındaki yaklaşık toplam örnek sayısı ile kaynakların alt küme dökümü yerel erişimde tekrar doğrulanmalıdır.

**Ön karar:** Tek bir serbest lisanslı test paketi gibi kullanılamaz. Kullanılacaksa her satırın license alanına göre filtrelenir, kaynak lisansı korunur, kısıtlı/uyuşmayan alt kümeler dışarıda bırakılır ve veri erişim şartları kabul edilir.

## 4. MİHENK için önerilen veri katmanları

### Katman A – Temel ASR

- FLEURS tr_tr test split'i.
- Common Voice Turkish 27.0 test split'i.
- Kaynakların her biri için ayrı skor; mümkünse veri kümesi/konuşmacı sızıntısı kontrolü.

### Katman B – Doğal konuşma ve medya

- MediaSpeech tr, ancak Türkçe alt küme erişimi ve kaynak hakları doğrulanırsa.
- Real-TurnTurk'ten yalnız uygun ses odaklı keşif; kişi eşleştirmesi ve görsel öznitelikler dışarıda.

### Katman C – MİHENK kontrollü sentetik/kontrollü diyalog

56.12'nin gerçek iş yüküne daha yakın testler için kendi kontrol setimiz gereklidir:
- Önceden yazılmış kurgusal senaryolar ve serbest konuşma yönergeleri.
- Katılımcıların açık ve belgeli rızası.
- Gerçek kişi, dosya, dava, adres veya hassas bilgi içermeyen yapay metin.
- Tek mikrofon/tek miks ve çok kanallı kayıtların ayrı test profilleri.
- İki veya daha fazla konuşmacı, kısa geri bildirimler, söz kesme, örtüşme, fısıltı, uzak mikrofon ve kontrollü arka plan koşulları.
- Her kayıt için ayrı anonim konuşmacı etiketi; kayıtlar arası kimlik eşleştirmesi yok.
- İzin verilmedikçe sesler public depoya konmaz; yalnız metaveri ve şema yayımlanır.

## 5. Veri split ve sızıntı politikası

- Kaynağın resmi train/validation/test split'i varsa ilk aşamada aynen korunur.
- Split'i olmayan veri, rastgele klip bazında değil; mümkün olduğunda konuşmacı, oturum ve kaynak kaydı bazında ayrılır.
- Aynı konuşmacının aynı oturumdaki cümleleri train ve test arasında bölünmez.
- Model eğitiminde kullanılmış veri/konuşmacı/oturum bilgisi biliniyorsa test ile çakışma taranır.
- Eğitim veri kökeni bilinmiyorsa bu belirsizlik sonuç raporuna yazılır; modelin test skoru bağımsız performans olarak sunulmaz.
- Geliştirme/ayar kümesi ile nihai test kümesi ayrılır. Nihai test kümesi, parametre seçimi için kullanılmaz.
- Test verisi değiştiğinde veri kümesi sürümü ve test kimliği değişir; geçmiş sonuçlar yeni veriyle karşılaştırılabilir gibi gösterilmez.

## 6. Veri kümesi manifestine yazılacak alanlar

Her kaynak ve indirilen sürüm için:
- Sabit veri kümesi kimliği ve kaynak URL'si.
- Veri kümesi adı, sürüm, commit/release ve erişim tarihi.
- Dil, alt yapılandırma ve split.
- Kaynak sayfasındaki lisans ile her alt örneğin lisansı.
- Kaynakta bildirilen örnek sayısı, süre, codec, kanal ve örnekleme hızı.
- İndirme dosyalarının yerel checksum değerleri.
- Veri kullanım amacı ve yasak/kısıtlı kullanım koşulları.
- İnsan referans metni var mı; anotasyon yöntemi ve doğrulama durumu.
- Model eğitim verisiyle olası çakışma bilgisi.
- Kullanım kararı, karar sahibi, inceleme tarihi ve açık riskler.

Manifest şablonu 56-12-veri-kumesi-manifest-sablonu.json dosyasındadır. Public dosya yalnızca kamuya açık kaynak verisi ve genel metadata içerebilir. Gerçek bilirkişi dosyalarının hash'leri, adları, transkriptleri veya kimlik bilgileri public manifest'e yazılmaz.

## 7. Kaynaklar

- [Mozilla Common Voice – veri kümesi kataloğu](https://commonvoice.mozilla.org/bas/datasets)
- [Google FLEURS – veri kartı](https://huggingface.co/datasets/google/fleurs) ve [ham README / Türkçe split](https://huggingface.co/datasets/google/fleurs/raw/main/README.md)
- [MediaSpeech – veri kartı](https://huggingface.co/datasets/ymoslem/MediaSpeech)
- [Real-TurnTurk – veri kartı ve dosya şeması](https://huggingface.co/datasets/tugrulbayrak/Real-TurnTurk)
- [TurkASR-Bench – veri kartı](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench) ve [LICENSE.md](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench/blob/main/LICENSE.md)

Bu kaynakların güncel durumu her test yayımında yeniden kontrol edilir. Bu belge, bu veri kümelerinin MİHENK'e gömülebileceği veya public depoda dağıtılabileceği anlamına gelmez.
