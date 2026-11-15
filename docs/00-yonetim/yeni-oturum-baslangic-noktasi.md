# MİHENK — Yeni Oturum Başlangıç ve Devir Noktası

> **Son güncelleme:** 15 Kasım 2026  
> **Yeni oturumda ilk okunacak belge:** Bu dosya  
> **Tasarım durumu:** Wireframe v0.5 proje sahibi tarafından kabul edildi. Uygulama mevcut prototip üzerinden ilerletilecek.  
> **İlk sonraki hedef:** Mevcut uygulamanın canlı durumunu görmek; main, eski dallar ve issue'ları denetleyip kabul edilen tasarıma göre uygulama planını çıkarmak.

## 1. Proje kaynakları

- **Araştırma/ürün deposu:** https://github.com/azmisahin-gov/mihenk-arge
- **Uygulama deposu:** https://github.com/azmisahin-gov/mihenk

Araştırma deposunda mevzuat, ürün/sistem kararları, wireframe ve kabul kriterleri bulunur. Uygulama deposunda kaynak kodu, test, CI ve masaüstü paketleri bulunur. Gerçek bilirkişi dosyası, ses, transkript, dosya numarası veya kişisel veri hiçbir public depoya, issue'ya, PR'a, log'a veya CI artifact'ına konmaz.

## 2. Ürün hedefi ve kullanıcı işinin özü

İlk kullanılabilir teslimat 56.12 — Ses Kayıtlarının Metne Dönüştürülmesi kontrollü bilirkişi pilotudur. Uzun vadede ortak çekirdek ve bağımsız uzmanlık modülleriyle genişleyen MİHENK hedeflenir.

Bilirkişinin asıl işi motor seçmek veya uzun formlar doldurmak değildir:
1. Görevlendirme belgesini eklemek; sistemin görev bilgilerini/sorularını otomatik çıkarması.
2. Aynı göreve ait materyalleri eklemek; sistemin envanter ve işlem işlerini yapması.
3. ASR'nin kontrol işaretlerine göre önce şüpheli ses bölümlerine odaklanmak; sesi dinleyip metni düzeltmek.
4. Kendisine yöneltilen sorulara hızlıca erişip kaynaklarıyla cevaplamak.
5. Tek, okunabilir ve görevlendiren merciye uygun raporu tüm sayfalarıyla kontrol etmek.
6. Gerekirse çalışmasını ikinci uzmana/denetçiye kanıt iziyle sunabilmek.

MİHENK kelime, hukukî yorum veya bilirkişi kanaati uydurmaz. Nihai transkript, bulgu, yanıt, kanaat, imza ve resmî teslim bilirkişinin kontrolündedir.

## 3. Kabul edilen tasarım — Wireframe v0.5

**15.11.2026 tarihinde proje sahibi v0.5'i mevcut haliyle kabul etti.** Uygulama geliştirme için tasarım temelidir. Bu kabul, mevcut uygulamanın tamamlandığı, 56.12 bilirkişi kabulü, bağımsız güvenlik incelemesi veya UYAP uyumluluğu anlamına gelmez.

- [Wireframe v0.5 açıklama ve uygulama kabul listesi](../02-urun/56-12-wireframe-v0.5.md)
- [01 Modül ve motor hiyerarşisi](../02-urun/wireframe-v0.5-01-modul-ve-motor-hiyerarsisi.svg)
- [02 Yeni görevlendirme akışı](../02-urun/wireframe-v0.5-02-yeni-gorevlendirme-akisi.svg)
- [03 Görev çalışma alanı](../02-urun/wireframe-v0.5-03-gorev-calisma-alani.svg)
- [04 Ana ses inceleme tezgâhı](../02-urun/wireframe-v0.5-04-ana-ses-inceleme-tezgahi.svg)
- [05 Tek rapor ve A4 önizleme](../02-urun/wireframe-v0.5-05-tek-rapor-a4.svg)
- [06 Daraltılabilir ana menü](../02-urun/wireframe-v0.5-06-daraltilebilir-ana-menu.svg)
- [56.12 Kalite Güvencesi ve Denetim Modeli](../02-urun/56-12-kalite-ve-denetim-modeli-v1.0.md)

v0.3 ve v0.4 kabul edilmemiş tarihsel taslaklardır; v0.5'in yerine kullanılmamalıdır.

