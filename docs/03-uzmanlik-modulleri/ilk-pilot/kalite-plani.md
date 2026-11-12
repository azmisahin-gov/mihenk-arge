# 56.12 Kalite Planı

> **Durum:** KULLANICI DOĞRULAMASI BEKLİYOR  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## İnsan referans kümesi

Pilot öncesi sentetik veya açık izinli seslerden insan tarafından iki kez gözden geçirilmiş referans transkript hazırlanmalıdır. Gerçek mahkeme kayıtları yalnızca yetkili ve hukukî dayanaklı ayrı çalışma protokolü altında kullanılabilir; GitHub'a veya genel test sistemine konmaz.

## Hata sınıfları

- Kelime atlama/ekleme/değiştirme.
- Özel ad ve kişi/yer adı hatası.
- Sayı, tarih, para ve kısaltma hatası.
- Zaman damgası kayması.
- Konuşmacı etiketi karışması.
- Örtüşen konuşma.
- Gürültü, yankı, düşük ses ve telefon bandı etkisi.
- Anlaşılamayan bölümün yanlış tahmini.

## Test katmanları

1. Temiz Türkçe tek konuşmacı.
2. Farklı bölgesel aksan/lehçe.
3. Gürültülü ve düşük kaliteli kayıt.
4. Üst üste konuşma.
5. Özel isim/rakam yoğun konuşma.
6. Uzun kayıt ve kesinti/yeniden başlatma.
7. Dönüştürme sonrası zaman damgası doğruluğu.
8. Orijinal dosyanın byte-level değişmezliği.

## Başarı ölçütleri

WER/CER eşikleri uzmanlarla ve pilot amacına göre belirlenmelidir; bu aşamada sayı koymak sahte kesinlik yaratır. Ayrıca uzman düzeltme süresi, kritik hata oranı, `ANLAŞILAMADI` işaretlerinin kalitesi, zaman damgası tutarlılığı ve yanlış güven hissi ölçülmelidir.

## Kaynaklar

- [SWGDE Best Practices for Forensic Audio, v2.5 (09.06.2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [NISTIR 8387 — Digital Evidence Preservation: Considerations for Evidence Handlers (08.09.2022)](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
