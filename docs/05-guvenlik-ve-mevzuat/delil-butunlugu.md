# Delil Bütünlüğü

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Kavram ayrımı

- Hash/kriptografik özet, dosyanın belirli bayt dizisini tanımlamaya ve zaman içinde değişip değişmediğini karşılaştırmaya yarar.
- Dijital imza, imza sahibini ve imzalanan verinin bütünlüğünü doğrulamaya yardımcı olur; her türlü teslim zincirinin yerine geçmez.
- Denetim kaydı, uygulama içindeki olayları kaydeder; mahkeme/kurum tutanağı veya resmî teslim kaydı değildir.
- Şifreleme, saklanan/taşınan verinin gizliliğini korumaya yöneliktir; erişim yönetimi ve anahtar yönetimi olmadan yeterli değildir.

## İş akışı önerisi

1. Kaynak ve teslim yöntemini kaydet.
2. Orijinal materyalin geldiği biçimi ve teknik özelliklerini koru.
3. İçe alma sırasında hash al ve kopya hash'ini karşılaştır.
4. Orijinal dosyaya yazma koruması uygula.
5. Çalışma kopyası üretildiğinde parametreleri ve araç sürümünü kaydet.
6. Türetilmiş her çıktı için kaynak dosya ve işlem ilişkisini sakla.
7. Belirli aralıklarla hash yeniden doğrulaması yap.
8. Hata/uyuşmazlıkta çalışmayı durdur, kullanıcıya görünür uyarı ver ve not kaydet.

## Sınır

Bu teknik tasarım, materyalin hukuka uygun elde edildiğini veya mahkemece delil olarak kabulünü garanti etmez. Uygulama “delil zinciri sağlandı” iddiası kullanmamalıdır.

## Kaynaklar

- [SWGDE Best Practices for Forensic Audio, v2.5 (09.06.2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [SWGDE Best Practices for Digital Evidence Collection, 18-F-002-2.0 (30.06.2025; sayfa taslak statüsüne işaret ediyor)](https://www.swgde.org/documents/published-complete-listing/18-f-002-best-practices-for-digital-evidence-collection/)
- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [ISO/IEC 27037:2012 — Guidelines for identification, collection, acquisition and preservation of digital evidence](https://www.iso.org/standard/44381.html)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
