# Mimari İlkeler ve Teknoloji Seçim Süreci

> **Durum:** Teknoloji seçimi yapılmadı  
> **Güncelleme:** 13 Kasım 2026

## Sıfırdan karar ilkesi

MİHENK'in dili, framework'ü, istemci tipi, veri tabanı, bulut/yerel yaklaşımı, GPU kullanımı veya dağıtım modeli henüz seçilmemiştir. Önceki transkripsiyon örneklerindeki teknoloji ve mimariler MİHENK için başlangıç varsayımı olmayacaktır.

## Ürün akışı için mimari hipotez

- UYAP resmî sistem olarak kalır; görev kabulü ve resmî teslim kullanıcının kontrolünde yürür.
- MİHENK ayrı bir çalışma alanı açar; UYAP bilgisi kullanıcı tarafından girilir veya yetkilendirilmiş entegrasyon varsa açıkça izinli kaynaktan alınır.
- Portal/USB gibi kanallardan gelen materyal yerel çalışma alanına güvenli biçimde alınır.
- Orijinal materyal değişmeden korunur; hash, kaynak/teslim bilgisi, kopya ve türetilmiş çıktı bağlantıları saklanır.
- İş akışı ortak görev çekirdeği ile uzmanlık modüllerini ayırır.
- Makine tarafından üretilen taslaklar ile uzmanın gözden geçirip kabul ettiği içerik ayrı tutulur.
- Teslim öncesi otomasyon, yalnızca açıkça tanımlanmış kontrolleri yürütür; mutlak doğruluk/eksiksizlik garantisi vermez.

## Teknoloji seçmeden önce cevaplanacak sorular

- Kullanıcıların cihazları ve işletim sistemleri nelerdir?
- İlk açılış/kurulum ne kadar kolay olmalı; yönetici izni gerekiyor mu?
- Bilirkişiler masaüstü mü, tarayıcı mı, tablet/telefon mu kullanıyor?
- İnternet kesildiğinde hangi işlevler çalışmalı?
- Hassas materyal cihazdan dışarı çıkabilir mi; bulut/AI servisine aktarım için hangi izin ve hukuki dayanak gerekir?
- Tek kullanıcı mı, ekip/kurul veya çok cihazlı çalışma mı gerekiyor?
- Hangi dosya türleri, boyutlar, adetler ve işlem süreleri bekleniyor?
- GPU gerçekten gerekli mi, yoksa donanım bağımsız varsayılan çalışma mı daha önemli?
- Güncelleme, kurulum, imzalama ve teknik destek kim tarafından yürütülecek?
- Güvenlik, saklama, yedekleme ve geri yükleme için hangi gereksinimler var?

## Mimari ilkeler (hedef; henüz teknoloji kararı değil)

1. İş kuralları arayüzden ve teknik araçlardan bağımsız tanımlanmalı.
2. Uzmanlık modülleri ortak çekirdeği gereksiz alanlarla şişirmemeli.
3. Orijinal materyal, çalışma kopyası ve üretilen çıktı ayrı modellenmeli.
4. Otomatik hazırlanan içerik ile uzmanın doğruladığı içerik ayrılmalı.
5. Kullanıcı yetkisi ve onayı olmadan resmî sistemlerde işlem yapılmamalı.
6. Kurulum, ilk açılış ve güncelleme güvenliği ürün deneyiminin parçası olmalı.
7. Yedek/geri yükleme ve hata sonrası kurtarma ilk sürüm tasarımına dahil olmalı.
8. Gereksiz ağ çağrısı ve veri aktarımı olmamalı; varsayılan telemetri vaka içeriği taşımamalı.
9. Erişilebilirlik, bakım maliyeti, lisanslar ve tedarik zinciri güvenliği teknoloji seçiminin parçası olmalı.

## Mimari karar kapısı

Kullanıcı görüşmeleri ve ürün kapsamı netleşmeden framework karşılaştırmasında kazanan ilan edilmeyecektir. Uygulama yapılacaksa en az iki alternatif; geliştirme maliyeti, güvenlik, performans, platform desteği, bakım, lisans, dağıtım ve test kolaylığı bakımından karşılaştırılacaktır.

## Depo ayrımı

- Araştırma deposu: [azmisahin-gov/mihenk-arge](https://github.com/azmisahin-gov/mihenk-arge)
- Uygulama deposu: [azmisahin-gov/mihenk](https://github.com/azmisahin-gov/mihenk) — ayrılmış, public ve henüz boş.

Uygulama deposu yalnızca sıfırdan geliştirilecek ürün kodunu taşır. Public/private görünürlük ve lisans kararı kaynak kod eklenmeden önce tamamlanmalıdır.
