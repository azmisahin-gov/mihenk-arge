# 56.12 Araçlar ve Yöntemler

> **Durum:** Resmî araç ve ASR araştırmasıyla güncellendi — üretim aracı seçilmedi  
> **Araştırma tarihi:** 13 Kasım 2026  
> **Motor uyumluluğu:** [56.12 motor/runtime uyumluluk araştırması](56-12-motor-runtime-uyumluluk-arastirmasi.md)

## 1. Araçların rolü

56.12, ses kayıtlarının metin hâline dönüştürülmesi alanıdır. MİHENK'in 56.12 modülü kendi arayüzünden ses materyali kabulü, teknik inceleme, yerel ASR, dinleme/düzeltme, zaman bağlantısı ve rapor hazırlığını yürütmelidir.

MİHENK'in amacı kullanıcıya ayrı Audacity/FFmpeg/ASR web sayfası açtırmak değildir. Alttaki motorlar, lisans ve güvenlik incelemesinden sonra uygulama ile birlikte paketlenmiş yerel araç veya izole worker olabilir. Kullanıcı tek MİHENK uygulamasında kalır.

## 2. Bakanlıkça doğrulanmış resmî araçlar

- UYAP Doküman Editörü Adalet Bakanlığı Bilgi İşlem biriminin geliştirdiği resmî kelime işlemci ve UYAP ile entegre araçtır.
- UYAP Editör Windows, macOS, Pardus/Debian ve mobil platformlar için resmî dağıtım sayfasında sunulmaktadır.
- Adalet e-İmza, UYAP'ın 2026 duyurularında yer alan resmî imza/giriş uygulamasıdır.
- İncelenen kamuya açık resmî kaynaklarda 56.12 için Bakanlıkça onaylandığı belirtilen ASR modeli/konuşma tanıma paketi doğrulanamamıştır.

MİHENK'in ASR adayları bu nedenle “Bakanlık onaylı” değil; açık kaynak ve MİHENK tarafından test edilmiş yardımcı modeller olarak ele alınacaktır.

## 3. ASR adayları

İlk karşılaştırma:
- Whisper Large v3 / turbo (MIT) + whisper.cpp veya doğrulanmış yerel çalışma zamanı.
- TurkMedSTT Whisper Large v3 Türkçe Genel M1 (Apache 2.0 model kartı; veri kaynakları ayrıca lisans kontrolünden geçer).
- ufakzeka-kulak (Apache 2.0; küçük çevrimdışı aday; konuşma diyaloğunda hata artışı nedeniyle ikincil).
- Vosk Turkish Small 35 MB (Apache 2.0; WER “TBD”, yalnız düşük öncelikli karşılaştırma).

Bu seçeneklerin hiçbirinin adli seslerde doğruluğu kabul edilmiş sayılmaz. Aday ayrıntıları `docs/03-uzmanlik-modulleri/ilk-pilot/asr-motor-arastirmasi.md` belgesindedir.

## 4. Ses motorlarının görev sınırları

- **ASR** metin taslağı üretir.
- **VAD** konuşma olan aralıkları belirler; konuşmacı ayrımı yapmaz.
- **Forced alignment** önceden hazırlanmış metne zaman aralığı önerir; metnin doğruluğunu teyit etmez.
- **Diarization** kayıt içindeki anonim konuşmacı kümelerini ayırır; gerçek kimlik belirlemez.
- **Source separation** karışmış kaynakları ayrı kanallara ayırmaya çalışır; ilk sürüm zorunluluğu değildir.
- **Speech enhancement** sesin işitilebilirliğini değiştirebilir; yalnız türev kopyada ve karşılaştırmalı testle değerlendirilir.

Bu motorlar arka planda farklı teknoloji kullanabilir; uzman tek MİHENK arayüzünde kalır. Adayların model biçimi, runtime, lisans ve bellek koşulları [uyumluluk araştırmasında](56-12-motor-runtime-uyumluluk-arastirmasi.md) ele alınmıştır.

## 5. Ses materyali ilkeleri

- Orijinal dosya salt okunur ve hash ile kaydedilmiş kalır.
- ASR ön işleme (kanal seçimi, yeniden örnekleme, ses seviye düzenleme, kesit çıkarma) yalnız çalışma kopyasında yapılır.
- Her türev dosyada kaynak hash, işlem, araç/model sürümü ve parametreler saklanır.
- Duyulmayan ses tahminle doldurulmaz; belirsiz zaman aralığı açıkça işaretlenir.
- Gürültü azaltma veya ses iyileştirme çıktısı orijinalin yerine geçmez ve yeni bir türev olarak kaydedilir.
- ASR, sesin özgünlüğünü/manipülasyonunu doğrulamaz.
- Konuşmacı sıralaması kişi kimliği, yaş, cinsiyet veya biyometrik teşhis değildir.

## 6. İnsan incelemesi ve zaman bağlantısı

- Transkript, kaynak ses ve zaman konumuyla birlikte gösterilir.
- Kullanıcı bir metin parçasına tıklayınca ilgili ses aralığına gidebilir.
- Tekrar dinleme, hız ayarı ve ses dalga formu aynı MİHENK arayüzünde bulunur.
- Birden fazla ASR motoru kullanılırsa farklı sonuçlar birleştirilip doğrulanmış gibi sunulmaz; uyuşmayan bölümler bilirkişinin dinleme kuyruğunda öne çıkarılır.
- İnsan düzeltmeleri kaynak model çıktısından ayrı sürüm ve olay kaydı taşır.

## 7. Kalite ölçümü

- WER/CER insan tarafından doğrulanmış referans transkriptle hesaplanır.
- Aksan, telefon kalitesi, düşük ses, fısıltı, arka plan gürültüsü, üst üste konuşma, özel adlar, sayı/tarih ve sessizlik ayrı test sınıfıdır.
- Sessizlikte uydurma metin, cümle atlama ve konuşmacı karışması ayrı hata sınıfı olarak ölçülür.
- İşlem süresi, bellek, CPU/GPU kullanımı, gerçek zaman katsayısı ve kesinti sonrası devam ölçülür.
- Model güven puanı, bilirkişi kanaati veya adli doğruluk garantisi değildir.

## 8. Adli kapsam sınırı

56.12 transkripsiyon desteği ile 56.11 adli ses/görüntü inceleme ve çözümlemesi birbirine karıştırılmaz. Konuşmacı kimliklendirmesi, ses karşılaştırması, montaj/manipülasyon incelemesi ve kaydın özgünlüğü ayrı yöntem ve uzmanlık gerektirebilir; bu modül bunları otomatik olarak yapmış sayılmaz.

## 9. Kaynaklar

- [Bilirkişilik Temel ve Alt Uzmanlık Alanları](https://bilirkisilik.adalet.gov.tr/)
- [UYAP Doküman Editörü](https://www.uyap.gov.tr/UYAP-Editor)
- [56.12 Türkçe ASR motor araştırması](asr-motor-arastirmasi.md)
- [56.12 motor/runtime uyumluluk araştırması](56-12-motor-runtime-uyumluluk-arastirmasi.md)
- [SWGDE Best Practices for Forensic Audio v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
