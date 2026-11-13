# 56.12 — Türkçe ASR Motor Araştırması

> **Durum:** Aday değerlendirmesi — üretim motoru seçimi değildir  
> **Araştırma tarihi:** 13 Kasım 2026  
> **Amaç:** MİHENK içinde yerel, çevrimdışı ve test edilebilir konuşma tanıma motor(lar)ı belirlemek.  
> **Runtime uyumluluğu:** [ASR, zaman hizalama ve diarization motor uyumluluk araştırması](56-12-motor-runtime-uyumluluk-arastirmasi.md)

## 1. Resmî onay ve açık kaynak ayrımı

İncelenen kamuya açık Adalet Bakanlığı/UYAP/Bilirkişilik Daire Başkanlığı kaynaklarında 56.12 için Bakanlıkça onaylanmış bir ASR modeli veya konuşma tanıma yazılımı yayımlanmış/doğrulanmış görünmüyor. Bu nedenle aşağıdaki açık kaynak modellerin hiçbiri “Bakanlık onaylı” olarak tanımlanamaz.

MİHENK, açık kaynak ASR kullanabilir; fakat bu motorların kabulü MİHENK'in kendi testleri, lisans/veri kökeni incelemesi ve bilirkişi kabulüyle olur. Modelin geliştiricisinin beyan ettiği doğruluk veya açık kaynak lisansı tek başına adli kullanım güvenilirliği değildir.

## 2. Değerlendirme ölçütleri

- Türkçe doğal konuşma; aksan, düşük ses, fısıltı, arka plan gürültüsü ve üst üste konuşmadaki davranış.
- Uzun seslerde kesintisiz işleme, zaman damgası ve bölümler arası bağlam.
- Ağ bağlantısı olmadan yerel çalışabilme.
- Windows ve Linux/Pardus dağıtımı; CPU/GPU seçimi ve bellek kullanımı.
- Model/çalışma zamanı lisansı, eğitim verisinin lisans ve kökeni.
- Aynı sürüm/parametreyle yeniden üretilebilir çıktı.
- İnsan düzeltme, belirsiz bölüm ve hata analizi desteği.
- Paket büyüklüğü, başlangıç süresi, gerçek zaman katsayısı (RTF) ve çökme/kurtarma.

## 3. Adaylar

### Aday A — Whisper Large v3 + yerel çalışma zamanı

- Resmî Whisper kodu ve model ağırlıkları MIT lisansı altında yayımlanmıştır.
- Çok dilli model ailesi Türkçe dahil çok sayıda dilde konuşma tanıma sağlar.
- `whisper.cpp`, C/C++ tabanlı yerel çalışma zamanı sunar; CPU, NVIDIA CUDA ve Vulkan gibi GPU hızlandırma seçenekleri bulunur. MIT lisanslıdır.
- Bu, aynı Whisper modelini bulut hizmetine göndermeden yerel çalıştırmak için güçlü bir temel adaydır.

**Önerilen rol:** Karşılaştırma için temel model ve yerel dağıtım adayı. `large-v3` doğruluk referansı, daha hızlı `turbo` ise donanım/performance alternatifi olarak ayrı test edilir. Model boyutu ve cihaz gereksinimi test edilmeden tek donanım profiline karar verilmez.

