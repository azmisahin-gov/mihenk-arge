# 56.12 İçin Örnek İş Akışı Araştırması

> **Durum:** İlk kullanıcı testiyle güncellendi — modül/MVP kararı değildir  
> **Güncelleme:** 13 Kasım 2026

## Bu belgenin amacı

56.12 ilk görev testinde kullanılan örnek uzmanlık alanıdır. Önceki transkripsiyon depoları MİHENK'in kod tabanı veya pilot uygulaması olarak kullanılmayacaktır. Bu belge, alanın olası iş akışını ve genel ürünün karşılaması gereken sınırları araştırır.

## 56.12 kapsam sınırı

Resmî 2026 listesi 56.12'yi “Ses Kayıtlarının Metin Haline Dönüştürülmesi” olarak tanımlar ve yargı mercilerince ses ve görüntü bilişim sisteminin kullanılmasına ilişkin istisna içerir. 56.11 ise adli ses ve görüntü inceleme/çözümlemeleridir. İki alan karıştırılmamalıdır.

## İlk kullanıcının testiyle ortaya çıkan akış hipotezi

1. **Görevlendirme:** Bilirkişi işi UYAP Bilirkişi Portalında görür; görev ve dosya erişimiyle ilgili resmî işlemleri portalda yürütür.
2. **Materyal edinimi:** Materyal portal üzerinden veya fiziki ortamda (ör. USB bellek) alınabilir. Edinim yöntemi ve teslim bilgisi kaydedilmelidir.
3. **Çalışma alanı:** Bilirkişi MİHENK'te yeni görev/dosya çalışma alanı açar ve gerekli görev bilgisini kendisi girer. Otomatik portal çekimi varsayılmaz.
4. **Güvenli içe alma:** Dosyalar envantere alınır; orijinal ile çalışma kopyası ayrılır; hash ve dosya özellikleri kaydedilir. Kaynak materyal değiştirilmez.
5. **Ön kontrol:** Dosya okunabilirliği, format, tekrar, eksik/bozuk materyal, süre/boyut ve desteklenen işlem koşulları kontrol edilir.
6. **İnceleme:** Gerekli araçlarla dinleme ve transkripsiyon taslağı hazırlanır; kullanılan araç/sürüm/parametre bilgisi izlenebilir olmalıdır.
7. **Uzman doğrulaması:** Uzman kaynak kaydı dinler, metni kontrol eder, belirsiz bölümleri düzeltir ve hangi çıktıyı kabul ettiğini işaretler.
8. **Rapor hazırlığı:** İlgili görev/mahkeme şablonu, görev soruları, yöntem, inceleme bulguları, ekler ve kaynak dosyalar ilişkilendirilir.
9. **Kalite kapısı:** Sistem tanımlı biçimsel/tamlık kontrollerini yapar; uzman içerik, teknik değerlendirme ve kanıt yorumunu son kez gözden geçirir.
10. **Dışa aktarma ve teslim:** MİHENK uygun rapor/ek paketini dışa aktarır. Bilirkişi resmî evrakı UYAP'a kendisi yükler, imzalar ve portalda teslimi doğrular.

Bu sıra tek bir senaryo üzerinden oluşmuş araştırma hipotezidir. Gerçek görev türü, yargı birimi, materyal teslim şekli ve güncel rapor şablonuyla doğrulanmalıdır.

## Ortak çekirdek ve alana özgü işlev

**Ortak çekirdek adayı:** görev kaydı, deadline/aşama, materyal envanteri, güvenli kopya, kontrol listesi, çalışma notu, sürüm/ek takibi, rapor hazırlığı ve teslim kontrolü.

**56.12'ye özgü aday:** ses dosyası oynatma, zaman konumuna bağlı transkript, düzeltme, belirsiz bölüm işaretleme ve çoklu ses dosyasının takibi.

## Kapsam dışında tutulması gereken ayrımlar

Konuşmacı kimliği çıkarımı, ses karşılaştırması, sesin özgünlüğü, montaj/sahtecilik değerlendirmesi veya görüntü incelemesi otomatik olarak 56.12 transkripsiyon özelliği sayılmamalıdır. Bu işler ayrı uzmanlık ve yöntem doğrulaması gerektirir.

## Otomasyon sınırı

- Dosya listesi, hash, biçim/okunabilirlik, zorunlu alan ve ek kontrolü gibi belirlenmiş kontroller otomatik yapılabilir.
- Transkripsiyon makine yardımıyla taslak üretir; nihai metin olarak etiketlenmez.
- Güven skoru tek başına kelime doğruluğu veya bilirkişi kanaati değildir.
- Belirsiz bölümler gizlenmemeli; uzmanın incelemesi için öne çıkarılmalıdır.
- Nihai teknik kanaat, delil yorumu, rapor onayı ve resmî sunum otomatikleştirilmemelidir.

## Kaynaklar

- [2026 Temel ve Alt Uzmanlık Alanları](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [NISTIR 8387 — Digital Evidence Preservation](https://www.nist.gov/publications/digital-evidence-preservation-considerations-evidence-handlers)
