# Değişiklik Kaydı

## 0.10.1 — 13.11.2026

- TurkASR-Bench'i kullanan güncel Türkçe ASR liderlik tablosunun dış benchmark sonuçları belgelendi; genel WER'in doğal diyalogdaki yüksek hata oranını gizleyebildiği gösterildi.
- Qwen3-ASR 0.6B/1.7B, Türkçe destekleyen yerel/akışlı ve farklı bir ASR ailesi olarak karşılaştırma adaylarına eklendi.
- Qwen3-ForcedAligner'ın yayımlanmış 11 dil listesinde Türkçe olmadığı belirtildi; Türkçe zaman hizalaması ayrı değerlendirmeye bırakıldı.
- TurkASR-Bench'in 5.200 örnek/14,7 saat/16 kHz mono FLAC yapısı ve 742 örneklik Real-TurnTurk alt kümesi kaydedildi. Harici leaderboard sonuçlarının MİHENK testi olmadığı açıklandı.

## 0.10.0 — 13.11.2026

- Kamuya açık veri kümesi kataloğu için JSON Schema ve doldurulabilir manifest şablonu eklendi.
- Kamuya açık kaynak düzeyi metadata ile korumalı yerel örnek manifesti ayrıştırıldı; dosya yolları, örnek hash'leri ve anotasyonların public depoya yazılmaması yapısal kuralla desteklendi.
- Mevcut veri kümesi ve anotasyon belgeleri tek kaynak olarak korunarak yinelenen taslak belgeler kaldırıldı.

## 0.9.9 — 13.11.2026

- İncelenen açık model kartları ve benchmark tariflerinde Türkçe karışık mono konuşma için bağımsız diarization doğrulaması bulunamadığı, kapsamı sınırlı bir araştırma bulgusu olarak belgelendi.
- pyannote/sherpa-onnx/NeMo adayları üretim onayı almadan tutuldu; ECAPA speaker embedding ve VoxLingua107 language-ID modellerinin tek başına diarization olmadığı açıklandı.
- Türkçe karışık mono kayıtta aday motor doğrulaması için DIA-006 eklendi; senaryo kataloğu 52 benzersiz test kimliğine ulaştı.
- Test planına Türkçe diarization kanıt boşluğu ve kabul ön koşulları eklendi.

## 0.9.8 — 13.11.2026

- Türkçe düşük kaynak ASR adayları Turkish STT 66M v2 ve Uran STT Base araştırmaya eklendi; lisans/kalite kısıtları nedeniyle biri beklemeye, diğeri düşük öncelikli karşılaştırmaya alındı.
- ufakzeka-kulak modelinin NeMo, Transformers, sherpa-onnx ve Parakeet.cpp GGUF dışa aktarımları ile f32/q8_0 varyantları belgelendi.
- GGUF'nin yalnızca LLM modelleriyle sınırlı olmadığı, ancak her model/runtime çifti için ayrı destek gerektiği açıklandı; whisper.cpp'nin GGML biçimi kullandığı kuralı korundu.
- Benchmark tasarımı Parakeet.cpp adapter'ıyla güncellendi; 3 yeni düşük kaynak/model biçimi testi eklenerek senaryo kataloğu 51'e çıkarıldı.

## 0.9.7 — 13.11.2026

- 56.12 için yerel benchmark düzeneği tasarımı eklendi; test tanımı, motor adapter'ı, yerel orkestrasyon, metrik ve sonuç şeması ayrıştırıldı.
- Aynı modelin farklı runtime/quantization koşullarında değerlendirilmesi ve yerel ağsız test yürütme akışı tanımlandı.
- Test koşusu sonuçları için JSON şablonu eklendi; LLM, GGUF ve embedding kullanım sınırları benchmark bağlamında açıklandı.
- Test planı benchmark tasarımı ve koşu şablonuna bağlandı.

## 0.9.6 — 13.11.2026

