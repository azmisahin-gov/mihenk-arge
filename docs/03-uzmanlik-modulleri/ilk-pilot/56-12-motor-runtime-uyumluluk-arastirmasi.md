# 56.12 – ASR, Zaman Hizalama ve Konuşmacı Ayrımı Motor Uyumluluk Araştırması

> **Durum:** Teknik aday ve uyumluluk araştırması; üretim motoru seçilmedi  
> **Araştırma tarihi:** 13 Kasım 2026  
> **Kapsam:** Yerel ASR, VAD, forced alignment, diarization ve ses işleme yardımcıları

## 1. Amaç

Bu belge, 56.12 modülünde değerlendirilecek motorların hangi işi yaptığını, hangi çalışma zamanında çalıştığını, hangi model biçimini beklediğini ve MİHENK'in dağıtımına ne kadar uygun göründüğünü ayırır.

**Bir motorun açık kaynak olması, model dosyasının aynı lisansa sahip olduğu veya Türkçe adli seslerde başarılı olduğu anlamına gelmez.** Kod, runtime, model ağırlığı, tokenizer/işlemci dosyaları, veri kökeni ve dönüştürme araçları ayrı incelenmelidir.

Üretim kararı verilmemiştir. Adaylar aynı sabit test setinde, yerel ve çevrimdışı koşullarda ölçülmelidir.

## 2. Birbirinden ayrılması gereken ses görevleri

| Görev | Ne yapar? | Ne yapmaz? |
|---|---|---|
| ASR (Speech-to-Text) | Konuşmayı metne dönüştürür | Metnin doğru olduğunu veya kaydın özgün olduğunu kanıtlamaz |
| VAD | Konuşma bulunan zaman aralıklarını sessizlikten ayırır | Konuşmacıyı tanımaz, kelimeyi yazıya dökmez |
| Forced Alignment | Önceden verilmiş metni ses üzerindeki zaman aralıklarına hizalar | Metnin duyulduğunu veya doğru olduğunu doğrulamaz; eksik/yanlış metni zorla hizalayabilir |
| Diarization | Aynı kayıt içindeki konuşma aralıklarını anonim konuşmacı kümelerine atar | Gerçek kişinin kimliğini, yaşını veya cinsiyetini belirlemez |
| Source Separation | Karışmış ses kaynaklarını ayrı ses kanallarına ayırmaya çalışır | Konuşmacı kimliği veya transkript doğruluğu üretmez |
| Speech Enhancement | Gürültü/yankı gibi sinyal koşullarını değiştirmeye çalışır | Orijinal sesin yerine geçmez; özgün içeriği koruduğu varsayılamaz |

Bu görevlerin tek bir “ses yapay zekâsı” motorunda birleşmesi zorunlu değildir. MİHENK arayüzü bunları tek deneyim içinde yönetebilir; arka planda farklı yerel motorlar kullanılabilir.

## 3. ASR çalışma zamanları

### 3.1 whisper.cpp

- Kod lisansı: MIT.
- Uygulama: C/C++; yerel CPU ve farklı GPU/işlemci hızlandırma backend'leri.
- Model dosyası: whisper.cpp'nin kendi özel **GGML** model biçimi. Resmî README model dosyasında parametreler, mel filtreleri, sözlük ve ağırlıkların tek dosyada tutulduğunu belirtir.
- **GGUF değildir.** GGUF, LLM çalışma zamanlarında sık kullanılan ayrı bir model biçimidir. Bir GGUF dosyasını uzantısını değiştirerek veya doğrudan whisper.cpp'ye vererek çalıştırma varsayımı yapılmamalıdır.
- Resmî model listesi çok dilli tiny, base, small, medium, large-v3 ve large-v3-turbo gibi seçenekleri içerir. .en son ekli modeller yalnız İngilizce modellerdir; Türkçe testte kullanılmaz.
- Resmî README'de tam duyarlıklı model için yaklaşık bellek değerleri: tiny 273 MB, base 388 MB, small 852 MB, medium 2,1 GB, large 3,9 GB. Bunlar belirli donanımdaki toplam sistem RAM'i garantisi veya nicemlenmiş model ölçümü değildir.
- Resmî model dosyaları arasında large-v3-q5_0 yaklaşık 1,1 GiB ve large-v3-turbo-q5_0 yaklaşık 547 MiB disk boyutuyla listelenir. Dosya boyutu, gerçek tepe RAM ihtiyacıyla aynı değildir.
- Q5_0 nicemleme model ağırlığı disk/bellek ihtiyacını azaltabilir; hızın artması veya doğruluğun korunması her donanım için garanti değildir. Aynı test setinde WER/CER, kritik kelimeler, RAM, VRAM ve RTF ölçülmelidir.
- whisper.cpp, Silero-VAD gibi VAD modelleriyle konuşma bölümlerini önceden seçebilir. Sessizlik işlemini hızlandırabilir; ancak kısa, kısık veya gürültü içindeki konuşmayı kesme riski nedeniyle sınır payı, padding ve kaynak zaman ofseti test edilmelidir.
- Token düzeyi zaman damgası için DTW tabanlı seçenekler deneysel niteliktedir; kelime zamanları ayrıca insan örneklem kontrolünden geçmelidir.

