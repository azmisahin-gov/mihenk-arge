# Pilot Planı

> **Durum:** KARAR BEKLİYOR — MİHENK uygulaması henüz geliştirilmedi  
> **Güncelleme:** 13 Kasım 2026

## Pilot amacı

MİHENK'in sıfırdan geliştirilecek ilk sürümünün bilirkişinin gerçek görev akışını ne ölçüde desteklediğini; materyal envanteri, dosya bütünlüğü, inceleme ergonomisi, insan düzeltme süresi, rapor tamlığı ve hata toparlama bakımından ölçmek. Pilot, hukukî geçerlilik sertifikası veya bilirkişi kanaatinin otomatik doğrulanması değildir.

56.12 ilk test senaryosudur; seçilmiş tek ürün modülü veya kesin MVP değildir.

## Pilot ön koşulları

1. Ürün ve MVP kapsamının proje sahibi tarafından onaylanması.
2. Mesleki iş akışı ve uzmanlık sınırlarının bilirkişi tarafından doğrulanması.
3. Rapor şablonu ve kontrol listesi kaynağının güncel sürümünün teyit edilmesi.
4. Güvenlik/veri sınıflandırması, saklama, yedekleme ve silme politikasının hukukçu/uzman incelemesinden geçmesi.
5. MİHENK'in eski transkripsiyon örneklerinden kod, mimari, veri modeli veya bağımlılık taşımadan sıfırdan geliştirilmesi.
6. Gerçek vaka verisi kullanılacaksa ayrı yetkilendirme, hukuki dayanak, erişim sınırı, saklama ve silme planının tamamlanması.

## Sentetik ve açık veri stratejisi

- İlk otomatik testler sentetik olarak oluşturulan Türkçe diyalog ve açık lisans koşulları doğrulanmış kamuya açık konuşma örnekleriyle yapılır.
- Mozilla Common Voice 27.0 Türkçe veri kümesi CC0-1.0 lisansıyla listelenmiştir; bu tür veri ASR temel/regresyon testleri için adaydır. Okunmuş cümlelerden oluşan konuşma verisi, gerçek adli kayıtları, doğal diyalogları, fısıltıyı, üst üste konuşmayı veya kayıt cihazı artefaktlarını tek başına temsil etmez.
- Çoklu konuşmacı, örtüşme, fısıltı, düşük ses, gürültü ve uzun kayıt gibi senaryolar için lisansı/izinleri açık sentetik test diyalogları hazırlanır.
- Test verisinin kaynağı, sürümü, lisansı, alınma tarihi, checksum ve kullanım amacı bir veri manifestinde tutulur.
- Büyük veri kümesinin tamamı GitHub'a commit edilmez. CI için küçük, sabitlenmiş test alt kümesi indirilir veya sentetik test dosyaları kullanılır; doğrulama hash/checksum ile yapılır.
- Gerçek dava dosyaları, mahkeme sesleri, UYAP ekranları veya gerçek kişi bilgileri public test verisi yapılmaz.

## Pilot aşamaları

1. **Referans görev tanımı:** Sekiz dosyalı/uzun kayıt örneği gibi çoklu materyal görev senaryosunu sentetik veriyle kur.
2. **Referans içerik:** Her ses için insan tarafından kontrol edilmiş referans metin, zaman aralıkları ve belirsiz bölüm etiketleri hazırla.
3. **Materyal kabul testi:** Dosya envanteri, sayım, hash, kopya, virüs taraması, okunabilirlik ve çalışma kopyası.
4. **İnceleme testi:** Transkripsiyon, ses-metni senkronizasyonu, tekrar dinleme, düzeltme, konuşmacı sırası ve önemli bölüm bağlantısı.
5. **Rapor testi:** Doğru merci şablonu, zorunlu bölüm, cevaplanmış sorular, ekler, eski görev verisi sızıntısı ve export.
6. **İnsan faktörü testi:** Görev tamamlama süresi; dinleme, düzeltme, not ve rapor hazırlığı ayrı ölçülür.
7. **Kurtarma/güvenlik testi:** Çökme, kesinti, kısmi çıktı, bozuk medya, zararlı dosya, yedek ve restore.
8. **Uzman kabulü:** Bilirkişi gerçek görev akışıyla kullanılabilirliği ve mesleki sınırı değerlendirir; proje sahibi go/no-go kararı verir.

## Başarı ölçütleri

- Tüm içe alınan dosyaların envanterde görünmesi.
- Hiçbir orijinal dosyanın değişmemesi.
- Kopya/çıktı ilişkisinin izlenebilir olması.
- Kritik transkripsiyon hataları ve belirsiz bölümlerin uygun biçimde işaretlenmesi.
- Uzman düzeltme süresi ve toplam görev süresinde ölçülebilir iyileşme.
- Raporun görev şablonuna uygun, ekleriyle eşleşmiş ve eski görev verisinden arındırılmış olması.
- Son kontrol listesindeki insan kararı bekleyen maddelerin görünür olması.
- Güvenlik ve yedek/geri yükleme kabul testlerinin geçmesi.

Sayısal eşikler pilot öncesi belirlenmelidir. Transkripsiyon doğruluğu, hukukî yeterlilik veya delil özgünlüğü için kanıt olarak sunulmaz.

## Kaynaklar

- [2026 Temel ve Alt Uzmanlık Alanları](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [Mozilla Common Voice — Datasets (Turkish; CC0-1.0)](https://commonvoice.mozilla.org/bas/datasets)
- [Bilirkişiler İçin Kontrol Listesi — Resmî PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20için%20Kontrol%20Listesi.pdf)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
