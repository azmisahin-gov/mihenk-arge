# İlk Pilot Seçimi

> **Durum:** KARAR BEKLİYOR  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Karar prensibi

Mevcut kodun bulunması, uzmanlık alanını otomatik olarak ilk pilot yapmaz. Bu nedenle sahadan kullanıcı ihtiyacı alınmadan sayısal puan/ ağırlık uydurulmamıştır.

## Ön eleme matrisi

| Kriter | 56.12 ses metne dönüştürme | 56.20 veri inceleme / 56.21 mobil inceleme | Muhasebe/hesaplama | İnşaat/gayrimenkul |
|---|---|---|---|---|
| Resmî alan kodu açık | Evet, 2026 listesinde | Evet, 56.20/56.21 | Resmî listede; alan şartları ayrıca çıkarılmalı | Resmî listede; alt alanlar ayrıca çıkarılmalı |
| Mevcut teknik artefakt | İki çalışan depo beyanı | Bu araştırmada incelenmiş ürün yok | Bu araştırmada incelenmiş ürün yok | Bu araştırmada incelenmiş ürün yok |
| İş akışının yazılımda desteklenebilirliği | Yüksek olasılık; insan doğrulaması şart | Alanın sınırına göre değişir | Hesap tablosu/tekrar eden işlerde olası | Saha verisi, ölçüm ve uzman yöntemine bağlı |
| Test materyali | Sentetik Türkçe ses üretilebilir; gerçek corpus yok | İzinli/anonimleştirilmiş dataset gerekecek | Sentetik finansal vaka üretilebilir | Gerçekçi sentetik/anonim proje verisi zor olabilir |
| Hukuki/uzmanlık riskleri | 56.11 ile karıştırma riski yüksek | İnceleme yetki sınırı belirsizleşebilir | Hesap otomasyonu kanaatle karışabilir | Yerinde inceleme ve metodoloji kritik |
| Kullanıcı ihtiyacı kanıtı | Yok | Yok | Yok | Yok |

## Geçici öneri

**Pilot adayı: 56.12, ancak ürün-pazar seçimi olarak değil, kontrollü doğrulama konusu olarak.** Bunun gerekçesi 56.12'nin 2026 listesinde açık ve 56.11'den ayrı tanımlanması ve mevcut iki uygulamanın somut teknik akış sunmasıdır. Buna karşılık gerçek bilirkişi talebi, işlem yoğunluğu, rapor beklentisi, test veri seti ve kullanıcı memnuniyeti henüz doğrulanmadığı için 56.12'yi en iyi pazar olarak seçmek mümkün değildir.

## Go / No-Go ölçütleri

56.12 pilotunu sürdürmek için: (1) en az 5 aktif 56.12 uygulayıcısıyla görüşme; (2) uygulamanın gerçek görev akışına uyup uymadığını uzman kontrolü; (3) izinli/sentetik test corpus; (4) insan tarafından referans transkript; (5) kayıt kalitesi sınıfları; (6) uzman ve hukuki sınırların doğrulanması; (7) yedek/geri yükleme ve hata toparlama; (8) rapor teslimiyle karıştırılmayan iş akışı.

Bu koşullar sağlanmazsa daha geniş platform geliştirilmemeli; ürün daraltılmalı veya geliştirme ertelenmelidir.

## Kaynaklar

- [Temel ve Alt Uzmanlık Alanları ve Aranan Nitelikler — 22.01.2026 PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