### Kesin ürün davranışları

- **Uzmanlık Alanlarım** profil bilgisidir; **Uzmanlık Modülleri** yazılım iş akışlarıdır; **56.12 → Motorlar ve Modeller** yerel ASR/yardımcı işlem ayarlarının yeridir.
- Motor görev başına seçilmez. Test edilmiş etkin yerel çalışma profili otomatik kullanılır; gerçek motor/model/sürüm ve parametreler işlem kaydında tutulur.
- Yeni görevlendirme katı wizard değildir. İlk belge eklenince otomatik kaydedilen görev taslağı oluşur. Görevlendirme okuma/çıkarım başlar; materyal o anda veya sonradan eklenir; Görevlerim'e dönüş her zaman mümkündür.
- Ses ekranı bütün kayıtları ve bütün transkripti erişilebilir tutar. Öncelik kuyruğu yalnızca önce kontrol edilmesi önerilen bölümleri öne çıkarır; model güven işareti doğruluk yüzdesi değildir.
- Konuşmacı ayrımı isteğe bağlıdır; kayıt içi “Konuşmacı A/B” etiketi üretir, kişi kimliği belirlemez. Otomatik diarization ilk pilot için zorunlu kabul edilmemiştir.
- Ses iyileştirme araçları orijinal dosyayı değiştirmez; türetilmiş kopyada ve geri alınabilir işlem kaydıyla yürütülür. Gelişmiş denoise/spectrogram gibi araçlar test edilmeden çalışıyor gösterilmez.
- ASR segmentleri düzenleme ve zaman içinde gezinme birimleridir. Nihai rapor dökümü konuşmacı sıralı, zaman damgalı okunabilir paragraflardır.
- Her görevde tek ana rapor ve aynı pakette ekler vardır. Merciye uygun referans iskeleti otomatik eşleştirilir; tek ve evrensel zorunlu resmî şablon iddiası yoktur. UYAP Editör aç/kaydet/yeniden aç testi geçmeden “UYAP'a hazır” denmez.
- Serbest metin üreten LLM/NLP nihai kelime kaynağı değildir. VAD, sınırlı noktalama ve diarization gibi yardımcılar ancak test edilip modülde etkinleştirildiğinde kullanılabilir.

## 4. Kalite ve denetim modeli

Aşağıdaki katmanlar birbirinin yerine geçmez:

1. **Bilirkişinin kendi kontrolü:** görev kapsamı, materyal, tüm ses kayıtları, transkript kontrol durumu, soru/yanıt/dayanak bağlantıları ve raporun bütün A4 sayfaları.
2. **Bağımsız dosya/rapor incelemesi:** gerektiğinde ikinci bilirkişi/denetçi için kullanıcı tarafından gözden geçirilmiş salt okunur denetim paketi; ana kayıt ve rapor değişmeden kalır.
3. **MİHENK ürün denetimi:** K-01–K-12 kanıtları, yazılım/model sürümü, testler, güvenlik, kullanılabilirlik, UYAP çıktı kabulü ve açık risklerden oluşan sürüm bazlı ürün kalite dosyası.

Ayrıntı ve uygulama aşamaları: [Kalite Güvencesi ve Denetim Modeli v1.0](../02-urun/56-12-kalite-ve-denetim-modeli-v1.0.md).

## 5. Araştırma deposu — birleştirme ve son durum

