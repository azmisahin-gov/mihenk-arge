# Mimari İlkeler ve Teknoloji Seçim Süreci

> **Durum:** Teknoloji seçimi yapılmadı  
> **Güncelleme:** 12 Kasım 2026

## Sıfırdan karar ilkesi

MİHENK'in dili, framework'ü, istemci tipi, veri tabanı, bulut/yerel yaklaşımı veya dağıtım modeli henüz seçilmemiştir. Önceki transkripsiyon örneklerindeki teknoloji ve mimariler MİHENK için başlangıç varsayımı olmayacaktır.

## Teknoloji seçmeden önce cevaplanacak sorular

- Kullanıcıların cihazları ve işletim sistemleri nelerdir?
- Bilirkişiler masaüstü mü, web mi, tablet/telefon mu kullanıyor?
- İnternet kesildiğinde hangi işlevler çalışmalı?
- Dosyalar cihazda mı kalmalı; kurum/kurul paylaşımı gerekli mi?
- Tek kullanıcı mı, ekip/kurul veya çok cihazlı çalışma mı gerekiyor?
- Hangi dosya türleri, boyutlar ve işlem süreleri bekleniyor?
- Güncelleme, kurulum ve teknik destek kim tarafından yürütülecek?
- Güvenlik, yedekleme ve saklama için hangi zorunluluklar var?

## Mimari ilkeler (hedef; henüz teknoloji kararı değil)

1. İş kuralları arayüzden bağımsız tanımlanmalı.
2. Uzmanlık modülleri ortak çekirdeği gereksiz alanlarla şişirmemeli.
3. Orijinal materyal, çalışma kopyası ve üretilen çıktı ayrı modellenmeli.
4. Otomatik hazırlanan içerik ile uzmanın doğruladığı içerik ayrılmalı.
5. Kullanıcı yetkisi ve onayı olmadan resmî sistemlerde işlem yapılmamalı.
6. Yedek/geri yükleme ve hata sonrası kurtarma ilk sürüm tasarımına dahil olmalı.
7. Gereksiz ağ çağrısı ve veri aktarımı olmamalı.
8. Güvenlik, erişilebilirlik, bakım maliyeti ve lisanslar teknoloji seçiminin parçası olmalı.

## Mimari karar kapısı

Kullanıcı görüşmeleri ve ürün kapsamı netleşmeden framework karşılaştırmasında kazanan ilan edilmeyecektir. Uygulama yapılacaksa en az iki alternatif; geliştirme maliyeti, güvenlik, performans, platform desteği, bakım, lisans, dağıtım ve test kolaylığı bakımından karşılaştırılacaktır.

## Depo ayrımı

Araştırma deposu `azmisahin-gov/mihenk` olarak kalacaktır. Uygulama kodu ayrı bir yeni depoda sıfırdan başlatılacaktır. Uygulama deposu açılmadan önce ad, görünürlük, lisans, CI, güvenlik ve release kararları kayda alınacaktır.