Kaynaklar:
- [OpenAI Whisper — kod ve model kartı](https://github.com/openai/whisper)
- [Whisper MIT lisansı](https://github.com/openai/whisper/blob/main/LICENSE)
- [whisper.cpp — yerel CPU/GPU çalışma zamanı](https://github.com/ggml-org/whisper.cpp)
- [whisper.cpp MIT lisansı](https://github.com/ggml-org/whisper.cpp/blob/master/LICENSE)

### Aday B — TurkMedSTT Whisper Large v3 Türkçe Genel (M1)

- Temel model Whisper Large v3; yaklaşık 140 saat genel Türkçe konuşma verisiyle LoRA uyarlaması yapılmış.
- Model kartında lisans Apache 2.0 olarak gösteriliyor.
- Proje, 320 gerçek ve medikal olmayan Türkçe klipte M1 için WER 0,0792 / CER 0,0226; temel Whisper Large v3 için aynı deneyde WER 0,1213 / CER 0,0546 bildiriyor.
- Eğitim kaynakları Common Voice, ISSAI ve OpenSLR 106. Her kaynak kendi lisans ve edinim koşullarıyla ele alınmalı; model kartı bütün ham eğitim seslerini yeniden dağıtmıyor.
- Model kartı aksan, gürültü, örtüşen konuşma ve alan dışı terminolojide başarım düşebileceğini; konuşmacı kimliği, zaman damgası ve diarization'ın ayrıca değerlendirilmediğini açıkça belirtiyor.

**Önerilen rol:** Türkçe uyarlama sayesinde umut veren doğruluk adayı. Model kartındaki skorlar geliştirici tarafından raporlanmıştır; bağımsız MİHENK testi değildir. İlk yerel testte referans Whisper Large v3 ile aynı seslerde karşılaştırılmalıdır. Transformers/PyTorch çalışma zamanı gerekir; paket boyutu ve GPU/CPU gereksinimi ayrıca ölçülmelidir.

Kaynaklar:
- [TurkMedSTT M1 model kartı ve lisansı](https://huggingface.co/turkmedstt/whisper-large-v3-turkish-general)
- [Eğitim verisi hazırlama reçetesi ve kaynak lisansları](https://github.com/muhammedkumcu/turkmedstt/blob/main/docs/DATA_PIPELINE.md)
- [TurkMedSTT benchmark açıklaması](https://huggingface.co/datasets/turkmedstt/turkish-asr-benchmark)

### Aday C — ufakzeka-kulak

- 02.11.2026 tarihli araştırma çalışması: 31,6 milyon parametreli, Türkçe için sıfırdan eğitilmiş FastConformer/TDT/CTC mimarisi.
- Apache 2.0 lisansı altında yayımlandığı ve eğitim kaynaklarının ticari kullanıma izin verdiği raporlanıyor.
- Çevrimdışı dizüstü bilgisayar, sunucu veya tarayıcı üzerinde çalıştırma hedefi var; Transformers, sherpa-onnx ve başka dışa aktarımlar belirtiliyor.
- Raporda FLEURS Turkish test WER 0,0921 ve Common Voice 27 test WER 0,0916; gerçek konuşma diyaloğu Real-TurnTurk testinde WER 0,3807.
- Bu fark, temiz/okunmuş konuşma ile doğal diyalog başarımının aynı olmadığını gösteriyor. B-01'in örneğindeki doğal konuşma, fısıltı ve üst üste konuşma için düşük WER sonucu tek başına yeterli değildir.

**Önerilen rol:** Küçük ve kaynak dostu ikinci motor adayı; özellikle CPU/düşük donanım profilini değerlendirmek için. Model kartında GGUF dışa aktarımı Parakeet.cpp için sunulmaktadır; bu, whisper.cpp GGML biçimiyle aynı değildir. Doğal konuşma başarımı yeterli görülmeden ana motor yapılamaz.

Kaynak:
- [ufakzeka-kulak — 02.11.2026 tarihli teknik rapor](https://arxiv.org/abs/2611.03605)

### Aday D — Vosk Turkish Small (yalnızca düşük öncelikli araştırma)

- Vosk API çevrimdışı ve yerel çalışmaya yönelik; API Apache 2.0.
- Türkçe `vosk-model-small-tr-0.3` 35 MB ve Apache 2.0 lisanslı olarak listeleniyor.
- Model sayfasında Türkçe hata oranı “TBD”; yayımlanmış ölçüm yok.

**Önerilen rol:** Düşük kaynaklı cihaz veya hızlı deneme alternatifi. Kalite ölçümü olmayana kadar üretim motoru veya Whisper'a denk alternatif sayılmaz.

Kaynaklar:
- [Vosk API](https://github.com/alphacep/vosk-api)
- [Vosk modeller listesi — Türkçe model ve TBD bilgisi](https://alphacephei.com/vosk/models)

### Aday E — Turkish STT 66M v2 (lisans incelemesi bekliyor)

- Model kartı: [mihuai/turkish-stt-66m-v2](https://huggingface.co/mihuai/turkish-stt-66m-v2).
- Model kartına göre 66 milyon parametreli, yaklaşık 68 MB INT8, streaming Zipformer transducer ve 16 kHz mono giriş kullanır.
- sherpa-onnx tabanlı ONNX encoder/decoder/joiner dosyaları yayımlanmıştır; tek CPU thread'inde akışlı/yerel çalıştırma örneği vardır.
- Geliştiricinin aynı FLEURS-TR 743 klibinde bildirdiği standart WER yüzde 10,06; Damga normalizasyonuyla yüzde 6,21. Whisper large-v3 için aynı kartta sırasıyla yüzde 7,82 ve yüzde 4,48 bildirilmiştir. Sonuçlar geliştirici ölçümüdür; doğal adli konuşma/örtüşme başarımı kanıtı değildir.
- Model kartı tek CPU thread'inde RTF 0,128 ve 16 çekirdekli makinede yaklaşık 25x gerçek zaman kapasitesi iddia eder; bunlar MİHENK donanımında doğrulanmış değildir.
- Lisans alanı özel mihu-community-license olarak gösteriliyor; bağlantılı LICENSE dosyasının tam metni bu araştırmada alınamadı. Bu nedenle model lisans metni doğrulanana kadar indirme/paketleme ve ürün kullanımına kapalıdır. Testte kullanımı da yalnızca hak sahibinin koşulları izin verirse mümkündür.
- Model kartında eğitim verisi ayrıntısı yalnızca Türkçe konuşma olarak özetlenmiş; kaynak/split ve gerçek diyalog dağılımı bu araştırmada doğrulanamadı.

**Önerilen rol:** Çok küçük CPU/streaming adayı olarak lisans ve veri kökeni doğrulamasına bağlı bekleme listesi. Şu an onaylı açık kaynak aday değildir.

### Aday F — Uran STT Base (düşük öncelikli CPU karşılaştırması)

- Model kartı: [curiositytech/uran-stt-base](https://huggingface.co/curiositytech/uran-stt-base).
- Whisper-base üzerine LoRA/PEFT ile uyarlanmış; önerilen çalışma zamanı faster-whisper/CTranslate2; Apache 2.0 lisansı ve yaklaşık 75 MB INT8 model boyutu beyanı vardır.
- Eğitim kaynağı olarak Common Voice 17 Turkish ve OpenSLR-108 Turkish; toplam yaklaşık 80 saat bildirilmiştir.
- Model kartında Common Voice 17 Turkish testinde WER yüzde 38,5 / CER yüzde 10,3 açıklanıyor. Bu skor diğer kaynakların test protokolü ve normalizasyonuyla doğrudan birleştirilemez; ayrıca gerçek diyalog başarımı göstermez.
- 5 saniyelik örnek için Intel i7 12. nesil CPU'da 250–400 ms gecikme ve RTF 0,06 beyan edilmiştir; donanım/ayar farklılıkları nedeniyle yalnızca geliştirici ölçümüdür.

**Önerilen rol:** Hafif CTranslate2/CPU taban çizgisi olarak düşük öncelikli test. Yayımlanan WER değeri nedeniyle ana doğruluk adayı değildir.

### Aday G — Qwen3-ASR 1.7B / 0.6B

- Resmî [Qwen3-ASR projesi](https://github.com/QwenLM/Qwen3-ASR) ve model kartları, 1.7B ve 0.6B modellerinin 52 dil ve lehçede ASR/dil tanıma yaptığını; Türkçenin desteklenen diller arasında bulunduğunu bildiriyor.
- Proje belgelerinde çevrimdışı ve akışlı (streaming) çıkarım desteği yer alıyor. Resmî `qwen-asr` paketi Transformers ve vLLM arka uçlarını sunuyor; yerel ağırlıklar indirildikten sonra ağ erişimi olmadan kullanılabilir.
- Qwen3-ASR-1.7B model kartında Apache 2.0 lisansı görülüyor; proje deposu da Apache 2.0. 0.6B ve dönüştürülmüş/quantized dosyalar için ürün paketine alınmadan önce tam model kartı ve artifact lisansı ayrıca kaydedilmelidir.
- TurkASR-Bench liderlik tablosunda Qwen3-ASR-1.7B WER yüzde 15,85 / CER yüzde 7,15 raporlamıştır. Aynı kaynağın Real-TurnTurk alt kümesinde WER yüzde 57,99'dur. Bunlar üçüncü taraf benchmark sonuçlarıdır; MİHENK ölçümü değildir.
- Qwen3-ForcedAligner-0.6B, proje kartında 11 dil için listeleniyor; listede Türkçe yoktur. Bu nedenle Qwen3-ASR'nin Türkçe desteklemesi, Qwen ForcedAligner'ın Türkçe zaman hizalaması yaptığı anlamına gelmez.
- Qwen'in ASR modeli Whisper ailesinden ayrı bir adaydır; ancak 1.7B ağırlık boyutu, Transformers/vLLM bağımlılıkları ve donanım bellek gereksinimi ölçülmelidir.

**Önerilen rol:** Aynı veri ve anotasyonla Whisper/TurkMedSTT karşısında ölçülecek bağımsız çok dilli ASR ailesi. 0.6B ve 1.7B ayrı koşu kimlikleriyle test edilir; üretim veya düşük RAM uygunluğu şimdiden varsayılmaz.

Kaynaklar:
- [Qwen3-ASR resmî deposu ve Apache 2.0 lisansı](https://github.com/QwenLM/Qwen3-ASR)
- [Qwen3-ASR-1.7B model kartı](https://huggingface.co/Qwen/Qwen3-ASR-1.7B)
- [Turkish ASR Leaderboard](https://yagmurtuncer-turkish-asr-leaderboard.hf.space/)

## 4. Runtime, model biçimi ve nicemleme notları

- whisper.cpp, model dosyalarında kendi GGML biçimini kullanır; **GGUF, whisper.cpp model biçimi değildir**. GGUF dosyası uzantısı değiştirilerek whisper.cpp'ye verilemez.
- whisper.cpp model listesinde `.en` son ekli ağırlıklar İngilizceye özeldir; Türkçe testte kullanılmaz. `small.en-tdrz` tinydiarize örneği deneysel İngilizce konuşmacı dönüş işaretlemesidir; genel Türkçe diarization motoru olarak değerlendirilmez.
- whisper.cpp VAD (ör. Silero-VAD) ile konuşma bulunan aralıkları seçebilir. VAD, diarization değildir; yalnız konuşma/sessizlik bölütlemesi yapar. Kısa, düşük sesli veya örtüşen konuşmayı kesme riski ayrıca ölçülmelidir.
- faster-whisper, Whisper modellerini CTranslate2 üzerinde çalıştıran alternatif runtime'dır. CTranslate2 INT8, FP16 ve desteklenen diğer compute türlerini sunar; gerçek kullanım türü donanım/backend'e bağlıdır. INT8 seçeneği her donanımda aynı sonuç veya bellek kazancını garanti etmez.
- TurkMedSTT M1'in Transformers/PyTorch ile çalışması, otomatik olarak whisper.cpp GGML veya CTranslate2 biçimine dönüştürülebileceği anlamına gelmez. Her dönüşüm için model mimarisi, tokenizer, ağırlıklar ve çıktı eşdeğerliği doğrulanmalıdır.
- WhisperX'in Türkçe hizalama modeli bulunması, transkriptin doğru olduğunu göstermez. Forced alignment yalnızca verilen metne zaman aralığı önerir; yanlış metni de hizalayabilir.
- Kod/runtime lisansı, her model ağırlığının ve eğitim verisinin lisansından ayrıdır. Her dosya için ayrı kaynak, checksum, lisans ve kullanım koşulu kaydedilir.

Ayrıntılı karşılaştırma, model biçimleri, VAD, diarization, alignment ve runtime adayları için [motor/runtime uyumluluk araştırmasına](56-12-motor-runtime-uyumluluk-arastirmasi.md) bakınız. Hiçbir runtime veya model üretim için seçilmiş değildir.

## 5. Aday dışı / düşük öncelikli model notları

- `ozcangundes/wav2vec2-large-xlsr-53-turkish` Apache 2.0 ve Common Voice temelli. Model kartında self-reported Common Voice WER 29,620 olarak listeleniyor; bu sonuç Whisper/TurkMedSTT ile aynı test protokolü değildir ve doğal adli konuşmayı doğrulamaz.
- `oguzhankarahan/asr-300m-turkish` Apache 2.0; model kartında WER 0,3879 bildiriliyor. İlk MİHENK aday sırasına alınmıyor.
- Araştırma erişimiyle sınırlı, ticari olmayan veya yeniden dağıtımı yasak modeller MİHENK uygulamasına eklenemez.

## 6. İlk önerilen karşılaştırma

| Rol | Aday | Gerekçe | Şimdiki karar |
|---|---|---|---|
| Temel karşılaştırma | Whisper Large v3 / turbo | Yaygın çok dilli temel model, MIT ağırlık/kod, yerel çalışma zamanı | Teste alınsın |
| Türkçe doğruluk adayı | TurkMedSTT M1 | Genel Türkçe uyarlama; model kartında daha düşük WER beyanı | Teste alınsın; veri lisansları/çalışma zamanı doğrulansın |
| Düşük kaynak alternatifi | ufakzeka-kulak | Küçük model; Apache 2.0; çevrimdışı hedef; doğal konuşmada belirgin hata artışı | İkincil test |
| Çok küçük alternatif | Vosk Turkish Small | 35 MB; Apache 2.0; WER yayımlanmamış | Yalnız düşük öncelikli test |
| Bağımsız çok dilli aday | Qwen3-ASR 0.6B / 1.7B | Türkçe destekli; resmî yerel/akışlı runtime; harici leaderboard'da ölçülmüş | Aynı testte eklensin; yerel kaynak kullanımı ölçülsün |

Whisper Large v3 ve M1 aynı temel aileden olduğundan tamamen bağımsız iki mimari sayılmaz. ufakzeka-kulak bağımsız ve küçük mimari alternatifidir. Vosk da farklı ve çok küçük bir seçenek olarak saklanabilir; fakat Türkçe kalite verisi beklenir.

### 6.1 Harici TurkASR-Bench liderlik tablosu – MİHENK dışı kanıt

13 Kasım 2026 tarihinde incelenen Turkish ASR Leaderboard, aynı TurkASR-Bench setinde 19 açık modeli karşılaştırıyor. Ana görünümde sayılar Türkçe sözcük biçimine çevrilerek puanlanıyor; Türkçe küçük harf dönüşümü, noktalama temizliği ve kelime içi kesme işaretinin korunması kullanılıyor. Farkların anlamlılığı 2.000 eşleştirilmiş bootstrap örneklemesiyle inceleniyor.

| Model | Parametre | WER | CER | Real-TurnTurk WER |
|---|---:|---:|---:|---:|
| TurkMedSTT Whisper | 1,55B | %12,39 | %5,79 | %55,16 |
| Whisper Large v3 | 1,55B | %12,83 | %7,04 | %55,93 |
| Whisper Large v3 Turbo | 809M | %12,92 | %6,91 | %56,57 |
| Qwen3-ASR-1.7B | 1,7B | %15,85 | %7,15 | %57,99 |

**Yorum ve sınır:**
- Bu tablo, aynı veri ve puanlama yöntemi üzerinde adayların birbirlerine göre konumunu gösteren harici bir referanstır; MİHENK'in kendi test sonucu, bilirkişilik doğruluğu veya üretim kabulü değildir.
- Genel WER yaklaşık %12–16 aralığındayken Real-TurnTurk doğal diyalog alt kümesinde ilk dört modelin WER'i %55'in üzerindedir. Tek bir genel ortalama doğal konuşmadaki ciddi düşüşü gizleyebilir. MİHENK sonuçları kaynak/konuşma türü bazında ayrı raporlamalıdır.
- Leaderboard modelleri tek bir Apple Silicon dizüstünde çalıştırdığını, hız sıralaması vermediğini belirtiyor. Bu tablodan RAM, VRAM, RTF veya Windows/Pardus performansı çıkarılamaz.
- TurkASR-Bench karışık kaynak lisanslıdır; bu skorları referans almak, bütün ses dosyalarını indirip MİHENK'e dahil etme izni anlamına gelmez. Veri kaynağı ve lisans incelemesi ayrı tutulur.

Kaynaklar:
- [Turkish ASR Leaderboard – sıralama ve kaynak bazında sonuçlar](https://yagmurtuncer-turkish-asr-leaderboard.hf.space/)
- [TurkASR-Bench veri kartı ve lisans sınırları](https://huggingface.co/datasets/yagmurtuncer/turkasr-bench)



## 7. Test planı — gerçek ses public depoya girmez

### Açık/sentetik test
- Kullanım lisansı ve konuşmacı koşulları doğrulanmış açık Türkçe veri.
- Sentetik olarak üretilmiş, insan tarafından kontrol edilmiş kısa diyaloglar.
- Temiz, gürültülü, telefon kalitesi, düşük ses, fısıltı, aksan, sayı/tarih/özel isim ve örtüşen konuşma sınıfları.
- Uzun kayıt ve bölme/birleştirme senaryoları.
- Sessizlikte uydurma konuşma üretme/hallucination testi.

### Yetkili yerel pilot
- Gerçek mahkeme/soruşturma sesleri GitHub'a, bulut ASR API'sine veya izinsiz üçüncü taraf servise yüklenmez.
- Gerekli hukukî ve kurumsal izinler sağlanırsa yalnız bilirkişinin cihazında, çevrimdışı ve görev verisi kasasında test edilir.
- Pilot sesleri testten sonra saklama/iade/silme politikasıyla yönetilir; test amacı için kopya alınacaksa ayrı iz kaydı tutulur.

### Metrikler
- WER ve CER; referans transkripti iki kişi tarafından kontrol edilerek hazırlanır.
- Kritik isim/sayı/tarih/olumsuzluk gibi hata sınıfları ayrıca raporlanır.
- Uzun kayıt için gerçek işlem süresi / ses süresi (RTF), bellek, CPU/GPU ve kesinti sonrası devam ölçülür.
- Duyulmayan bölümün uydurulması, sessizlikte metin üretimi, cümle atlama ve konuşmacılar arası karışma ayrı hata olarak kaydedilir.
- Modelin kendi güven skoru veya WER değeri “adli doğruluk” ya da hukukî ispat anlamına gelmez.

## 8. MİHENK içinde çalışma ilkesi

- ASR motorları kullanıcıya ayrı masaüstü program olarak açılmaz; MİHENK'in 56.12 modülünün arka plan motorları olarak yönetilir.
- Model dosyaları imzalı/sabitlenmiş sürüm, checksum, lisans ve kaynak bilgisiyle paketlenir.
- İlk çalıştırmada model indirmek gerekiyorsa indirme resmî/izinli kaynaktan doğrulanır; gerçek ses dışarı gönderilmez.
- Transkripsiyon varsayılan olarak yerel ve ağ kapalı işlenir.
- Orijinal ses değişmez; gerekiyorsa normalize/örnekleme dönüştürülmüş kopya yeni türev kayıt olur.
- İki motor çalıştırılırsa sonuçlar otomatik birleştirilip “doğru” ilan edilmez. Farklılıklar uzman dinlemesine öncelik verecek şekilde yan yana gösterilir.
- ASR metni makine taslağıdır. Bilirkişi onayı ve düzeltmesi ayrı sürümlenir.
- Konuşmacı ayırımı, kimlik tespiti ve ses özgünlüğü incelemesi ASR ile aynı özellik değildir; ayrıca doğrulanır ve gerekiyorsa ayrı modül/uzmanlık kapsamı gerektirir.

## 9. Kabul kararı için kapılar

- Aynı MİHENK test seti tüm adaylarda çalıştırılmalı.
- Model/runtime/quantization sürümleri sabitlenmeli ve checksum ile kaydedilmeli.
- CPU ve GPU'da işlem süresi/bellek ölçülmeli.
- İzin/lisans/model ağırlığı ve veri kökeni hukukî değerlendirmeden geçmeli.
- Doğal konuşma, fısıltı, gürültü ve örtüşen konuşmada hata profili bağımsız uzmanla incelenmeli.
- Kritik kelime/sayı hataları ve sessizlikte uydurma metin kabul eşikleri tanımlanmalı.
- Nihai motor seçimi ancak gerçek kullanıcı kabulü ve test sonuçlarından sonra yapılmalı.

Bu aşamada bir ASR motoru üretim için seçilmedi; MİHENK'te ASR yazmak yerine mevcut modelleri yerel ve denetlenebilir şekilde çalıştırma yaklaşımı benimsenmiştir.
