# 56.12 İçin Örnek İş Akışı Araştırması

> **Durum:** İlk görev anlatımıyla güncellendi — modül/MVP kararı değildir  
> **Güncelleme:** 13 Kasım 2026

## Bu belgenin amacı

56.12 ilk görev testinde kullanılan örnek uzmanlık alanıdır. Önceki transkripsiyon depoları MİHENK'in kod tabanı veya pilot uygulaması olarak kullanılmayacaktır. Bu belge, alanın olası iş akışını ve genel ürünün karşılaması gereken sınırları araştırır.

## 56.12 kapsam sınırı

Resmî 2026 listesi 56.12'yi “Ses Kayıtlarının Metin Haline Dönüştürülmesi” olarak tanımlar ve yargı mercilerince ses ve görüntü bilişim sisteminin kullanılmasına ilişkin istisna içerir. 56.11 ise adli ses ve görüntü inceleme/çözümlemeleridir. İki alan karıştırılmamalıdır.

## İlk kullanıcı anlatımından çıkarılan ayrıntılı iş akışı hipotezi

1. **Görevlendirme:** Bilirkişi görevi UYAP'ta görür ve portalda kabul eder.
2. **Fiziki teslim çağrısı:** İlgili mahkeme telefonla arayarak dosyanın alınması için bilgilendirebilir. Bu adım tek testte gözlenmiştir; tüm dosyalar için genel kural değildir.
3. **Dosya teslimi:** Fiziki dosya, ekleri ve USB gibi dijital medya imza karşılığı teslim alınabilir. Mevcut tutanak ve materyal listesi kaydedilmelidir.
4. **Ön inceleme:** Görevlendirme yazısı/talep ve cevaplanması istenen sorular belirlenir. Kapsam dışı konu, eksik bilgi veya materyal ihtiyacı varsa merciye bildirme ihtiyacı doğabilir.
5. **Materyal envanteri:** Fiziki dosyadaki belgeler, ekler, zarf/taşıyıcı ve dijital ortam ayrı listelenir. Her materyalin görev açısından durumu belirtilir. Her belgeyi tümüyle okumak zorunlu varsayılmaz; ancak teslim alınan ve incelemeye esas olan materyalin listesi ve kapsamı bilinmelidir.
6. **Dijital içe alma:** USB/medya içeriği listelenir; dosya sayısı, ad, tür, boyut, süre ve hash bilgisi alınır. Orijinal korunur ve yalnızca çalışma kopyası üzerinde işlem yapılır.
7. **Ön kontrol:** Eksik, bozuk, okunamayan, desteklenmeyen veya beklenmeyen dosyalar işaretlenir. Beklenen/alınan/aktarılmış materyal eşleşmesi kontrol edilir.
8. **Ses işleme ve transkripsiyon taslağı:** Kullanılan motor, model, sürüm, parametre ve dönüşüm adımları kaydedilerek makine taslağı oluşturulur.
9. **Uzman dinleme ve düzeltme:** Metin sesle eşzamanlı sunulur. Uzman bölüm döngüleme, zaman konumuna atlama ve belirsiz/fısıltılı/örtüşen konuşma işaretleriyle metni doğrular.
10. **Konuşmacı etiketleri:** Yalnızca ayırt edilebilen konuşmacı sıraları için nötr etiketler (ör. Konuşmacı 1/2) kullanılması değerlendirilebilir. Bu etiket kişi kimliği, yaş veya cinsiyet tespiti değildir. Belirsiz veya üst üste konuşmalar açıkça işaretlenir.
11. **Önemli bölüm seçimi:** Uzman, önemli gördüğü zaman aralıklarını rapor için işaretler. Her alıntı kaynak dosyaya ve zaman aralığına geri bağlanmalıdır.
12. **Rapor oluşturma:** Görev/merci türüne uygun resmî rapor şablonu seçilir. Görev soruları, yöntem, materyal listesi, inceleme bulguları, belirsizlikler ve ekler ilişkilendirilir.
13. **Otomatik tamlık kontrolü:** Sistem boş alan, cevaplanmamış görev sorusu, eksik dosya durumu, ek eşleşmesi, hatalı referans, kalan yer tutucu ve başka görevden kalmış veri kontrolü yapar.
14. **Uzman son kontrolü:** İçerik, teknik değerlendirme, alıntı bağlamı ve nihai kanaat bilirkişi tarafından onaylanır. Otomatik kontroller bu onayın yerini almaz.
15. **Dışa aktarma ve resmî teslim:** MİHENK rapor ve ek paketini hazırlar. Bilirkişi dosyayı UYAP'a kendisi yükler, imzalar ve teslimi portalda doğrular.
16. **Materyal iadesi ve kapanış:** Fiziken alınan dosya ve ekler envanterle karşılaştırılır, merciye iade adımı kullanıcı tarafından kaydedilir. Uygulama resmî iade işlemini yapmış gibi göstermez.

