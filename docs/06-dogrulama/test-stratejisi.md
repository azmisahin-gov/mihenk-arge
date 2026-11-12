# Test Stratejisi

> **Durum:** TASLAK — clean-room MİHENK geliştirme kararına bağlı  
> **Güncelleme:** 13 Kasım 2026

## Test katmanları

1. **Mevzuat ve resmî şablon doğrulama:** Her gereksinim güncel resmî kaynak/maddeye bağlanır; hukukçu onayı bekleyenler ayrıca işaretlenir.
2. **Alan doğrulama:** Her uzmanlık modülü için aktif bilirkişi iş akışını, terimleri ve teknik sınırları kontrol eder.
3. **Birim testleri:** Dosya sayımı, metadata, hash, kopya ilişkisi, görev durum geçişi, rapor alanı ve şablon kuralları.
4. **Entegrasyon testleri:** Çoklu dosya içe alma, transkripsiyon kuyruğu, ses-metni senkronizasyonu, dışa aktarma ve uygulama içi olay kaydı.
5. **Güvenlik:** Path traversal, kötü amaçlı medya, güvenli decoder sınırı, shell injection, yedek sızıntısı, ağ trafiği ve imzalı güncelleme doğrulaması.
6. **Kurtarma:** Crash, power loss, DB corruption, partial output, tekrar başlatma, yedek/restore.
7. **Kullanılabilirlik:** İlk kurulum, ilk açılış, hata açıklamaları, klavye/oynatıcı ergonomisi ve yoğun işte odaklanma.
8. **İnsan faktörü:** Dinleme, tekrar, düzeltme, rapor hazırlığı ve son kontrol süresinin ayrı ölçülmesi.
9. **Pilot:** Sentetik/açık lisanslı test materyali; uzman kabulü ve görev akışı ölçümü.

## 56.12 özel otomatik testleri

- Sekiz ses dosyası içeren görevde içeri alınan, işlenen ve rapora bağlanan dosya sayıları eşleşiyor mu?
- Aynı adlı farklı klasör dosyaları yanlışlıkla birbirinin üzerine yazılıyor mu?
- Eksik/bozuk/codec desteklenmeyen dosya açık uyarı veriyor mu?
- Orijinal hash içe alma sonrasında ve işlem sonunda aynı mı?
- Çalışma kopyasının her türetilmiş çıktıyla ilişkisi kayıtlı mı?
- ASR metni, zaman damgası ve kaynak dosyaya geri döndürülebiliyor mu?
- Belirsiz/fısıltılı/örtüşen bölüm sessizce tahmin edilmek yerine işaretleniyor mu?
- Konuşmacı etiketleri sabit ve nötr mü; gerçek kişi kimliği iddiası üretilmiyor mu?
- Alıntı ve önemli bölüm raporda doğru kaynak dosya/zaman aralığına bağlanıyor mu?
- Rapor export'unda eski görevden kalan ad, tarih, dosya numarası, yer tutucu veya ek var mı?
- Kullanıcı son onay vermeden uygulama nihai raporu onaylanmış veya UYAP'a gönderilmiş göstermiyor mu?

## Test verisi ilkeleri

- Önce sentetik diyaloglar ve insan kontrolünden geçmiş açık lisanslı Türkçe konuşma verisi kullan.
- Her örnek için kaynak, sürüm, lisans, checksum ve kullanım amacı kaydet.
- Common Voice gibi okunmuş konuşma veri kümelerini temel ASR regresyon testi olarak kullan; bunları doğal adli konuşma, ses özgünlüğü veya mahkeme kayıtları için temsilî kabul etme.
- Fısıltı, örtüşme, çoklu konuşmacı ve uzun kayıt senaryoları için ayrı, sentetik ve lisans/izin koşulları belli test örnekleri oluştur.
- Gerçek dava kaydı, UYAP ekran görüntüsü ve kişisel veri public CI, fixture veya log'a giremez.

## Kabul kapısı

- 0 açık kritik güvenlik bulgusu.
- Yedek/geri yükleme acceptance test geçer.
- Orijinal materyal değişmezliği ve kopya izlenebilirliği test edilir.
- Tüm içe alınan dosyalar envanterde görünür; işlenmeyenler nedenleriyle işaretlidir.
- Resmî teslimi yanlış gösteren hiçbir otomatik durum yoktur.
- Uzman görüşü ile AI/ASR çıktısı ayrı tutulur.
- Konuşmacı sıralaması kimlik belirleme olarak sunulmaz.
- Tüm hata senaryoları kullanıcıya açıklanır.

Test sayısı başlı başına kalite kanıtı değildir. Her testin hangi riski kapsadığı, beklenen sonucu ve referans verisinin kaynağı kaydedilmelidir.

## Kaynaklar

- [NISTIR 8387 — Digital Evidence Preservation](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [Mozilla Common Voice — Datasets](https://commonvoice.mozilla.org/bas/datasets)