**Önerilen rol:** Öncelikli yerel ASR adaylarından biri. Düşük/orta kaynak donanım için base, small, large-v3-turbo-q5_0 gibi farklı ölçekler karşılaştırılabilir; en küçük modelin Türkçe doğruluğu kabul edilmiş değildir.

### 3.2 faster-whisper + CTranslate2

- faster-whisper kodu ve CTranslate2 runtime'ı MIT lisanslıdır.
- faster-whisper, Whisper modellerini CTranslate2 üzerinde çalıştıran alternatif uygulamadır.
- CTranslate2; int8, int8_float32, int8_float16, float16, float32 ve donanıma bağlı diğer türleri destekler. CPU'da INT8; uyumlu NVIDIA GPU'da INT8/FP16 karması gibi seçenekler sunar.
- CTranslate2 belgeleri desteklenen compute türünün CPU/GPU mimarisine göre farklı şekilde çözümlenebileceğini, bazı Apple MPS INT8 isteklerinin FP16'ya dönüşebildiğini belirtir. Bu nedenle yalnızca yapılandırmada “int8” yazması, gerçek hesaplamanın kesin olarak INT8 olduğu anlamına gelmez.
- faster-whisper geliştiricisinin karşılaştırmasında Large-v2, RTX 3070 Ti 8 GB üzerinde int8 modunda FP16'ya göre daha düşük VRAM ve daha kısa işlem süresi göstermiştir; CPU Small modelde de INT8, aynı test ortamında bellek kullanımını düşürmüştür. Bunlar geliştirici benchmark'ıdır, MİHENK donanımında garanti değildir.
- Model dönüştürme/quantization aşamasında CTranslate2 uyumlu model dosyası oluşturulmalıdır. Her Hugging Face/Transformers modeli doğrudan hazır CTranslate2 biçiminde değildir.

**Önerilen rol:** whisper.cpp ile aynı Whisper model ailesini farklı runtime'da karşılaştıran önemli performans adayı. Özellikle CPU INT8 ve NVIDIA GPU INT8/FP16 bellek/süre sonuçları test edilmelidir.

### 3.3 Hugging Face Transformers / PyTorch

- TurkMedSTT M1 ve Türkçe wav2vec2/XLS-R gibi modellerin doğal çalışma yolu Transformers/PyTorch olabilir.
- Bu runtime modeli doğrudan kaynak mimarisinde denemeye imkân verir; fakat PyTorch, model ve bağımlılık paketi masaüstü kurulumunun boyutunu/belleğini artırabilir.
- M1'in Whisper mimarisinden türemesi, otomatik olarak whisper.cpp GGML veya CTranslate2 dosyasına uyumlu olduğu anlamına gelmez. Ağırlıkların birleştirilmesi, model mimarisi, tokenizer ve dönüştürme çıktısı ayrı doğrulanmalıdır.
- Transformers tabanlı referans çalışma ile dönüştürülmüş hızlı çalışma karşılaştırılırken aynı ağırlık sürümü ve mümkün olduğunca aynı decoding ayarları kullanılmalıdır.

**Önerilen rol:** Türkçe uyarlamaların referans çalışma zamanı ve model dönüştürme denetimi. Üretim dağıtım tercihi henüz değil.

