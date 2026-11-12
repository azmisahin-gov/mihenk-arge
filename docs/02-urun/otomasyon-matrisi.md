# Otomasyon Matrisi

> **Durum:** İlk saha gözlemi + mevzuat araştırmasıyla güncellendi  
> **Güncelleme:** 13 Kasım 2026

| İş | Sınıf | Ürün yaklaşımı | Sınır |
|---|---|---|---|
| Görevlendirme belgesini içe alma | Varsayılan otomatik | PDF/UDF veya izinli belgeyi oku, alanları çıkar | Düşük güvenli/çelişkili alanı işaretle |
| Görev koşullarını yapılandırma | Otomatik çıkarım + istisna kontrolü | Konu, sınır, sorular, tarih, süre, teslim ve suret şartlarını görev profiline dönüştür | Belirsiz talimatı kendi kendine yorumlayıp hukukî karar üretmez |
| Uzmanlık uygunluğu | Sistem ön kontrolü, bilirkişi kararı | Uzmanlık alanı ve işbirliği ihtiyacını karşılaştır | Görevi kabul/ret veya çekinme kararını yazılım vermez |
| Görev/çalışma alanı açma | Otomatik | Her görevlendirme için yeni, izole görev alanı oluştur | UYAP'ta resmî görevlendirme değildir |
| Süre/hatırlatma | Otomatik | Tutanaktaki süre ve başlangıç olayından yerel takvim oluştur | Başlangıç olayı belirsizse doğrulama ister; resmî tebligat değildir |
| Fiziki teslim kaydı | Kullanıcı girdisi + otomatik kontrol | Teslim eden/alan, tarih, imza/tutanak, taşıyıcı ve iade bilgisi | Resmî tutanağın yerine geçmez |
| Fiziki/dijital materyal envanteri | Dosyalar için otomatik; fiziksel evrak için yardımcı kayıt | Klasör/dosya listesi, metadata, dosya adedi ve içerik bağlantısı | Fiziki evrakın içeriği kullanıcı/merci listesiyle eşleştirilir |
| Beklenen/alınan/incelenen/iade edilen materyal | Otomatik karşılaştırma | Dört ayrı envanter durumunu karşılaştır | Eksik materyalin önemini uzman belirler |
| Metadata ve okunabilirlik | Otomatik | Tür, boyut, süre, codec, kanal, örnekleme oranı ve dosya açılabilirliği | Metadata kaynağın geçmiş özgünlüğünü kanıtlamaz |
| Hash ve kopya doğrulama | Deterministik otomasyon | İçe alma hash'i, çalışma kopyası karşılaştırması ve yeniden doğrulama | İlk hash teslimden önceki değişikliği kanıtlamaz |
| Güvenli çalışma kopyası | Otomatik, riskte durdur | Orijinali koru; dönüşüm aracı/sürüm/parametre kaydet | Tehlikeli veya desteklenmeyen dosyada işlem durur |
| ASR/transkripsiyon | Varsayılan makine taslağı | Dosya başına kuyruk, zaman damgası ve belirsiz bölüm işareti | Nihai metin ve kanaat bilirkişide |
| Ses-metni inceleme | Arayüz otomasyonu | Zaman konumuna atlama, bölüm tekrar döngüsü, hız ve oynatma kontrolleri | Yeterli inceleme ölçütünü görev ve uzman belirler |
| Konuşmacı sıralaması | Yazılım önerisi + insan düzeltmesi | Nötr Konuşmacı 1/2 etiketleri | Gerçek kişi kimliği, yaş/cinsiyet veya ses karşılaştırması iddiası yok |
| Önemli bölüm işaretleme | Yazılım kolaylaştırır, uzman seçer | Kaynak dosya ve zaman aralığına bağlı işaret/alıntı | Önem ve bağlam kararını bilirkişi verir |
| Rapor şablonu seçimi | Otomatik öneri + istisna kontrolü | Merci/yargı türü ve görev kapsamına göre sürümlü şablon | Belirsiz/çelişkili durumda kullanıcıya sorar |
| Her dava için yeni rapor | Varsayılan otomatik | Sadece o görevin doğrulanmış alanları ve sonuçlarından yeni belge üret | Önceki dava raporundan kopyala-yapıştır yok |
| Rapor tamlık/biçim kontrolü | Otomatik | Boş alan, cevaplanmamış soru, ek, eski görev verisi, suret ve biçim kontrolü | İçerik doğruluğu ve teknik kanaat bilirkişide |
| Rapor biçimi/UDF uyumu | Araştırma + uyumluluk testi | UYAP Editörü ve görev türünün desteklediği biçimlere çıktı adaptörü | UDF/diğer format ve imza kombinasyonu doğrulanmadan varsayım yok |
| E-imza/m-imza | Kullanıcı kontrolünde | Resmî editör/imza aracına hazır dosya paketi | Anahtar/PIN MİHENK'e alınmaz; uzman imzalar |
| UYAP'a resmî gönderim | Yetkisiz otomasyon kapsam dışı | Yükleme için hazır paket ve adım kontrolü | API/yazılı izin olmadan portal otomasyonu yok |
| Hukuki değerlendirme/nihai teknik kanaat | Otomatikleştirilmemeli | Karar yerine kanıt, kaynak ve kontrol görünürlüğü | Bilirkişinin mesleki sorumluluğu |
| Fiziki iade | Kullanıcı kontrollü + otomatik liste | İade öncesi envanter karşılaştırması | Resmî teslim/tesellüm işlemi MİHENK dışında |

## Otomasyonun çalışma politikası

- Tekrarlı, deterministik ve güvenli işlemler varsayılan olarak otomatik çalışır; her adımda kullanıcı onayı istenmez.
- Eksik/bozuk materyal, çelişkili talimat, düşük belge okuma güveni veya belirsiz görev kapsamı varsa yalnızca sorunlu adım kullanıcıya çıkarılır.
- İşlem sonucu ve kaynağı kaydedilir; otomatik işlem gerektiğinde tekrar çalıştırılabilir veya güvenli şekilde geri alınabilir.
- Nihai teknik kanaat, raporun meslekî onayı, elektronik imza ve resmî UYAP teslimi kullanıcı kontrolünde kalır.
- Otomatik kontrolün geçtiği ifadesi yalnızca tanımlı kontrolün geçtiğini gösterir; “rapor kesinlikle doğru/eksiksizdir” garantisi değildir.

## Kaynaklar

- [Bilirkişilik Yönetmeliği — 16.06.2025 tarihli konsolide PDF](https://rayp.adalet.gov.tr/resimler/494/dosya/bilirkisilik-yonetmeligi16-06-20254-49-pm.pdf)
- [6100 sayılı HMK](https://mevzuat.adalet.gov.tr/mevzuat/103103)
- [5271 sayılı CMK](https://mevzuat.adalet.gov.tr/mevzuat/102946)
- [Bilirkişiler İçin Kontrol Listesi](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20için%20Kontrol%20Listesi.pdf)
- [UYAP Doküman Editörü — Resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
- [Mahkemeye Rapor Gönder — Bilirkişi Portal Kullanım Rehberi](https://rayp.adalet.gov.tr/resimler/489/dosya/portal-kullanimi21-09-202210-21-am.pdf)
