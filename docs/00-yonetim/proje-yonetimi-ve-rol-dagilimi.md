# Proje Yönetimi ve Rol Dağılımı

> **Durum:** Çalışma düzeni — kabul edildi  
> **Güncelleme:** 12 Kasım 2026

## Roller

### Proje sahibi
- Bilirkişilerle görüşür ve izin/onamı alır.
- Görüşme rehberine göre soruları sorar.
- Gerçek vaka verisi göndermeden anonimleştirilmiş bulguları aktarır.
- Öncelik, kapsam, bütçe, zaman ve iş kararlarını verir.
- Ürün ve yayın kararlarını onaylar.

### ChatGPT — ürün/teknik çalışma ortağı
- Güncel mevzuat ve teknik konuları kaynaklarıyla araştırır.
- Görüşme bulgularını problem, gereksinim, risk ve karar kayıtlarına dönüştürür.
- Dokümanları, backlog'u, yol haritasını ve GitHub kayıtlarını günceller.
- Ürün akışları, ekran taslakları, mimari alternatifler ve teknoloji karşılaştırmaları hazırlar.
- Uygulama kararı verildiğinde kod, test, CI ve teknik belgeler için çalışır.
- Yapılan GitHub değişikliklerini commit/PR bağlantısı ve doğrulama sonucu ile bildirir.
- Kanıtlanmamış varsayımları gerçek gibi sunmaz.

ChatGPT kendiliğinden bilirkişilere ulaşamaz, telefon/e-posta görüşmesi yapamaz veya sürekli arka planda çalışamaz. Çalışma, kullanıcı bilgi verdiğinde veya yeni görev açtığında yürütülür.

### Bilirkişi / hukukçu danışmanlar
- Gerçek görev ve uzmanlık iş akışını doğrular.
- Hukukî, meslekî ve teknik sınırları değerlendirir.
- Eksik veya yanıltıcı olabilecek özellikleri açıklar.
- Örnekleri mümkün olduğunca anonim ve kişisel veri içermeyen şekilde verir.

## Çalışma döngüsü

1. Proje sahibi bir uzmanla görüşür.
2. Kısa, anonim görüşme notunu ChatGPT'ye iletir.
3. Bulgular kullanıcı ifadesi / araştırmacı yorumu / açık soru olarak ayrıştırılır.
4. Gereksinim, risk, kaynak, karar ve yol haritası belgeleri güncellenir.
5. Gerekirse GitHub Issue/PR açılır veya güncellenir.
6. Bir sonraki görüşme için takip soruları hazırlanır.
7. Yeterli kanıt oluşunca ürün kapsamı ve mimari kararı verilir.

## GitHub depo politikası

### `azmisahin-gov/mihenk`

Araştırma, ürün, gereksinim, karar, risk, görüşme sentezi ve proje yönetimi dokümanlarını içerir.

### Gelecekteki uygulama deposu

Uygulama kararı çıkarsa sıfırdan yeni bir depo açılır. Geçici ad `mihenk-app` olabilir; ad, görünürlük ve lisans kararı o aşamada verilir. Bu depo yalnızca MİHENK'e ait yeni kaynak kodu, test, CI ve release süreçlerini taşır. Dokümantasyon deposundaki gereksinim ve kararları referans alır; eski transkripsiyon depolarından kod veya bağımlılık içermez.

## Karar yetkisi

| Karar | Hazırlayan | Onaylayan |
|---|---|---|
| Kullanıcı problemi ve hedef | ChatGPT + proje sahibi | Proje sahibi, bilirkişi geri bildirimiyle |
| Meslekî/uzmanlık sınırı | Uzman görüşü + mevzuat araştırması | İlgili bilirkişi/hukukçu |
| Ürün kapsamı ve öncelik | ChatGPT | Proje sahibi |
| Teknoloji/mimari | ChatGPT alternatifleri hazırlar | Proje sahibi |
| Gerçek vaka verisiyle pilot | Hukuk/güvenlik değerlendirmesi | Proje sahibi ve ilgili yetkili taraflar |
| Yayın ve dağıtım | ChatGPT hazırlık yapar | Proje sahibi |

## Bilgi güvenliği

GitHub'a veya görüşme notlarına gerçek dosya numarası, kişi adı, T.C. kimlik numarası, ses kaydı, mahkeme evrakı, UYAP ekran görüntüsü veya gizli/özel nitelikli veri konmaz.

## Durum etiketleri

- **DOĞRULANDI:** Kaynak veya saha kanıtı mevcut.
- **KULLANICI DOĞRULAMASI BEKLİYOR:** Bilirkişi görüşmesi gerekli.
- **HUKUKİ İNCELEME BEKLİYOR:** Hukukçu değerlendirmesi gerekli.
- **VARSAYIM:** Doğrulanmamış hipotez.
- **KARAR BEKLİYOR:** Proje sahibi seçimi gerekli.
- **UYGULAMADA:** Uygulama deposunda geliştirme sürüyor.
- **TAMAMLANDI:** Kabul ölçütü ve doğrulama kanıtı mevcut.

Her çalışma oturumunda tamamlananlar, yeni kanıtlar, kararlar, açık riskler ve proje sahibinden beklenen sonraki katkı kısaca raporlanır.