### 3.4 Model-özel GGUF dışa aktarımı: ufakzeka-kulak + parakeet.cpp

- ufakzeka-kulak model kartı aynı ağırlıkların NeMo, Transformers, sherpa-onnx, parakeet.cpp için GGUF ve parakeet-mlx biçimlerinde yayımlandığını belirtiyor.
- GGUF dosyaları Parakeet.cpp v0.6.1 ile çalıştırılmak üzere hazırlanmıştır; f32 ve q8_0 varyantları bulunur. Model kartı q8_0 dışa aktarımını FLEURS Turkish dev ve Common Voice 27 Turkish dev üzerinde NeMo referansına yakın sonuçlarla kontrol ettiğini bildirir.
- Bu, GGUF'nin whisper.cpp tarafından kullanıldığı anlamına gelmez. Her GGUF dosyası yalnızca kendi model mimarisini ve runtime'ını destekleyen yürütücüyle çalışır.
- Model tek utterance işleyen, streaming olmayan bir modeldir; VAD ile bölütleme ve her bölümde birkaç yüz milisaniye sınır payı önerilir.
- Model diarization yapmaz; kelime zaman damgaları değerlendirilmemiştir. Real-TurnTurk konuşma testinde bildirilen WER 0,3807'dir; doğal diyalogta önemli başarım düşüşü vardır.
- Eğitim verilerinin büyük bölümü YODAS kaynaklıdır. Model kartına göre bu kayıtların önemli kısmının metni bir ASR tarafından oluşturulup başka bir ASR tarafından kontrol edilmiştir; iki sistemin ortak hataları eğitim metninde kalmış olabilir.

**Önerilen rol:** Düşük kaynaklı, Türkçe tek-utterance ASR karşılaştırması; özellikle Parakeet.cpp GGUF q8_0 ile sherpa-onnx INT8 varyantlarının aynı örneklerde ölçülmesi. Yalnızca model kartı benchmark'ıyla üretim onayı verilmez.

### 3.5 Turkish STT 66M v2 + sherpa-onnx

