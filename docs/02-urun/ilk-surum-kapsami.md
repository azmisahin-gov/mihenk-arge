# İlk Sürüm Kapsamı

> **Durum:** Henüz belirlenmedi — bütünleşik platform hedefi eklendi  
> **Güncelleme:** 13 Kasım 2026

## Bu aşamadaki karar

**İlk kullanılabilir teslimatın odağı 56.12 — Ses Kayıtlarının Metne Dönüştürülmesi kontrollü uzman pilotudur.** Bu yön, proje sahibinin açık talimatıdır ve ADR-032 ile kayıt altına alınmıştır.

Bu karar, MİHENK'in uzun vadeli bütün platform MVP'sinin tamamlandığı veya bütün uzmanlıkların kapsamının seçildiği anlamına gelmez. İlk teslimat dar bir uzmanlık modülünde baştan sona gerçek kullanıcı işini tamamlamayı hedefler; sonraki modüller ortak çekirdek üzerinde aşamalı biçimde ele alınır.

56.12 kullanıcı arayüzü için [Wireframe v0.3](56-12-wireframe-v0.3.md) hazırlanmıştır. **v0.3 taslaktır, kullanıcı tarafından kabul edilmemiştir ve uygulama tasarımı için nihai referans değildir.** Yeni oturumda ilk açılıştan tek raporun önizlenmesine kadar yeniden gözden geçirilip netleştirilecektir.

[56.12 Minimum Sürüm Kapsamı ve Kabul Kapıları](../03-uzmanlik-modulleri/ilk-pilot/56-12-minimum-surum-kapsami.md) teknik/işlevsel ilk pilot kapsamını; [İlk Teslimat Ürün Sözleşmesi](56-12-ilk-teslimat-urun-sozlesmesi.md) ise kullanıcı hedefini tanımlar. Bu belgeler gerçek 56.12 uzmanı, hukuk ve veri koruma incelemesinin yerine geçmez.

## Uzun vadeli ürün hedefi

MİHENK, bilirkişinin görevini tek uygulama içinden başlatabildiği, yürüttüğü, inceleme/analiz araçlarını kullandığı, raporunu oluşturduğu ve teslim öncesi kontrollerini tamamladığı bütünleşik ve kapsamlı bir platform olmalıdır.

Kullanıcıdan uzmanlık aracını ayrıca indirip açması, farklı programlar arasında dosya taşıması, komut satırında işlem yapması veya haricî web hizmetine dosya yüklemesi beklenmez. Uzmanlık araçları MİHENK'in içine entegre edilmiş, sürümü ve lisansı yönetilen modüller olarak sunulur. Teknik motorlar gerektiğinde uygulama ile birlikte paketlenmiş arka plan süreçlerinde çalışabilir; kullanıcı deneyimi tek uygulama olarak kalır.

## Kapsamın büyüme modeli

- Ortak görev, materyal, güvenlik, belge ve rapor çekirdeği bütün modüllerin temelidir.
- Her uzmanlık alanının kendi araç seti, yöntemleri, veri alanı ve kalite testleri bulunur.
- Yeni modüller ortak çekirdeği değiştirmeden eklenebilir.
- Modüller gerçek kullanıcı iş akışı, resmî kapsam, açık kaynak/üçüncü taraf lisansları, veri güvenliği ve test sonuçları doğrulanarak yayımlanır.
- Tüm uzmanlık alanlarına ait bütün araçları ilk sürümde tamamlamak yerine, platform mimarisi baştan bu genişlemeyi desteklemelidir.

## Ürün hipotezi

Bilirkişi resmî görevlendirmesini UYAP'ta yürütür; MİHENK ise her görevin kendi tutanak ve materyallerinden hareketle çalışma alanını kurar, uzmanlık araçlarını çalıştırır, işi yönetir, raporunu oluşturur ve tanımlı kalite kontrollerini yapar.

İş akışı tek bir sabit form değildir. Ortak bir görev çekirdeği bulunur; her görev için kapsam, sorular, materyal listesi, süre, şablon, çıktı biçimi, nüsha ve iade koşulları görevlendirme belgesinden/merci talimatından alınır.

## Otomasyon ilkesi

Mümkün olan bütün tekrarlı, deterministik ve güvenli adımlar varsayılan olarak otomatik çalışır. Kullanıcıdan her aşama için tekrar tekrar onay istenmez. İnsan müdahalesi belirsizlik, çelişki, risk, meslekî kanaat, imza ve resmî teslim noktalarında kalır.

## MVP karar kapısı

- Ortak sorun farklı uzmanlık/deneyimlerde doğrulanmalı.
- Ortak çekirdek ile modüle özel araçlar ayrıştırılmalı.
- İlk modülün kullanıcı, uzmanlık ve test kapsamı seçilmeli.
- Belge ve UDF uyumluluğu test edilmelidir.
- Lisans, veri güvenliği, çevrimdışı çalışma ve güncelleme modeli doğrulanmalıdır.
- Proje sahibi ilk sürüm kapsamını onaylamalıdır.
