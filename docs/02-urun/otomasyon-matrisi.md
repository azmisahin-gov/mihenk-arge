# Otomasyon Matrisi

> **Durum:** İLK SAHA GÖZLEMİYLE GÜNCELLENDİ — gereksinimler ve hukukî sınırlar ayrıca doğrulanacak  
> **Güncelleme:** 13 Kasım 2026

| İş | Sınıf | Ürün yaklaşımı | Sınır |
|---|---|---|---|
| Görev/çalışma alanı açma | Kullanıcı girdisiyle otomatik | Temel görev bilgisi ve görev soruları için yapılandırılmış kayıt | Resmî görevlendirme veya UYAP kabulü değildir |
| Görev kapsamı ve yeterlilik kontrolü | Sistem hatırlatır, uzman karar verir | Uzmanlık alanı, işbirliği ihtiyacı, süre ve eksik bilgi soruları | Görevi kabul/ret veya hukuki kanaati yazılım vermez |
| Fiziki teslim kaydı | Kullanıcı kontrollü | Teslim eden/alan, tarih, mevcut tutanak ve iade durumu | Resmî tutanağın yerine geçmez |
| Fiziki/dijital materyal envanteri | Kısmen otomatik | Klasör/dosya listesi, dosya sayısı ve metadata çıkarımı; fiziksel evrak kullanıcı tarafından kaydedilir | İçeriğin görev açısından yeterli olup olmadığını uzman belirler |
| Eksik/işlenmemiş materyal kontrolü | Kural tabanlı otomatik | Beklenen/alınan/aktarılmış/incelenmiş materyal durumlarını karşılaştır | Eksik materyalin hukuki önemini uzman değerlendirir |
| Dosya üstverisi | Otomatik hazırla, onay gerekir | Tür, boyut, süre, codec, kanal, örnekleme oranı ve okunabilirlik | Metadata kaynağın doğruluğunu veya özgünlüğünü kanıtlamaz |
| Hash ve kopya doğrulama | Deterministik otomasyon | İçe alım hash'i, çalışma kopyası hash karşılaştırması ve yeniden doğrulama | İlk hash teslim öncesi değişikliği göstermez; resmî delil zinciri değildir |
| Güvenli çalışma kopyası | Uzman onaylı otomatik | Orijinali koru; dönüştürme aracını/sürümünü/parametresini kaydet | Orijinal üzerinde çalışma yapılmamalı |
| Virüs ve dosya güvenliği | Kontrollü otomasyon | Güvenli/izole tarama ve medya ayrıştırma; riskte işlemi durdur | Tarama tüm kötü amaçlı davranışları yakalamayı garanti etmez |
| ASR/transkripsiyon | Uzman kontrollü | Makine taslağı, zaman damgası ve belirsiz alan işaretleri | Makine çıktısı nihai transkript değildir |
| Konuşmacı sıralama | Yazılım önerir, uzman düzeltir | Nötr Konuşmacı 1/2 etiketleri ve örtüşme/belirsizlik işareti | Gerçek kimlik, yaş/cinsiyet veya ses karşılaştırması çıkarımı yok |
| Dinleme/düzeltme | İnsan + arayüz desteği | Metinle eşzamanlı oynatma, zaman konumuna atlama, tekrar döngüsü, hız kontrolü | Tüm kaydın yeterli incelenmesi gerektiği görev ölçütünü uzman belirler |
| Önemli bölüm işaretleme | Yazılım kolaylaştırır, uzman seçer | Kaynak dosya ve zaman aralığına bağlı işaret/alıntı | Önem, bağlam ve rapora alınma kararını uzman verir |
| Rapor şablonu seçimi | Öneri + kullanıcı doğrulaması | Merci/yargı türüne göre resmî şablon kataloğu ve sürüm kontrolü | Yanlış şablon seçiminin sorumluluğu otomasyona bırakılamaz |
| Rapor tamlık/biçim kontrolü | Kural tabanlı otomatik | Boş alan, soru-cevap eşleşmesi, ek listesi, dosya referansı ve eski görev verisi kontrolü | İçerik doğruluğu, gerekçe ve kanaat uzman onayındadır |
| Hukuki değerlendirme ve nihai teknik kanaat | Otomatikleştirilmemeli | Bu alanlarda karar üretme özelliği yok | Bilirkişinin mesleki sorumluluğu |
| Sesin özgünlüğü/manipülasyon incelemesi | Ayrı uzmanlık/görev | Ayrı kapsam ve yöntem ihtiyacını işaretle | Transkripsiyon modülü otomatik “orijinal/sahte” diyemez |
| UYAP teslimi | Yetkisiz otomasyon kapsam dışı | Resmî portalda kullanıcı adımları için son kontrol | API/yazılı izin olmadan entegrasyon yok |
| Materyal iadesi | Uzman kontrollü | İade öncesi envanter ve kontrol listesi | Fiziki teslim tutanağının yerine geçmez |
| Saklama/silme | Karar bekliyor | Kullanıcı ve hukukçu onaylı politika | Genel süre uydurulmaz |

Her yeni otomasyon için hata etkisi, geri alma, iz kaydı, kullanıcı onayı ve başarı ölçütü ayrı tasarlanmalıdır. Otomatik kontrol sonucu yalnızca tanımlanmış kontrolün geçtiğini ifade eder; “inceleme eksiksizdir” veya “rapor doğrudur” garantisi değildir.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [Bilirkişiler İçin Kontrol Listesi — Resmî PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20için%20Kontrol%20Listesi.pdf)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE Best Practices for Digital Audio Authentication](https://www.swgde.org/documents/published-complete-listing/15-a-001-swgde-best-practices-for-digital-audio-authentication/)
