# 56.12 – Minimum Benchmark ve Uygulama Sırası

> **Durum:** Minimum pilot için daraltılmış plan; henüz model çalıştırılmadı veya ürün kabul edilmedi  
> **Tarih:** 13 Kasım 2026  
> **Ana kapsam:** [56.12 Minimum Sürüm Kapsamı ve Kabul Kapıları](56-12-minimum-surum-kapsami.md)

## 1. Bu matrisin amacı

İlk sürüm için amaç, çok sayıda modeli ve donanım kombinasyonunu yarıştırmak değil; **bir yerel transkripsiyon akışının gerçek uzman işini azaltıp azaltmadığını** gösterecek kadar kanıt toplamaktır.

Bu nedenle ilk turda 48 senaryonun tamamı ve tüm motor/runtime araştırması zorunlu değildir. Minimum pilot için yalnızca [12 kabul kapısı](56-12-minimum-surum-kapsami.md#4-minimum-dogrulama--12-kabul-kapisi) uygulanır.

## 2. İlk model denemesi

| Sıra | Aday | İlk kullanım | Sınır |
|---|---|---|---|
| 1 | Whisper Large v3 Turbo veya hedef cihaza uygun desteklenen Whisper varyantı | Yerel ASR zincirini çalıştıran temel aday | Yerel runtime, model dosyası ve donanım uyumu doğrulanır; otomatik üretim seçimi değildir. |
| 2 | TurkMedSTT M1 | En fazla bir Türkçe uyarlama alternatifi | Model kartı, lisans/veri kökeni ve Transformers/PyTorch yerel çalışma gereksinimi doğrulanır. Uyumlu değilse alternatif zorlanmaz. |

Qwen3-ASR, ufakzeka-kulak, Vosk, Uran ve diğer adaylar araştırma kayıtlarında kalır; ilk pilotu bloke etmez. İlk iki adaydan biri lisans veya teknik koşulları karşılamazsa, yeni model ailesi eklemeden önce kapsam ve ihtiyaç yeniden değerlendirilir.

## 3. Asgari test verisi

- Bir küçük, sürümü sabitlenmiş ve lisansı doğrulanmış Türkçe okuma konuşması seti.
- Özel ad, sayı, tarih, saat ve olumsuzluk içeren sentetik/kontrollü örnekler.
- Mümkünse izinli doğal konuşma örneği; yoksa okunmuş konuşma sonucunun doğal konuşmaya genellenemeyeceği açıkça yazılır.
- Her örnek için modelden bağımsız insan referansı. Belirsiz ses tahminle doldurulmaz.
- Gerçek dava/soruşturma sesi yalnızca ayrıca yetkilendirilmiş, yerel ve korumalı pilotta kullanılabilir; public depoya, CI sistemine veya buluta konmaz.

Veri kaynağı, split ve lisans bilgisi mevcut [veri kümeleri kaydı](56-12-veri-kumesi-kayitlari.md) içinde tutulur. Yeni bir benchmark veri altyapısı kurmak gerekmez.

## 4. Ölçülecek minimum sonuçlar

1. WER/CER: aynı insan referansı ve aynı normalizasyon kuralı.
2. Kritik hata: özel ad, sayı, tarih/saat, olumsuzluk ve kısaltma.
3. Atlanan konuşma ve sessizlikte uydurulan metin.
4. Uzmanın ASR taslağını düzeltme süresi ve yaptığı düzeltme miktarı.
5. Toplam ses süresine göre işleme süresi (RTF) ve gözlenen tepe bellek.
6. Ağ kapalı çalışma, görev yalıtımı ve orijinal dosyanın değişmezliği.

İlk denemede ayrıntılı GPU profilleme, yüzdelik gecikme analizi, bootstrap sıralaması veya her nicemleme türünün testi yapılmaz. Hedef cihaz ve model belirlendikten sonra gerçek bir darboğaz görülürse eklenir. Sayısal WER/RTF kabul eşiği uzman ve pilot sonuçları olmadan uydurulmaz.

## 5. Uygulama sırası

| Aşama | İş | Çıkış ölçütü | Durum |
|---|---|---|---|
| M0 | Minimum kapsamı ve uzman iş akışını doğrula | Giriş/çıkış biçimleri, uzman kontrol noktaları ve görev sınırı net | Belge hazır; uzman onayı bekliyor |
| M1 | Tek yerel ASR motoruyla dikey dilim PoC | Ses al → yerel transkript → sesle karşılaştırarak düzelt → çıktı üret | Henüz çalıştırılmadı |
| M2 | Gerekirse tek alternatif modeli aynı referansta karşılaştır | Model tercihi için WER/CER, kritik hatalar ve düzeltme eforu | Bekliyor |
| M3 | 12 minimum kabul kapısını uygula | GEÇTİ/KALDI/ENGELLENDİ sonuçları ve açık riskler | Bekliyor |
| M4 | B-01 ile iş akışı pilotunu değerlendir | Gerçek zaman/efor kazanımı ve uzman kabul notu | Bekliyor |

Aşamalar tamamlanmadan model “üretime hazır” ilan edilmez. Teknik olarak çalışan bir PoC, uzman kabulü veya hukuki uygunluk anlamına gelmez.

## 6. Şimdilik yapılmayacak işler

- Özel Python CLI/benchmark harness geliştirmek.
- Tüm ASR model ailelerini ve runtime/nicemleme varyantlarını çalıştırmak.
- Otomatik diarization motoru karşılaştırması.
- Forced alignment, source separation veya ses iyileştirme deneyleri.
- LLM, embedding, vektör arama veya çok modlu model seçimi.
- Mobil performans, GPU ürün matrisi veya her işletim sistemi için ayrı optimizasyon.

Bunlar sonraki aşama araştırmalarıdır; minimum 56.12 pilotunun giriş koşulu değildir.

## 7. Model seçimini dondurmak için gereken karar

Model tercihi ancak hedef bilgisayarda yerel çalışma, lisans/veri kökeni, kritik hata profili ve uzman düzeltme eforu birlikte görüldükten sonra yapılır. Modelin geliştirici benchmark'ı veya tek bir genel WER puanı MİHENK kabulü değildir.

Bu matris, uygulama çatısı veya masaüstü teknoloji yığını seçmez. Önce 56.12 dikey diliminin gerçek ihtiyacı doğrulanır.
