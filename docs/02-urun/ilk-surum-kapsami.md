# İlk Sürüm Kapsamı

> **Durum:** Henüz belirlenmedi — görev bazlı yapılandırma ilkesi eklendi  
> **Güncelleme:** 13 Kasım 2026

## Bu aşamadaki karar

Henüz MVP veya ilk uzmanlık modülü seçilmedi. 56.12, tek kullanıcının ilk örnek görev senaryosudur. Bu davadaki sekiz ses dosyası yalnızca o örneğin materyal sayısıdır; MİHENK'in dosya sayısı veya görev akışı varsayılanı değildir.

## Ürün hipotezi

MİHENK'in araştırılacak temel fikri, bilirkişinin resmî görevlendirmesini UYAP'ta yürüttüğü; MİHENK'in ise her görevin kendi tutanak ve materyallerinden hareketle çalışma alanını kurduğu, işi yönettiği, inceleme hazırlığını desteklediği, raporunu oluşturduğu ve tanımlı kalite kontrollerini yaptığı bir görev ortamıdır.

İş akışı tek bir sabit form değildir. Ortak bir görev çekirdeği bulunur; her görev için kapsam, sorular, materyal listesi, süre, şablon, çıktı biçimi, nüsha ve iade koşulları görevlendirme belgesinden/merci talimatından alınır.

## Her görevde otomatik çıkarılacak koşullar

- Görevlendiren merci ve dosya referansı.
- İnceleme konusu, sınırlar ve cevaplanacak sorular.
- Uzmanlık uygunluğu ve başka uzman desteği ihtiyacı.
- Rapor süresi, başlangıç olayı ve ek süre.
- Teslim edilen/beklenen fiziki ve dijital materyal.
- Rapor şablonu, zorunlu içerik ve ekler.
- Teslim formatı, imza koşulu, istenen suret/nüsha sayısı.
- Fiziki materyalin iade koşulu.

Belge okuma veya OCR güveni düşükse, alanlar çelişiyorsa veya talimat eksikse yalnızca o nokta bilirkişi/proje kullanıcısı kontrolüne çıkarılır.

## Otomasyon ilkesi

Mümkün olan bütün tekrarlı ve deterministik adımlar varsayılan olarak otomatik çalışır. Kullanıcıdan her aşama için tekrar tekrar onay istenmez. İnsan müdahalesi şu durumlarla sınırlandırılır:
- Materyal eksik, bozuk, belirsiz veya şüpheli olduğunda.
- Görevlendirme kapsamı/uzmanlık/süre/şablon çelişkili veya belirsiz olduğunda.
- Otomasyon yeterli güvenle sonuca ulaşamadığında.
- Nihai teknik kanaat, raporun mesleki onayı, e-imza veya resmî UYAP gönderimi gerektiğinde.

Bu yaklaşım bilirkişinin kararını yazılıma devretmez; aradaki manuel iş yükünü azaltır.

## Ortak çekirdek için araştırılacak işlev kümeleri

- Görev kaydı ve görevlendirme belgesinden koşul çıkarımı.
- Süre ve aşama takibi.
- Fiziki/dijital materyal envanteri, teslim ve iade.
- Orijinal materyal/kopya ayrımı ve işlem geçmişi.
- Göreve göre otomatik oluşturulan kontrol listesi.
- Uzmanlık modülüne göre inceleme araçları.
- Kaynak materyal, bulgu ve rapor eki bağlantısı.
- Her görev için temiz rapor üretimi ve tamlık/biçim kontrolü.
- UYAP'a manuel gönderim için doğrulanmış çıktı paketi.

## 56.12'ye özgü araştırma

Birden fazla ses kaydı için dosya başına işlem durumu, zaman konumuna bağlı transkript, tekrar dinleme, belirsiz bölümler, nötr konuşmacı sıralaması ve önemli bölüm işaretleme. Bu özelliklerin bir başka uzmanlık alanına genellenmesi beklenmez.

## Kapsam dışında tutulanlar

- UYAP API/yazılı izin olmadan resmî portala otomatik giriş veya gönderim.
- Bilirkişi yerine nihai teknik kanaat, kanıt yorumu veya hukuki değerlendirme.
- Doğrulanmamış doğruluk/eksiksizlik garantisi.
- Önceki görev raporunu kopyalayıp alanları değiştirme.
- Önceki Forensic Transcriber depolarından kod, mimari veya bağımlılık kullanımı.
- Gerçek vaka/ses/evrakın public GitHub veya yetkisiz haricî servise aktarılması.

## MVP karar kapısı

- Ortak sorun farklı uzmanlık/deneyimlerde doğrulanmalı.
- Her görevde değişen alanlarla ortak çekirdek ayrıştırılmalı.
- Resmî şablon, süre, teslim biçimi ve nüsha talepleri güvenilir kaynakla eşleştirilmeli.
- İnsan kararı gereken aşamalar ve otomatik durdurma/istisna halleri tanımlanmalı.
- Hukuk ve güvenlik sınırları doğrulanmalı.
- Proje sahibi kapsamı onaylamalı.
