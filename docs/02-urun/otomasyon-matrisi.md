# Otomasyon Matrisi

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

| İş | Sınıf | Ürün yaklaşımı | Sınır |
|---|---|---|---|
| Görev kartı açma | Otomatikleştirilebilir | Kullanıcı girişi ve şablon | Resmî görevlendirme değildir |
| Süre/hatırlatma | Tam otomatik (kullanıcı onayı/ayarıyla) | Yerel takvim/uyarı | Resmî tebligat/süre tebliği yerine geçmez |
| Materyal üstverisi | Otomatik hazırla, onay gerekir | FFprobe/metadata okuma | Kaynağın doğruluğu insan tarafından kontrol edilir |
| Hash hesaplama | Tam otomatik | SHA-256 ve re-verify | Delil zinciri/hukuka uygunluk ispatı değildir |
| Çalışma kopyası oluşturma | Uzman onaylı otomatik | Parametreleri göster, logla | Orijinal korunur, dönüşüm gerekçesi belgelenir |
| ASR/transkripsiyon | Uzman kontrollü | Taslak üret; insan dinleyerek doğrular | Sonuç/kanaat üretmez; hata ölçümü gerekir |
| Konuşmacı etiketleme | İnsan yapar, yazılım destek olur | Anonim etiket ve elle düzenleme | Biyometrik kimlik belirleme yok |
| Rapor biçim kontrolü | Otomatik | Bölüm/ek/boş alan kontrolü | İçerik doğruluğu ve kanaat kontrolü bilirkişide |
| Hukukî değerlendirme | Otomatikleştirilmemeli | Özellik yok | 6754 m.3 ve ilgili usul sınırları |
| Tarafsızlık/çekinme kararı | Otomatikleştirilmemeli | Kontrol listesi, kullanıcı kararı | Çıkar çatışması bağlamı karmaşık |
| UYAP teslimi | Yetkisiz otomasyon kapsam dışı | Resmî portalda kullanıcı yapar | API/yazılı izin olmadan entegrasyon yok |
| Materyal iadesi | Uzman kontrollü | Checklist ve tarih kaydı | Fiziki teslim tutanağının yerine geçmez |
| Saklama/silme | Karar bekliyor | Kullanıcı ve hukukçu onaylı politika | Genel süre uydurulmaz |

Her yeni otomasyon için yanlış sonuç etkisi, geri alma, loglama ve kullanıcı onayı ayrı tasarlanmalıdır.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [UYAP Bilirkişi Portal](https://bilirkisi.uyap.gov.tr/)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [SWGDE Best Practices for Forensic Audio, v2.5 (09.06.2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