- whisper.cpp, faster-whisper/CTranslate2, Transformers/PyTorch, WhisperX, pyannote, sherpa-onnx ve NVIDIA NeMo adaylarının görev, model biçimi, runtime ve lisans sınırları belgelendi.
- whisper.cpp'nin GGML biçimi kullandığı ve GGUF ile aynı olmadığı; VAD, forced alignment ve diarization işlevlerinin birbirinden farklı olduğu netleştirildi.
- Türkçe WhisperX hizalama modeli ile İngilizce/deneysel whisper.cpp tinydiarize sınırları kaydedildi.
- VAD, forced alignment ve runtime/quantization karşılaştırması için 4 yeni test senaryosu eklendi; katalog 48 senaryoya ulaştı.
- ASR motor araştırması, araçlar/yöntemler, test planı ve manifest yeni uyumluluk belgesiyle ilişkilendirildi.

## 0.9.5 — 13.11.2026

- 56.12 kontrollü ses kayıt protokolü ve kurgusal Türkçe okuma/doğal diyalog metin seti eklendi.
- Gönüllü rızası, anonim etiketleme, gerçek tek-miks konuşmacı ayrımı girdisi ve ayrı referans mikrofon/kanal yaklaşımı tanımlandı.
- Ana kayıt ile türev gürültü/telefon/codec örnekleri ayrıştırıldı; henüz gerçek gönüllü kaydı alınmadığı açıklandı.
- Test planı ve veri kümesi kaydı kontrollü ses protokolüne bağlandı.

## 0.9.4 — 13.11.2026

- Common Voice Spontaneous Speech 5.0 Türkçe veri kümesi doğal yanıt konuşması adayı olarak eklendi; 54 klip, 13 konuşmacı ve atanmamış split nedeniyle yalnız keşifsel kontrol olarak sınırlandı.
- IARPA Babel Turkish telefon konuşması paketi, LDC lisans/ücret koşulları ve 8 kHz A-law özellikleriyle kaydedildi.
- SpeechDataAI ticari Türkçe diyalog verisi ve SesMetin-v2 sentetik TTS kümesi ayrı kullanım kategorileri olarak belgelendi.
- Açık, kısıtlı, ticari ve sentetik veri kaynaklarının birbirinin yerine geçemeyeceği açıklandı; test planı güncellendi.

## 0.9.3 — 13.11.2026

- 56.12 Türkçe test veri kaynakları; split, lisans, kullanım kısıtları ve veri yapısı açısından ayrı ayrı kaydedildi.
- FLEURS tr_tr split sayıları ve Real-TurnTurk'ün ayrı konuşmacı kanalları gibi test tasarımını etkileyen ayrıntılar belgelendi.
- MediaSpeech Türkçe yapılandırmasının güncel metadata/README görünümündeki tutarsızlık ve TurkASR-Bench kaynak lisansı uyuşmazlığı açık risk olarak kaydedildi.
- İnsan referans transkripti için sözcüğü sözcüğüne anotasyon, zaman aralığı, belirsizlik, örtüşme ve anonim konuşmacı etiketleme kuralları önerildi.
- Veri kümesi ve anotasyon kayıtları için JSON şablonları eklendi.

## 0.9.2 — 13.11.2026

- 56.12 test planını uygulanabilir senaryolara dönüştüren katalog eklendi.
- Materyal kabulü, bütünlük, ses teknik kontrolü, ASR, diarization, zaman bağlantısı, performans, güvenlik, kurtarma ve rapor senaryoları kimlik ve önceliklerle tanımlandı.
- Testlerin sentetik/açık lisanslı/kontrollü pilot veri sınıfları ayrıştırıldı; senaryo kataloğunda test sonucu veya model kabulü iddiası bulunmadığı belirtildi.

## 0.9.1 — 13.11.2026

