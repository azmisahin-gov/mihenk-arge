# 56.12 İçin Örnek Kalite Planı

> **Durum:** Araştırma şablonu — seçilmiş modül/pilot değildir  
> **Güncelleme:** 13 Kasım 2026

Bu belge, 56.12 olası uzmanlık akışında hangi kalite sorularının sorulabileceğini gösterir. Tek kullanıcı testi, kalite eşiği veya ürün kabul kriteri belirlemek için yeterli değildir.

## İnsan referans kümesi

Pilot yapılmasına karar verilirse sentetik veya açıkça izinli seslerden insan tarafından gözden geçirilmiş referans transkript hazırlanmalıdır. Gerçek mahkeme kayıtları ancak ayrı yetkilendirme ve veri işleme protokolüyle kullanılabilir; GitHub'a konmaz.

## Hata sınıfları

- Kelime atlama/ekleme/değiştirme.
- Özel ad, sayı ve tarih hatası.
- Zaman damgası kayması.
- Konuşmacı etiketinin karışması.
- Örtüşen konuşma, gürültü ve düşük ses seviyesi.
- Anlaşılamayan bölümün yanlış tahmin edilmesi.
- Orijinal kayıttan kopuk veya yanlış dosyaya bağlanan metin.
- Rapor metni/ekler ile kaynak materyal arasında yanlış eşleşme.

## Test katmanları

Temiz konuşma, aksan/lehçe çeşitliliği, gürültü, örtüşen konuşma, özel isim/sayı, uzun kayıt, birden fazla dosya, kesinti sonrası toparlama, zaman damgası, dosya bütünlüğü, yedek/geri yükleme ve doğru rapor paketleme.

## Başarı ölçütleri

- İnsan düzeltme süresi ve düzeltme miktarı.
- Kelime hata oranı (WER) ve karakter hata oranı (CER).
- Kritik hata oranı: özel isim, sayı, tarih ve anlamı değiştiren kelimeler.
- Belirsiz bölümlerin doğru işaretlenme oranı.
- Zaman konumlarının doğruluğu.
- Materyal envanteri ve rapor eklerinde eksik/yanlış dosya oranı.
- Orijinal materyalin içe alma ve işlem boyunca değişmeden kaldığının kontrolü.
- Kullanıcının son kontrol listesinde atlanan madde sayısı.

WER/CER ve model güven puanı tek başına bilirkişilik doğruluğu veya hukuki yeterlilik kanıtı değildir. Eşikler gerçek kullanıcı, görev ve risk sınıfıyla belirlenmelidir; görüşme yapılmadan sayı koymak sahte kesinlik yaratır.

## Rapor kalite kapısı

1. Görev ve soru kapsamı doğru kaydedilmiş mi?
2. Kullanılan materyallerin listesi ve kaynağı belli mi?
3. Her kaynak dosya için inceleme durumu açık mı?
4. Kullanılan yöntem/araç ve ilgili sürüm bilgisi yazılmış mı?
5. Makine çıktısı ile uzman tarafından kabul edilen/düzeltilen içerik ayrılmış mı?
6. Belirsiz veya incelenemeyen bölümler açıkça belirtilmiş mi?
7. İstenen soruların her biri cevaplanmış mı?
8. Rapor şablonu ve zorunlu alanlar doğru mu?
9. Ekler, dosya isimleri ve referanslar doğru eşleşiyor mu?
10. Nihai teknik değerlendirme uzman tarafından gözden geçirilmiş ve onaylanmış mı?

Bu liste raporun eksiksizliğini garanti etmez; sadece tanımlı kontrolleri görünür kılar.

## Kaynaklar

- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [NISTIR 8387](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
