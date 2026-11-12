# Proje Yönetimi ve Rol Dağılımı

> **Durum:** Çalışma düzeni — kabul edildi  
> **Güncelleme:** 13 Kasım 2026

## Roller

### Proje sahibi
- Bilirkişilerle görüşür ve gerekli izin/onamı alır.
- Son gerçek görev akışını ve test gözlemlerini aktarır.
- Gerçek vaka verisi göndermeden genelleştirilmiş bulguları paylaşır.
- Öncelik, kapsam, bütçe, zaman, depo görünürlüğü, lisans ve yayın kararlarını verir.
- Ürün ve yayın kararlarını onaylar.

### ChatGPT — ürün/teknik çalışma ortağı
- Güncel mevzuat ve teknik konuları kaynaklarıyla araştırır.
- Görüşme bulgularını kullanıcı ifadesi / araştırmacı yorumu / açık soru olarak ayırır.
- Gereksinim, risk, karar, backlog ve yol haritasını günceller.
- Ürün akışları, ekran taslakları, mimari alternatifler ve teknoloji karşılaştırmaları hazırlar.
- Uygulama geliştirme kararı verildiğinde kod, test, CI ve teknik belgeler için çalışır.
- GitHub değişikliklerini commit/PR bağlantısı ve doğrulama sonucu ile bildirir.
- Kanıtlanmamış varsayımları gerçek gibi sunmaz.

ChatGPT kendiliğinden bilirkişilere ulaşamaz, görüşme yapamaz veya sürekli arka planda çalışamaz. Çalışma, kullanıcı bilgi verdiğinde veya yeni görev açtığında oturum içinde yürütülür.

### Bilirkişi / hukukçu / güvenlik danışmanları
- Gerçek görev ve uzmanlık iş akışını doğrular.
- Mesleki, hukuki, veri koruma ve teknik sınırları değerlendirir.
- Hatalı veya eksik otomasyon varsayımlarını işaretler.

## Çalışma döngüsü

1. Proje sahibi bir uzmanla görüşür veya kontrollü bir görev testi yaptırır.
2. Gerçek vaka materyalini paylaşmadan özet bulguyu aktarır.
3. Bulgular kullanıcı anlatımı / ekran gözlemi / araştırmacı yorumu / resmî kaynak / açık soru olarak ayrıştırılır.
4. Gereksinim, risk, kaynak, karar ve yol haritası belgeleri güncellenir.
5. Gerekirse GitHub Issue/PR açılır veya güncellenir.
6. Sonraki görüşme için davranış temelli takip soruları hazırlanır.
7. Yeterli ve farklı kaynaklardan kanıt oluşunca ürün kapsamı ve mimari kararı verilir.

## GitHub depo politikası

### `azmisahin-gov/mihenk-arge` — araştırma deposu
Araştırma, mevzuat, anonimleştirilmiş saha sentezi, gereksinim, karar, risk ve proje yönetimi belgelerini içerir.

### `azmisahin-gov/mihenk` — uygulama deposu
Proje sahibi tarafından ayrılmıştır; 13 Kasım 2026 itibarıyla public ve boştur. Uygulama kararı ve güvenlik kapıları geçilince yalnızca MİHENK için sıfırdan yazılmış kod, test, CI ve release süreçleri burada yer alacaktır. Eski transkripsiyon depolarından kod veya bağımlılık taşınmayacaktır. Kaynak kod eklenmeden önce public/private görünürlük ve lisans bilinçli biçimde kararlaştırılmalıdır.

### Public depo kuralı
Her iki depo public olduğundan gerçek vaka verisi, ses/görüntü, rapor, dosya numarası, kişi/kurum bilgisi, UYAP ekran görüntüsü, sertifika, token, parola, üretim logu ve gizli evrak commit edilmez. Katılımcı kodu tek başına anonimlik sağlamaz; yeniden kimliklendirme riski azaltılmış toplu/tematik bulgular kullanılır. Gerçek görüşme notları ve ham ekran görüntüleri public repoda tutulmaz.

## Karar yetkisi

| Karar | Hazırlayan | Onaylayan |
|---|---|---|
| Kullanıcı problemi ve hedef | ChatGPT + proje sahibi | Proje sahibi, bilirkişi geri bildirimiyle |
| Mesleki/uzmanlık sınırı | Uzman görüşü + mevzuat araştırması | İlgili bilirkişi/hukukçu |
| Ürün kapsamı ve öncelik | ChatGPT | Proje sahibi |
| Teknoloji/mimari | ChatGPT alternatifleri hazırlar | Proje sahibi |
| Gerçek vaka verisiyle pilot | Hukuk/güvenlik değerlendirmesi | Proje sahibi ve ilgili yetkili taraflar |
| Depo görünürlüğü ve lisans | ChatGPT riskleri açıklar | Proje sahibi |
| Yayın ve dağıtım | ChatGPT hazırlık yapar | Proje sahibi |

## Durum etiketleri

- **DOĞRULANDI:** Güvenilir kaynak veya tekrarlanabilir saha kanıtı mevcut.
- **İLK GÖZLEM:** Tek kullanıcı/test veya sınırlı ekran incelemesi.
- **KULLANICI DOĞRULAMASI BEKLİYOR:** Başka bilirkişi görüşmesi gerekli.
- **HUKUKİ İNCELEME BEKLİYOR:** Yetkin hukukçu değerlendirmesi gerekli.
- **VARSAYIM:** Doğrulanmamış hipotez.
- **KARAR BEKLİYOR:** Proje sahibi seçimi gerekli.
- **UYGULAMADA:** Uygulama deposunda geliştirme sürüyor.
- **TAMAMLANDI:** Kabul ölçütü ve doğrulama kanıtı mevcut.
