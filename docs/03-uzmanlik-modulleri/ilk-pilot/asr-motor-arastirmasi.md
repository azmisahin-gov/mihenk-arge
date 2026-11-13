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

**Önerilen rol:** Küçük ve kaynak dostu ikinci motor adayı; özellikle CPU/düşük donanım profilini değerlendirmek için. Doğal konuşma başarımı yeterli görülmeden ana motor yapılamaz.

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

Whisper Large v3 ve M1 aynı temel aileden olduğundan tamamen bağımsız iki mimari sayılmaz. ufakzeka-kulak bağımsız ve küçük mimari alternatifidir. Vosk da farklı ve çok küçük bir seçenek olarak saklanabilir; fakat Türkçe kalite verisi beklenir.

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
