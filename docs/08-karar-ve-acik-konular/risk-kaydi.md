# Risk Kaydı

> **Durum:** İLK SAHA GÖZLEMİYLE GÜNCELLENDİ — olasılık/etki değerleri ön değerlendirmedir  
> **Güncelleme:** 13 Kasım 2026

| ID | Risk | Olasılık / etki | Önlem | Durum |
|---|---|---|---|---|
| R-01 | Ürün ihtiyacı tek kullanıcı gözleminden genellenir | Yüksek / yüksek | Farklı uzmanlık ve deneyimden ek kullanıcılar | Açık |
| R-02 | UYAP işlevleri/yetkileri yanlış varsayılır | Orta / yüksek | Yetkili kullanıcı ve güncel resmî doküman doğrulaması | Açık |
| R-03 | UYAP entegrasyonuna izinsiz erişim | Orta / kritik | API/yazılı izin yoksa entegrasyon yok | Kapsam dışı |
| R-04 | Bilirkişi kapsamı dışına taşma | Orta / kritik | Uzmanlık kodu, görev sorusu ve açık kapsam sınırı | Açık |
| R-05 | Delil materyalinin değişmesi/kaybolması | Orta / kritik | Orijinal-kopya ayrımı, hash re-verify, backup/restore | Açık |
| R-06 | Gizli/özel nitelikli veri sızıntısı | Orta / kritik | Veri minimizasyonu, şifreleme, public repo yasağı | Açık |
| R-07 | ASR yanlış transkript ve aşırı güven | Yüksek / yüksek | İnsan doğrulaması, belirsiz bölüm ve referans corpus | Açık |
| R-08 | Üçüncü taraf lisans uygunsuzluğu | Orta / yüksek | SBOM ve hukukî lisans inceleme | Açık |
| R-09 | Güncelleme tedarik zinciri saldırısı | Orta / yüksek | İmzalı yayın, provenance, checksum/signature | Açık |
| R-10 | Çoklu cihaz/senkronizasyon veri çakışması | Orta / yüksek | İhtiyaç kanıtlanmadan senkronizasyon yok | Önlem önerildi |
| R-11 | Resmî şablon/rapor kuralının eski veya yanlış seçilmesi | Orta / yüksek | Merci bazında sürüm ve kaynak teyidi | Açık |
| R-12 | UI testi saha koşullarını temsil etmez | Yüksek / yüksek | Sentetik/açık veri + gerçek kullanıcı görev testi | Açık |
| R-13 | Fiziki dosya, ekler ve USB içeriğinin eksik envanterlenmesi | Orta / kritik | Teslim edilen/beklenen/aktarılan/incelenen/iade edilen materyali ayrı izleme | Yeni |
| R-14 | Uzun kayıt ve tekrar dinlemede yorgunluk/dikkat kaybı | Yüksek / yüksek | Senkronize metin-ses, tekrar döngüsü, işaret ve süre ölçümü | Yeni |
| R-15 | Konuşmacı sırası ile gerçek kişi kimliğinin karıştırılması | Orta / yüksek | Nötr etiket, kimlik iddiası yok, insan doğrulaması | Yeni |
| R-16 | Hash/metadata ile sesin özgünlüğü hakkında aşırı sonuç çıkarma | Orta / kritik | Hash sınırını açıkla; özgünlük incelemesini ayrı uzmanlık yap | Yeni |
| R-17 | Eski görev verisinin yeni rapora kopyalanması | Orta / yüksek | Temiz belge üretimi, alan doğrulaması ve çapraz-görev sızıntı testi | Yeni |
| R-18 | Görev kapsamına uymayan rapor şablonu kullanılması | Orta / yüksek | Merci/yargı türü seçimi ve kullanıcı onayı | Yeni |
| R-19 | Açık veri kümesinin gerçek adli konuşmayı temsil ettiği varsayımı | Yüksek / orta | Veri seti uygunluk sınırı ve ayrı sentetik test setleri | Yeni |

## Risk yönetimi kuralı

Kritik riskler kabul edilmeden gerçek vaka verisiyle dağıtım yapılmaz. Risk sahibi, hedef tarih ve kapatma kanıtı her satıra eklenmelidir. Olasılık/etki değerleri saha kanıtı geldikçe güncellenir.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [Bilirkişiler İçin Kontrol Listesi — Resmî PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20için%20Kontrol%20Listesi.pdf)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE Best Practices for Digital Audio Authentication](https://www.swgde.org/documents/published-complete-listing/15-a-001-swgde-best-practices-for-digital-audio-authentication/)