- 56.12 için veri kümesi/lisans incelemesi, insan referans anotasyonu, Türkçe WER normalizasyonu ve kritik hata sınıflarını tanımlayan ayrıntılı test planı eklendi.
- ASR model kalitesi ile MİHENK dağıtım/runtime performans testleri birbirinden ayrıldı.
- Diarization için DER bileşenleri, collar ve örtüşen konuşma raporlama yaklaşımı belgelendi.
- Yerel/çevrimdışı çalışma, RAM/VRAM/RTF, uzun kayıt, kurtarma ve uzman iş akışı testleri tanımlandı.
- Common Voice, FLEURS, MediaSpeech, Real-TurnTurk ve TurkASR-Bench kaynaklarının lisans/kapsam sınırlamaları kaydedildi; gerçek vaka materyalinin public depoya alınmaması tekrarlandı.

## 0.9.0 — 13.11.2026

- 56.12 modülü için görevlendirmeden teslim paketine kadar uçtan uca teknik iş akışı taslağı eklendi.
- Orijinal materyal/türev çalışma kopyası ayrımı, hash doğrulaması, ses envanteri, yerel ASR, isteğe bağlı diarization, uzman incelemesi, rapor ve teslim kapıları tanımlandı.
- 56.12 ile 56.11 kapsam sınırları ve otomatik sistemlerin uzman kanaatinin yerine geçemeyeceği ilkesi netleştirildi.
- SWGDE ses delili ve dijital ses iyileştirme rehberleri teknik kaynak olarak eklendi; Türkiye'de bağlayıcı mevzuat olmadıkları belirtildi.

## 0.8.0 — 13.11.2026

- Adalet Bakanlığı/UYAP'ın resmî Doküman Editörü, Adalet e-İmza ve Bilirkişi Portal araçları kaynaklarıyla ayrıştırıldı.
- Pardus'un TÜBİTAK BİLGEM tarafından sürdürülen Debian tabanlı işletim sistemi olduğu; UYAP Editörü'nün Bakanlık yazılımı olarak Pardus/Debian için de dağıtıldığı belgelendi.
- UYAP'ın tarihsel OpenOffice 2.4 kullanımı güncel onay gibi sunulmadan araştırma notuna eklendi.
- 56.12 için Whisper, TurkMedSTT M1, ufakzeka-kulak ve Vosk Turkish Small modelleri lisans, veri kökeni ve test sonuçlarıyla karşılaştırıldı.
- Bakanlıkça onaylı ASR yazılımı kamuya açık resmî kaynaklarda doğrulanamadığı kaydedildi.
- ASR'nin yerel/çevrimdışı çalışması, aynı test setinde en az iki aday karşılaştırması ve uyuşmazlıkların dinleme kuyruğuna alınması gereksinimleri eklendi.
- 56.12 araç/yöntem, UYAP akışı, modül mimarisi, test stratejisi ve karar kayıtları güncellendi.

## 0.7.0 — 13.11.2026

- MİHENK'in uzmanlık araçlarını tek kullanıcı arayüzünde sunan bütünleşik platform hedefi karara bağlandı.
- Modül/araç paketleri için manifest, imza, izin, lisans/SBOM, sandbox, güncelleme ve geri alma ilkeleri eklendi.
- LibreOffice/UNO, ONLYOFFICE, Collabora Online ve Apache OpenOffice seçenekleri lisans, offline, gömme ve format açısından karşılaştırıldı.
- UDF topluluk araçları incelendi; Apache 2.0 lisanslı udfpdf yalnızca okuma/dönüştürme PoC adayı, lisanssız veya ticari entegrasyonu yasaklı projeler kapsam dışı olarak kaydedildi.
- PDF.js, Apache PDFBox, OCRmyPDF ve Tesseract adayları incelendi.
- Tek rapor modeli ve DOCX/ODT/PDF/UDF çıktı adaptörleri yaklaşımı tasarlandı; teknoloji kararı verilmedi.
- Belge motoru ve modül güvenliği için test stratejisi güncellendi.

## 0.6.1 — 13.11.2026

- İki tamamen kurgusal görevlendirme metni ve beklenen Görev Profili sonuçları eklendi.
- Materyal sayısı, görev süresi, tebliğ tarihi, teslim kanalı ve rapor formatının görevler arasında değişebildiği sentetik testle gösterildi.
- Görev Profili, kaynak izi ve istisna yönetimi kararları ADR-018–020 olarak kaydedildi.