Bu sıra tek bir senaryo üzerinden oluşmuş araştırma hipotezidir. Gerçek görev türü, yargı birimi, teslim şekli ve güncel rapor şablonuyla bilirkişi tarafından doğrulanmalıdır.

## Ortak çekirdek ve alana özgü işlev

**Ortak çekirdek adayı:** görev kaydı, süre/aşama, fiziki ve dijital materyal envanteri, teslim/iade kaydı, orijinal-kopya ayrımı, kontrol listesi, işlem geçmişi, rapor şablonu ve teslim öncesi tamlık kontrolü.

**56.12'ye özgü aday:** ses oynatma, metin-ses senkronizasyonu, zaman damgası, transkripsiyon taslağı, bölüm tekrar dinleme, belirsiz alan işaretleme, nötr konuşmacı sıralama ve çoklu ses dosyası takibi.

## Rapor şablonu ve kontrol listesi

Bilirkişilik Daire Başkanlığının yayımladığı rapor şablonları merci/yargı türlerine göre ayrıdır. MİHENK'in göreve özgü şablon seçimini kullanıcıya doğrulatması ve şablon sürümünü kaydetmesi gerekir. Resmî bilirkişi kontrol listesindeki materyal envanteri, görev soruları, rapor biçimi ve fiziki iade başlıkları otomatik kontrol kapısına dönüştürülebilecek adaylardır.

## Kapsam dışında tutulması gereken ayrımlar

Konuşmacı kimliği, ses karşılaştırması, sesin özgünlüğü, montaj/sahtecilik değerlendirmesi veya görüntü incelemesi otomatik olarak 56.12 transkripsiyon özelliği sayılmamalıdır. Bu işler ayrı uzmanlık ve yöntem doğrulaması gerektirir. Hash/metadata kontrolleri tek başına kaydın sahte olmadığını veya geçmişte değiştirilmediğini kanıtlamaz.

## Otomasyon sınırı

- Dosya envanteri, hash, biçim/okunabilirlik, zorunlu alan ve ek eşleşmesi gibi belirlenmiş kontroller otomatik yapılabilir.
- Transkripsiyon makine yardımıyla taslak üretir; nihai metin olarak etiketlenmez.
- Belirsiz bölümler, yanlış güven vermeden uzmanın incelemesine sunulmalıdır.
- Konuşmacı sıralaması bir öneri olabilir; kimlik doğrulaması değildir.
- Ses özgünlüğü/manipülasyonu hakkında sonuç, bu modülün otomatik çıktısı olamaz.
- Nihai teknik kanaat, delil yorumu, rapor onayı ve resmî sunum otomatikleştirilmemelidir.

## Kaynaklar

- [2026 Temel ve Alt Uzmanlık Alanları](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [Bilirkişiler İçin Kontrol Listesi — Resmî PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20için%20Kontrol%20Listesi.pdf)
- [Bilirkişi Rapor Şablonları — Daire Başkanlığı](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisi-rapor-sablonlari14032022105509)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE Best Practices for Digital Audio Authentication](https://www.swgde.org/documents/published-complete-listing/15-a-001-swgde-best-practices-for-digital-audio-authentication/)