- Araştırma PR'ı: [PR #12 — Wireframe v0.5](https://github.com/azmisahin-gov/mihenk-arge/pull/12).
- PR yalnızca araştırma/ürün dokümanı ve SVG tasarımlarını içerir; uygulama kodu veya gerçek vaka verisi içermez.
- [PR #12](https://github.com/azmisahin-gov/mihenk-arge/pull/12) 15.11.2026 tarihinde squash merge ile `main` dalına alındı.
- Merge commit: `3b526885beec52aeab23c0b0d56514492e4050a5`.
- PR kapsamı yalnızca dokümantasyon ve SVG wireframe dosyalarıdır; uygulama deposuna kod aktarılmadı.
- v0.5 tasarımı ürün sahibi tarafından kabul edildi; teknik ve meslekî testler ayrıca açık kalır.

## 6. Uygulama deposunun 15.11.2026 başlangıç fotoğrafı

### Main dalında görülen yetenekler

Uygulama main dalındaki README ve kaynak dosyaları üzerinden yapılan ilk incelemede şu prototip yetenekleri belgeleniyor:

- Görev/atama alanı, görev bazlı çalışma ve ses materyali kuyruğu.
- AES-256-GCM şifreli yerel kasa; 240 MiB'ye kadar akışlı ses içe alma ve SHA-256.
- Şifreli kopyanın bağımsız read-back hash kontrolü; Symphonia decoder tabanlı teknik metadata.
- Şifreli kaynaktan üretilen gerçek waveform; çözümleme hatasında temsili waveform gösterilmemesi.
- Yerel SEDA v0.1 ASR kurulumu ve akışlı transkripsiyon; model kurulduktan sonra ağsız ses işleme.
- Ham ASR taslağı ve uzman düzeltmesi ayrımı; segment zamanları ve revizyon geçmişi.
- Manuel anonim konuşmacı etiketleri ve kanal bilgisinin ayrı tutulması; otomatik diarization yok.
- Şifreli kasa yedeği/geri yükleme.
- Görev sorularına ayrı yanıtlar ve transkript segmentlerine dayanak bağlantısı; DOCX/ODT taslakları ve bazı QA kontrolleri.

Bu yetenek listesi README'de belgelenen durumdur; 56.12 pilot kabulünün geçtiği anlamına gelmez. Bir sonraki oturumda bunlar temiz checkout'ta test/uygulama çalıştırmasıyla doğrulanmalıdır. Kullanıcının daha önce bildirdiği preview 0.1.0-53'tür; o sürümün bugün en güncel release olduğu varsayılmamalı, güncel main ve release/preview yeniden doğrulanmalıdır.

### Eski uygulama dalları — henüz silinmedi

15.11.2026 tarihli Git karşılaştırması, her dalın main ile farkını gösteriyor. Hiçbir dal bu oturumda merge veya delete edilmedi:

| Dal | Main'e göre durum | Değiştirdiği başlıca dosyalar | İlk değerlendirme |
|---|---:|---|---|
| **feat/56-12-report-question-answers** | 16 ahead / 4 behind; diverged | src/App.tsx, src/domain/assignment.ts, src/domain/report.ts, stiller, testler | Soru-yanıt ve rapor özelliklerini main'deki mevcut işlevlerle karşılaştır; doğrudan merge etme |
| **feat/56-12-transcript-review-queue** | 6 ahead / 0 behind | src/App.tsx, src/domain/transcript.ts, stiller, testler | Main'e göre daha yakın; inceleme kuyruğunun main'de eksik kalan kısmı varsa seçici taşı |
| **feat/56-12-transcript-revision-history** | 33 ahead / 5 behind; diverged | src/App.tsx, src-tauri/src/asr.rs, audio/transcript/vault, testler | ASR/transkript sürümlemesi ve mevcut main değişiklikleriyle çakışma riski yüksek; ayrıntılı commit/diff incelemesi olmadan merge etme |

Uygulama deposunda açık PR aramasında sonuç bulunmadı. Bu üç dalı **henüz silme**. Önce her daldaki commit ve testleri main ile karşılaştır; korunmaya değer değişiklikleri yeni, temiz bir çalışma dalına seçici taşı; doğrula; ancak sonra eski dal için kapatma/silme kararı ver.

### Açık uygulama issue'ları

15.11.2026 tarihli açık issue aramasında şu yedi kayıt bulundu:

- [#3 — 56.12 ilk pilot kabul kriterleri](https://github.com/azmisahin-gov/mihenk/issues/3): ana pilot kabul/epic kaydı. Body'de “uygulamada henüz ASR motoru yok” gibi eski ifadeler var; main README SEDA entegrasyonunu belgeliyor. Tüm checklist yeniden kanıtla eşlenmeli.
- [#29 — Yerel ASR ve devam ettirilebilir kuyruk](https://github.com/azmisahin-gov/mihenk/issues/29): body main'de ASR bulunmadığını söylüyor; bu tarihsel. SEDA bağlantısı var, ancak idempotent iş defteri/kaldığı yerden devam, benchmark, provenance ve uzman kabulü ayrıca doğrulanmalı.
- [#30 — Materyal kabulü ve bütünlük](https://github.com/azmisahin-gov/mihenk/issues/30): body read-back hash ve decoder metadata'yı eksik gösteriyor; main README bu özelliklerin uygulandığını söylüyor. Gerçek kod/test ile doğrula ve issue body/checklist'ini güncelle.
- [#31 — Zaman bağlantılı transkript ve revizyon geçmişi](https://github.com/azmisahin-gov/mihenk/issues/31): body özelliklerin eksik olduğunu söylüyor; main README ham ASR/uzman ayrımı ve revizyon geçmişini belgeliyor. Tam kabul senaryosunu çalıştır.
- [#32 — Tek uygulama ses çalışma alanı](https://github.com/azmisahin-gov/mihenk/issues/32): body eski tek ekran/temsili waveform durumunu anlatıyor; main README artık görev alanı ve gerçek waveform bildiriyor. Kabul edilen v0.5 ile UI karşılaştırması yap ve açık eksikleri tespit et.
- [#33 — Soru bağlantılı rapor ve QA](https://github.com/azmisahin-gov/mihenk/issues/33): main README DOCX/ODT soru-yanıt/dayanak ve QA kontrolleri olduğunu bildiriyor; gerçek rapor şablonu, A4 önizleme, PDF/Office biçim kontrolü ve denetim paketi hâlâ doğrulanmalı.
- [#34 — Çevrimdışı, görev yalıtımı ve çökme/geri yükleme E2E](https://github.com/azmisahin-gov/mihenk/issues/34): kapsamlı E2E, offline/ağ gözlemi, görev sızıntısı ve zorla sonlandırma/kurtarma kabulü için ana açık paket.

Bu issue'ların updated_at tarihleri 14 Kasım 2026; main kodunda #24/#28/#35/#36 sonrasında değişiklikler bulunduğundan gövde/checkbox'lar bayat olabilir. İlk uygulama oturumunun işi issue'ları otomatik kapatmak değil, her kabul maddesini kanıta göre yeniden sınıflandırmaktır.

### Önceki kullanıcı tarafından bildirilen uygulama blokajları

- Pencerenin X kapatma davranışı düzgün kapanmıyor.
- Kasa yeniden açıldığında listede görünen bir ses seçili/oynatılabilir şekilde geri gelmiyor ve 00:00 gösterebiliyor.
- Dayanak/segment seçicisi dar alanda kullanımı bozuyor.
- Bir updater hatası görülmüştü; nedeni henüz kanıtlanmadı.

Bunların bugün main'de sürüp sürmediği canlı uygulama çalıştırmasıyla teyit edilecek. Issue yoksa tekrar üretilebilir testle yeni issue açılacak; çözüldüyse kanıtla kapatılacak.

## 7. Yeni oturumda yapılacak iş sırası

**A — Önce canlı mevcut sürümü gör**
1. Araştırma PR #12'nin main'e birleştiğini ve güncel commit'i doğrula.
2. Uygulama main dalını ve Releases/preview durumunu yeniden oku.
3. Temiz checkout'ta test/build komutlarını çalıştır: **npm ci**, **npm test**, **npm run check**, **npm run build**; Tauri/Rust test ve build'ini hedef OS'lerde doğrula.
4. Mevcut uygulamayı başlat ve hiçbir kod değişikliği yapmadan görev açma, ses içe alma, oynatma, waveform, SEDA/transkript, soru/yanıt ve rapor çıktısını göster. Gerçek vaka kullanma; sentetik/test materyaliyle çalış.
5. Kullanıcının elindeki 0.1.0-53 preview ile güncel main/preview davranışını farklarıyla kaydet. Sürüm etiketi doğrulanmadan “en son” denmez.

**B — Sonra dalları ve issue'ları temizle**
1. Üç eski dalı commit/diff/test bazında tek tek incele; main'e göre değişiklikleri dosya dosya ayır.
2. Çalışan veya eksik işi tamamlayan değişiklikleri gerekiyorsa yeni temiz feature dalına seçici taşı.
3. Her seçici taşıma sonrasında testleri çalıştır ve v0.5 ekran/akış maddelerine eşle.
4. Yinelenen issue'ları birleştir; yanlış/eski “yapılmadı” metinlerini düzelt; yalnız kanıtla tamamlanan maddeleri işaretle.
5. Eski dalları ancak kurtarılması gereken commit kalmadığı ve ilgili değişikliklerin main'e taşındığı doğrulandıktan sonra temizle.

**C — v0.5'i gerçek uygulamaya dönüştür**
1. Tasarım → mevcut ekran/kod → eksik özellik → issue/PR → test kanıtı matrisini çıkar.
2. Öncelik: gerçek görev listesi ve otomatik görevlendirme kabulü; çoklu materyal; ses inceleme tezgâhı; uzman düzeltme ve kontrol kuyruğu; çoklu soru/dayanak; tek A4 rapor.
3. ASR/yardımcı motor yönetimini 56.12 modül ayarlarına bağla; kullanıcıya görev başına model seçimi yaptırma. SEDA mevcut prototipte bir adaydır; nihai motor seçimi benchmark'a bağlıdır.
4. Denetim modelini aşamalı uygula: önce bilirkişi öz kontrolü ve işlem/rapor izi; sonra gizlilik kontrolü olan salt okunur denetim paketi; ürün kalite dosyası CI/QA'da ayrı tutulur.
5. Her dilimi çalışan uygulamada göster; arayüz görüntüsü tek başına yeterli değildir, akış gerçekten çalışmalıdır.

## 8. Güvenlik ve kabul sınırları

- Public GitHub/CI'da yalnız sentetik veya lisansı/izni doğrulanmış veri kullan.
- Gerçek vaka sesi/transkripti/raporu GitHub'a yüklenmez.
- ASR confidence gerçek doğruluk yüzdesi gibi sunulmaz; belirsiz ses tahminle doldurulmaz.
- Hash sesin özgünlüğünü/manipüle edilmediğini tek başına kanıtlamaz.
- Gerçek ASR başarımı izinli insan referans veri setinde WER/CER ve kritik hata örnekleriyle ölçülür; SEDA, Whisper veya başka model test edilmeden kazanan ilan edilmez.
- Otomatik diarization, gelişmiş denoise, source separation ve spektrogram araçları teknik/lisans testinden geçmeden zorunlu ilk pilot kapsamına sokulmaz.
- UYAP Portal otomasyonu, e-imza anahtarı/PIN yönetimi ve bilirkişi adına resmî teslim kapsam dışıdır.
- CI/derleme yeşil olması uzman, hukuk, güvenlik veya UYAP kabulü anlamına gelmez.
- K-01–K-12 kanıtı ve gerekli uzman/güvenlik değerlendirmesi tamamlanmadan 56.12 “pilot kullanıma hazır” ilan edilmez.

## 9. Yeni oturum için kopyalanabilir başlangıç talimatı

> MİHENK projesine devam ediyoruz. Önce mihenk-arge deposundaki docs/00-yonetim/yeni-oturum-baslangic-noktasi.md ve bağlantılı v0.5/kalite-denetim belgelerini oku; PR #12'nin main'e birleştiğini ve merge commit'ini doğrula. Wireframe v0.5 proje sahibi tarafından kabul edilmiştir. Sonra mihenk uygulama deposunun main dalını ve güncel preview sürümünü oku; kod değiştirmeden uygulamayı temiz ortamda build edip çalıştır ve mevcut canlı işlevleri sentetik verilerle göster. Özellikle mevcut main'de zaten bulunan görev, şifreli materyal, gerçek waveform, SEDA yerel ASR, transkript revizyonu ve soru/rapor işlevlerini yeniden yazma. Üç eski feature dalını (report-question-answers, transcript-review-queue, transcript-revision-history) main ile commit/diff/test bazında karşılaştır; hiçbir dalı erken silme veya doğrudan merge etme. Açık #3, #29–#34 issue'larının bayat gövdelerini koddaki gerçekle karşılaştırıp kanıtla güncelle. Önce mevcut çalışan sürümü göster, sonra v0.5'e göre fark/backlog matrisi çıkar ve küçük testli PR'larla ilerle. Bilirkişi öz kontrolü, bağımsız denetim paketi ve MİHENK ürün kalite dosyasını ayrı katmanlarda uygula. Gerçek vaka verisini GitHub/CI'ya koyma.

---

**Kritik çalışma ilkesi:** Kullanıcı v0.5 tasarımını kabul etti. Bundan sonra amaç yeniden tasarım yapmak değil, mevcut çalışan uygulamayı kaybetmeden kabul edilmiş akışa bağlamak; eksik olanı kanıtla tamamlamak ve bilirkişinin gerçek işini canlı masaüstü uygulamada göstermektir.
