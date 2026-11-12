# Ürün Gereksinimleri

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Gereksinim kayıt formatı

Her gereksinim `REQ-*` kimliği, kaynak, tip, gerekçe, öncelik, doğrulama, bağımlılık ve güven seviyesi taşır. Bu listedeki maddeler öneridir; hukukî zorunluluk ifadesi olarak okunmamalıdır.

| ID | İhtiyaç | Kaynak türü | Öncelik | Kabul ölçütü | Durum |
|---|---|---|---|---|---|
| REQ-CORE-001 | Görev kapsamı ve soruları kullanıcı tarafından elle kaydedilebilmeli | Hukuki iş akışından ürün önerisi | P0 | Her soru için açık cevap/inceleme durumu | Taslak |
| REQ-CORE-002 | Resmî işlem ve uygulama içi hazırlık görsel olarak ayrılmalı | Ürün güvenlik ilkesi | P0 | UYAP teslimi otomatik başarı sayılmıyor | Taslak |
| REQ-CORE-003 | Orijinal materyal ile çalışma kopyası ayrı saklanmalı | Teknik iyi uygulama | P0 | Orijinal dosya değişmez, türev metadata tutar | Taslak |
| REQ-CORE-004 | Görev, materyal ve rapor eylemleri denetim kaydı oluşturmalı | Ürün önerisi | P1 | Olay, zaman, uygulama sürümü, önce/sonra kaydı | Taslak |
| REQ-CORE-005 | Süre ve kullanıcı tanımlı hatırlatıcılar olmalı | Kullanıcı hipotezi | P1 | Tarih ve saat dilimi doğru | Görüşme bekliyor |
| REQ-SEC-001 | Yerel veri erişim kontrolü ve şifreleme planı olmalı | Teknik/hukuki | P0 | Tehdit modeli ve sızma testleri | Taslak |
| REQ-SEC-002 | Gerçek vaka verisi test ve telemetry için kullanılmamalı | Gizlilik ilkesi | P0 | CI sentetik fixture dışında vaka verisi içermiyor | Taslak |
| REQ-REPORT-001 | Rapor taslağı resmi görev sorularını eşleyebilmeli | HMK/CMK + ürün önerisi | P1 | Soru başına yanıt kontrolü | Hukukçu bekliyor |
| REQ-REPORT-002 | Uzman kanaati otomatik oluşturulmamalı | 6754 m.3 ve ürün sınırı | P0 | AI kapalı; sadece boş şablon/biçim kontrolü | Taslak |
| REQ-AUDIO-001 | Otomatik transkript ve uzman düzeltmesi ayrı tutulmalı | Mevcut repo/teknik öneri | P1 | Otomatik metin silinemez; farklar görünür | Pilot bekliyor |
| REQ-OPS-001 | Yedekleme ve geri yükleme akışı test edilmeli | Güvenilirlik gereksinimi | P0 | Tam geri yükleme ve bütünlük doğrulama | Taslak |

## Öncelik anlamı

P0: Güvenlik, veri kaybı veya hukuki sınır nedeniyle olmadan pilot yapılmamalı. P1: İlk kontrollü sürümde önemli. P2: kullanıcı kanıtıyla sonraki faz. P3: ileri fikir. Öncelikler bu aşamada geçicidir.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [6100 sayılı Hukuk Muhakemeleri Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/103103)
- [5271 sayılı Ceza Muhakemesi Kanunu — resmî PDF](https://aile.gov.tr/uploads/chgm/uploads/pages/kanunlar/5271-sayili-ceza-muhakemesi-kanunu.pdf)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
