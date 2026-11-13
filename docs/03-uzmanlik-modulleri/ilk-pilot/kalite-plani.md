# 56.12 İçin Örnek Kalite Planı

> **Durum:** Araştırma şablonu — seçilmiş modül/pilot değildir  
> **Güncelleme:** 13 Kasım 2026

Bu belge, 56.12 olası uzmanlık akışında hangi kalite sorularının sorulabileceğini gösterir. Tek kullanıcı testi, kalite eşiği veya ürün kabul kriteri belirlemek için yeterli değildir. Ayrıntılı veri kümesi, anotasyon, ASR/diarization ölçütleri, performans ve kabul kapıları için [56.12 Test Planı ve Başarı Ölçütleri](56-12-test-plani-ve-basari-olcutleri.md) belgesine bakınız.

## İnsan referans kümesi

Pilot yapılmasına karar verilirse sentetik veya lisansı/izin koşulları doğrulanmış açık Türkçe konuşma örneklerinden insan tarafından gözden geçirilmiş referans transkript hazırlanmalıdır. Gerçek mahkeme kayıtları, ayrı yetkilendirme ve veri işleme protokolü olmadan kullanılmaz ve GitHub'a konmaz.

## Hata sınıfları

- Kelime atlama/ekleme/değiştirme.
- Özel ad, sayı, tarih ve kısaltma hatası.
- Zaman damgası kayması.
- Konuşmacı sırası/etiket karışması.
- Örtüşen konuşma, fısıltı, gürültü ve düşük ses seviyesi.
- Anlaşılamayan bölümün tahminle doldurulması.
- Orijinal kayıttan kopuk veya yanlış dosyaya bağlanan metin.
- Rapor metni/ekler ile kaynak materyal arasında yanlış eşleşme.
- Eski görevden kalan ad, tarih, dosya bilgisi veya yer tutucu.

## Uzun kayıt ve çoklu materyal testi

İlk kullanıcı örneğinde sekiz kaydın toplamı yaklaşık 160 dakikaydı. Test paketi, tek kısa klip yanında çoklu dosya ve uzun süreli işlem senaryolarını da içermelidir. Kesinti, yeniden başlatma, kısmi çıktı, bozuk dosya ve bir dosyanın atlanması senaryoları test edilmelidir.

## Test katmanları

- Temiz, aksan/lehçe farklılığı içeren konuşma.
- Arka plan gürültüsü, düşük ses ve fısıltı.
- İki veya daha fazla konuşmacı; üst üste konuşma ve kısa konuşma geçişleri.
- Özel isim, sayı, tarih, saat ve kısaltmalar.
- Uzun kayıtlar ve çoklu dosya.
- Zaman damgası ve belirli cümleye tekrar atlama.
- Dosya hash'i, orijinalin değişmezliği ve çalışma kopyası.
- Dosya sayısı/ek envanteri, eksik materyal ve çift kayıt.
- Rapor şablonu seçimi, boş alan, eski görevden kalmış metin ve ek eşleşmesi.
- Çökme sonrası devam, yedek/geri yükleme ve güvenli dışa aktarma.

## Başarı ölçütleri

- İnsan düzeltme süresi ve düzeltme miktarı.
- Kelime hata oranı (WER) ve karakter hata oranı (CER).
- Özel isim/sayı/tarih gibi kritik hata sınıflarının oranı.
- Belirsiz bölümlerin doğru işaretlenmesi ve tahminle doldurulmaması.
- Zaman konumlarının doğruluğu.
- Konuşmacı ayrımı hata oranı ve belirsiz bölümlerin doğru işaretlenmesi.
- Materyal envanteri ve rapor eklerinde eksik/yanlış eşleşme oranı.
- Orijinal materyalin işlem boyunca değişmediğinin doğrulanması.
- Kullanıcı başına toplam görev süresi: dinleme, düzeltme, rapor ve teslim hazırlığı ayrı ölçülür.
- Son kalite kapısında atlanan kontrol sayısı.

WER/CER ve model güven puanı tek başına bilirkişilik doğruluğu veya hukuki yeterlilik kanıtı değildir. Otomatik konuşmacı ayırma da kişilerin kimliğini belirlemez. Eşikler gerçek kullanıcı, görev ve risk sınıfıyla belirlenmelidir; görüşme yapılmadan sayı koymak sahte kesinlik yaratır.

## Rapor kalite kapısı

1. Görev ve cevaplanacak sorular doğru kaydedilmiş mi?
2. Görevlendirme kapsamı/uzmanlık sınırı net mi?
3. Fiziki ve dijital materyallerin envanteri ve kaynağı belli mi?
4. Her materyal için incelendi/incelenmedi/eksik/bozuk/kapsam dışı durumu açık mı?
5. Çoklu dosyalarda her dosya ile transkript eşleşiyor mu?
6. Kullanılan yöntem, araç, model ve sürüm bilgisi yazılmış mı?
7. Makine çıktısı ile uzman tarafından düzeltilip kabul edilen içerik ayrılmış mı?
8. Belirsiz, örtüşen veya incelenemeyen bölümler açıkça belirtilmiş mi?
9. Önemli alıntılar kaynak dosya ve zaman aralığıyla eşleşiyor mu?
10. Görev sorularının tümü cevaplanmış mı?
11. Doğru merci/yargı türü rapor şablonu ve zorunlu alanlar kullanılmış mı?
12. Ekler, dosya adları ve referanslar doğru eşleşiyor mu?
13. Eski görevden kalan ad, dosya numarası, tarih veya yer tutucu var mı?
14. Fiziken teslim alınan dosya/eklerin iade durumu kullanıcı tarafından kapatılmış mı?
15. Nihai teknik değerlendirme ve rapor onayı bilirkişi tarafından verilmiş mi?

Bu liste raporun eksiksizliğini garanti etmez; yalnızca tanımlı kontrolleri görünür kılar. Atlanan veya insan kararı bekleyen madde varsa rapor “tamamlandı” yerine “uzman kontrolü bekliyor” durumunda kalmalıdır.

## Kaynaklar

- [Bilirkişiler İçin Kontrol Listesi — Resmî PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20için%20Kontrol%20Listesi.pdf)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE Best Practices for Digital Audio Authentication](https://www.swgde.org/documents/published-complete-listing/15-a-001-swgde-best-practices-for-digital-audio-authentication/)
- [NISTIR 8387](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