- [mihuai/turkish-stt-66m-v2](https://huggingface.co/mihuai/turkish-stt-66m-v2) yaklaşık 68 MB INT8, 66M parametreli streaming Zipformer transducer modeli olarak tanıtılıyor.
- Model kartı tek CPU thread'inde çalışmayı ve sherpa-onnx doğrudan kullanımını belgeliyor. FLEURS-TR 743 klip için geliştirici standart WER yüzde 10,06; Damga normalizasyonuyla yüzde 6,21 rapor ediyor.
- Model kartında lisans mihu-community-license olarak görünmekte; tam lisans metni bu araştırmada erişilebilir olmadığından ürün/dağıtım için uygunluğu doğrulanmamıştır.
- Lisans, eğitim veri kaynakları ve gerçek diyalog/örtüşme testleri doğrulanana kadar bekleme adayı olarak kalır. Performans beyanı MİHENK ölçümü değildir.

### 3.6 Uran STT Base + faster-whisper/CTranslate2

- [curiositytech/uran-stt-base](https://huggingface.co/curiositytech/uran-stt-base), Apache 2.0 lisanslı, Whisper-base temelli ve CTranslate2/faster-whisper biçiminde yayımlanan Türkçe uyarlamadır.
- Model kartı yaklaşık 75 MB INT8, yaklaşık 80 saat Common Voice 17 Turkish ve OpenSLR-108 eğitim verisi bildiriyor.
- Kartta Common Voice 17 Turkish testinde WER yüzde 38,5 / CER yüzde 10,3 ve belirli Intel i7 12. nesil CPU'da 5 saniyelik örnek için 250–400 ms latency beyanı bulunuyor.
- Bu sonuçlar model geliştiricisinin kendi ölçümleridir; test protokolü ve split sızıntısı bağımsız MİHENK denetiminden geçmemiştir. WER değeri nedeniyle ana doğruluk adayı değildir; düşük öncelikli CPU taban çizgisi olarak tutulur.
### 3.7 whisper.cpp ve faster-whisper arasında seçim

| Karar ölçütü | whisper.cpp | faster-whisper / CTranslate2 |
|---|---|---|
| Ana teknoloji | C/C++ ve GGML | C++ runtime, Python API ve CTranslate2 model biçimi |
| Kod lisansı | MIT | MIT |
| CPU düşük bellek | Küçük ve nicemlenmiş GGML modeller için güçlü aday | INT8 CPU desteği var; RAM ve hız gerçek cihazda ölçülmeli |
| GPU | Platform/backend'e bağlı çoklu hızlandırma | NVIDIA CUDA ve desteklenen diğer backend'ler; kurulum sürücü bağımlılıkları var |
| Model biçimi | whisper.cpp GGML | CTranslate2'ye dönüştürülmüş model |
| Quantization | Q5_0 gibi GGML nicemleme seçenekleri | INT8, INT8-FP16 vb. compute türleri |
| Uygulama entegrasyonu | C/C++ kütüphanesi/CLI | Python üzerinden kolay; yerel servis/worker olarak paketlenebilir |
| Açık risk | Quantization/DTW/VAD sınırlarının test edilmesi | Python/runtime/codec bağımlılıkları ve model dönüştürme zinciri |

**Ara karar:** İkisi de aynı Whisper model adaylarının farklı çalışma yolu olarak test edilecek; birini yalnız README benchmark'ına bakarak seçmeyeceğiz.

## 4. Zaman damgası ve forced alignment

### 4.1 WhisperX

- Kod lisansı BSD-2-Clause.
- WhisperX; faster-whisper/CTranslate2 ASR, VAD tabanlı bölümleme, wav2vec2 forced alignment ve pyannote diarization iş akışlarını birleştirir.
- Kelime düzeyi zaman damgası üretmek için ASR metnini dil-özel hizalama modeliyle sese hizalar.
- Mevcut WhisperX kaynak kodunda Türkçe (tr) için mpoyraz/wav2vec2-xls-r-300m-cv7-turkish hizalama modeli tanımlıdır.
- İlgili model kartı CC BY 4.0 gösterir ve yaklaşık 1,76 GB model boyutu listeler. Model Common Voice 7 Türkçe ve MediaSpeech üzerinde eğitilmiştir; kendi kartında Common Voice 7 testinde WER 8,62/CER 2,26; başka doğal konuşma değerlendirmesinde daha yüksek WER raporlar. Bunlar geliştirici/model kartı beyanıdır; MİHENK testi değildir.
- WhisperX README, hizalama sözlüğünde olmayan karakter/sayı gösterimlerinin zamanlanamayabileceğini; örtüşen konuşmanın iyi ele alınmadığını ve diarization'ın kusursuz olmadığını belirtir.
- Forced alignment, yanlış ASR metnini de ses zamanına oturtmaya çalışabilir. Bu nedenle metni doğrulamaz; uzman tarafından doğrulanmış metnin zaman bağlantısını üretmek için yardımcı aşama olarak değerlendirilmelidir.
- WhisperX'in Python/torch/pyannote bağımlılıkları ve model ağırlıklarının lisansları, BSD kod lisansından ayrıdır.

**Önerilen rol:** Kelime zaman damgası ve konuşmacı etiketlerinin tek arayüzde nasıl birleştirilebileceğini araştıran PoC adayı. Türkçe hizalama, sayılar, kısaltmalar, özel adlar ve belirsiz segmentlerde ayrı test gerekir.

### 4.2 Whisper.cpp zamanları

whisper.cpp segment ve token zaman bilgisi üretebilir; DTW tabanlı token-level timestamp seçeneği deneysel olarak belgelenmiştir. Türkçe kelime sınırlarının yeterliliği ve noktalama/sayı biçimiyle ilişkisi ayrıca ölçülmelidir. Forced alignment ile aynı işlem değildir.

## 5. Konuşmacı ayrımı motorları

### 5.1 pyannote.audio – speaker-diarization-community-1

- pyannote.audio kodu MIT; speaker-diarization-community-1 model pipeline'ı CC BY 4.0.
- Model dosyalarına erişmek için Hugging Face koşullarının kabul edilmesi ve hesap token'ı gerekir. Model indirildikten sonra yerel/çevrimdışı çalıştırılabilir; bulut kullanımına zorunlu değildir.
- Pipeline mono 16 kHz ses bekler; stereo/çok kanallı girdiyi otomatik mono karışıma indirger ve gerekirse 16 kHz'e örnekler. MİHENK kanalları otomatik birleştirmemeli; kaynak kanalları korumalı ve yalnızca seçilmiş çalışma kopyasını motora vermelidir.
- community-1, konuşmacı ataması ve konuşmacı sayısı iyileştirmeleri ile exclusive diarization çıktısı sağlar.
- PyTorch tabanlı çalışma zamanı ve bağımlılıkları nedeniyle CPU/RAM yükü sherpa-onnx gibi ONNX seçeneklerinden farklı olabilir; gerçek donanım testi gerekir.
- Benchmark sonuçları farklı diller/ortamlar üzerinde verilmiştir; Türkçe adli konuşma performansı ayrıca doğrulanmalıdır.

**Önerilen rol:** Kaliteli diarization için karşılaştırma referansı. Gated model erişimi ve CC BY 4.0 model şartları kurumsal dağıtım incelemesine tabidir.

### 5.2 sherpa-onnx

- Runtime kodu Apache 2.0; yerel/offline speech processing, C/C++ API ve çoklu platform desteği sunar.
- Offline diarization; konuşmacı segmentasyonu, speaker embedding çıkarımı ve clustering aşamalarını birleştirir.
- Resmî örnekler pyannote segmentation 3.0 ONNX modeli ve 3D-Speaker/NeMo embedding modelleriyle diarization gösterir; INT8 segmentation dosyası da bulunur.
- Örnek pyannote-segmentation-3.0 modeli model.onnx yaklaşık 5,7 MB, model.int8.onnx yaklaşık 1,5 MB olarak listelenir. Bu boyut yalnız segmentation bileşenidir; toplam pipeline boyutu değildir.
- Örnek embedding ağırlıklarından biri 3D-Speaker ERes2Net Çince (zh-cn) 16 kHz modelidir. Bu modelin Türkçe konuşmacı kümelerinde başarımı, model lisansı ve dağıtım koşulu ayrı test edilmelidir; boyutu küçük diye otomatik kabul edilmez.
- sherpa-onnx runtime lisansı, indirilen her segmentation/embedding modelinin lisansını kapsamaz. Her model dosyasıyla birlikte gelen lisans ve kaynak belgesi kontrol edilmelidir.

**Önerilen rol:** Düşük bellek/CPU ve paketlenebilir offline diarization hattı için birincil runtime adayı; Türkçe seslerde segmentation ve embedding modelleri ayrı ayrı doğrulanmalı.

### 5.3 NVIDIA NeMo Sortformer / Nemotron-3-Diarization

- Sortformer, konuşmacı etkinliğini uçtan uca tahmin eden diarization yaklaşımıdır.
- Güncel nvidia/Nemotron-3-Diarization model kartı OpenMDW License Agreement 1.1 gösterir ve en çok sekiz konuşmacı için yerel kayıtlı/gerçek zamanlı konuşma kullanımını tanımlar.
- NVIDIA NeMo Labs Nightly belgelerinde Nemotron-3-Diarization için belirli NeMo sürüm/build gereksinimi ve yerel .nemo dosyasıyla çalışma yolu belirtilir.
- Önceki diar_streaming_sortformer_4spk-v2.1 modeli dört konuşmacı ile sınırlıdır; NVIDIA Open Model License kullanır ve model kartında öncelikle İngilizce veriyle eğitildiği, İngilizce dışı ve gürültülü koşullarda performansın düşebileceği yazılıdır.
- NeMo Lab belgeleri benzer sesli konuşmacıları karıştırma, gürültü ve sınırlı aksan temsiline ilişkin riskleri de belirtir.
- NeMo/PyTorch yığını, CPU/RAM/GPU gereksinimi, paket boyutu ve belirli lisans şartları doğrulanmadan masaüstü kurulumuna alınmamalıdır.

**Önerilen rol:** Gelişmiş karşılaştırma adayı. İlk pilot için varsayılan motor değil; Türkçe ve hedef donanım doğrulaması gerekir.

### 5.4 whisper.cpp tinydiarize

- whisper.cpp'nin small.en-tdrz modeli -tdrz ile deneysel konuşmacı dönüşü işaretleme örneği sunar.
- Mevcut resmî model listesi bu varyantı small.en-tdrz olarak gösterir; .en İngilizce modele işaret eder.
- Bu nedenle Türkçe 56.12 diarization çözümü olarak kullanıma uygun kabul edilmez.
- VAD veya konuşmacı dönüş etiketi, genel çok konuşmacılı diarization ile eş anlamlı değildir.

## 6. Motorların görev bazında ön karşılaştırması

| İşlev | İlk araştırma adayı | İkinci aday | Ön durum |
|---|---|---|---|
| ASR – yerel temel | whisper.cpp GGML | faster-whisper/CTranslate2 | Aynı Whisper modelleriyle karşılaştır |
| Türkçe düşük kaynak ASR | ufakzeka-kulak / sherpa-onnx INT8 | ufakzeka-kulak / Parakeet.cpp GGUF q8_0 | Türkçe doğal konuşmada düşük başarı riski; CPU/RAM testine bağlı |
| Küçük streaming CPU ASR | Turkish STT 66M v2 (lisans beklemede) | Uran STT Base / CTranslate2 | Lisans ve WER sonuçlarına göre kısıtlı/ikincil test |
| Türkçe uyarlama | TurkMedSTT M1 / Transformers | Türkçe XLS-R | Runtime dönüştürme ve model veri kökenini doğrula |
| Düşük bellek diarization | sherpa-onnx + uygun ONNX ağırlıklar | pyannote community-1 | Önce kaynak/lisans, sonra Türkçe test |
| Diarization referans kalitesi | pyannote community-1 | NeMo Sortformer | Dil/ortam genellemesi ayrıca ölçülmeli |
| Kelime zaman hizalama | WhisperX + Türkçe wav2vec2 | whisper.cpp token/DTW | Forced alignment taslak metni doğrulamaz |
| VAD | whisper.cpp Silero-VAD | sherpa-onnx/Silero | Kısık/kısa sözleri kesme riski sınanmalı |
| Source separation | sherpa-onnx model kataloğundaki uygun adaylar | ayrı araştırma | İlk sürüm zorunluluğu değil |
| Speech enhancement | ayrı kontrollü yerel motor | sherpa-onnx yardımcıları | Varsayılan değil; türev ses ve karşılaştırma şart |

## 7. MİHENK için önerilen test sırası

1. **ASR tabanı:** whisper.cpp üzerinde base, small, large-v3-turbo ve desteklenen Q5_0 varyantlarını aynı kısa/uzun testlerde ölç.
2. **Aynı Whisper modelinde runtime kıyaslaması:** Uyumlu model sürümüyle whisper.cpp ve faster-whisper/CTranslate2 hız, RAM/VRAM ve WER/CER karşılaştırması yap.
3. **Türkçe uyarlama:** TurkMedSTT M1'i önce desteklenen Transformers/PyTorch runtime'ında değerlendir; dönüştürme ancak model eşdeğerliği testiyle.
4. **Zaman hizalama:** İnsan referans metni ve doğrulanmış ASR metniyle WhisperX Türkçe hizalama modelini sayı, kısaltma, özel ad ve noktalama alt testlerine tabi tut.
5. **Diarization:** pyannote community-1'i kalite referansı, sherpa-onnx'i düşük bellek runtime adayı olarak aynı karışık mono kayıtlarla karşılaştır.
6. **NeMo:** Ancak önceki seçenekler yetersiz veya farklı donanım hedefi varsa ayrı benchmark.
7. **VAD/iyileştirme:** Her biri aynı ham ses üzerinde ayrı türev deney olarak test edilir; orijinalin yerine geçmez.

Tüm koşullarda test verisi, model ve runtime checksum/sürüm bilgisi, parametreler, ağ kapalı durumu, CPU/GPU ve bellek kaydedilir.

## 8. Teknik ve güvenlik kısıtları

- Gerçek dosyalar çevrimdışı, bilirkişinin yetkili cihazında kalır.
- Model dosyası ve runtime ilk kurulumdan sonra internet olmadan çalışabilmelidir.
- Gated model indirme koşulları ve lisans metni kurulum öncesi değerlendirilir; kullanıcı token'ı vaka işleme sürecinde ağa çıkış için kullanılmaz.
- Her model dosyası checksum ve lisans kaydıyla sabitlenir.
- VAD'nin sessiz/kısık/örtüşen sözü atlama riski test edilmeden varsayılan açılmaz.
- Forced alignment yalnızca zaman hizalama önerisidir; metin doğruluğuna dair kanaat değildir.
- Diarization modelinin ürettiği konuşmacı embedding vektörleri gerçek kişi kimliği değildir; kayıtlar arası kişi eşleştirmesi yapılmaz. Gerekli değilse vektörler saklanmaz; sadece uzman tarafından gözden geçirilmiş anonim segment etiketleri ve zaman bilgisi tutulur.
- Orijinal ses değişmez; downmix, resampling, VAD kesiti, filtre ve iyileştirme yalnız türev çalışma kopyasında yapılır.
- Kod ve model lisansları ayrı saklanır; bağımlılık ve model envanteri/SBOM her sürüm için tutulur.

## 9. Ara kararlar

1. **GGUF, whisper.cpp için model biçimi değildir; whisper.cpp GGML biçimini kullanır.** Bununla birlikte Parakeet.cpp gibi ayrı runtime'lar, destekledikleri ses mimarileri için GGUF dışa aktarımı sunabilir. Bu destek modele/runtime'a özeldir.
2. whisper.cpp küçük/nicemlenmiş modeller ve C/C++ paketleme açısından güçlü yerel ASR adayıdır.
3. faster-whisper/CTranslate2, INT8 ve GPU bellek yönetimi açısından ayrı benchmark adayıdır.
4. WhisperX, Türkçe alignment modeli sunması nedeniyle zaman hizalaması için dikkate değerdir; fakat Python/PyTorch/pyannote bağımlılıkları ve model lisansları ayrı yük oluşturur.
5. Türkçe diarization için whisper.cpp tinydiarize yerine bağımsız diarization motorları araştırılmalıdır.
6. sherpa-onnx düşük bellek/offline paketleme adayı; pyannote kalite referansı; NeMo ileri karşılaştırma adayı olarak tutulur.
7. Turkish STT 66M v2 düşük kaynak adayıdır ancak özel lisans metni erişilebilir olmadığından beklemededir; Uran STT Base Apache 2.0 olsa da yayımlanan WER değeri nedeniyle düşük önceliklidir.
8. ufakzeka-kulak için Parakeet.cpp GGUF q8_0 ve sherpa-onnx INT8 dışa aktarımları gerçek testte karşılaştırılabilir; modelin doğal konuşma sınırlaması göz önünde tutulmalıdır.
9. Hiçbir runtime veya model henüz üretim için seçilmedi.

## 10. Kaynaklar

- [whisper.cpp README – GGML biçimi, bellek ve quantization](https://github.com/ggml-org/whisper.cpp)
- [whisper.cpp model listesi – Q5_0, large-v3-turbo ve English-only tinydiarize](https://github.com/ggml-org/whisper.cpp/blob/master/models/README.md)
- [whisper.cpp VAD – Silero](https://github.com/ggml-org/whisper.cpp#voice-activity-detection-vad)
- [faster-whisper – runtime ve karşılaştırma](https://github.com/SYSTRAN/faster-whisper)
- [CTranslate2 quantization](https://opennmt.net/CTranslate2/quantization.html)
- [WhisperX README – Türkçe hizalama ve sınırlamalar](https://github.com/m-bain/whisperX)
- [WhisperX Türkçe hizalama model kartı](https://huggingface.co/mpoyraz/wav2vec2-xls-r-300m-cv7-turkish)
- [pyannote Community-1 model kartı](https://huggingface.co/pyannote/speaker-diarization-community-1)
- [sherpa-onnx diarization belgeleri](https://k2-fsa.github.io/sherpa/onnx/speaker-diarization/index.html)
- [sherpa-onnx offline diarization C API](https://k2-fsa.github.io/sherpa/onnx/c-api/html/speaker_diarization.html)
- [NVIDIA Nemotron-3-Diarization model kartı](https://huggingface.co/nvidia/Nemotron-3-Diarization)
- [NVIDIA Sortformer 4-speaker v2.1 model kartı](https://huggingface.co/nvidia/diar_streaming_sortformer_4spk-v2.1)

Bu kaynaklarda yazan geliştirici benchmark'ları MİHENK test sonucu değildir. Model/weights lisansı, veri kökeni, Türkçe başarım ve hedef donanım uyumluluğu bağımsız olarak doğrulanmalıdır.
