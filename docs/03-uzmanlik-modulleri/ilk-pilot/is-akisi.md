# 56.12 İçin Örnek İş Akışı Araştırması

> **Durum:** İlk görev anlatımı + görev bazlı koşul yaklaşımı eklendi  
> **Güncelleme:** 13 Kasım 2026

## Bu belgenin amacı ve sınırı

56.12, tek kullanıcının ilk örnek görev testinde kullanılan uzmanlık alanıdır. Bu belge bütün MİHENK görevlerini tanımlamaz. Önceki transkripsiyon depoları yalnızca geçmiş deneyim referansıdır; kod, mimari, veri modeli veya bağımlılık taşınmayacaktır.

İlk örnekte sekiz ses dosyası ve yaklaşık 160 dakika kayıt bulunuyordu. Bu sayı yalnızca örnek görevin materyal bilgisidir. MİHENK sekiz dosyayı varsayılan kabul etmeyecek; her görevin gerçek envanterini kullanacaktır.

## 56.12 kapsam sınırı

2026 resmî uzmanlık listesi 56.12'yi ses kayıtlarının metin hâline dönüştürülmesi olarak tanımlar ve yargı mercilerince ses/görüntü bilişim sistemi kullanılmasına ilişkin istisna içerir. 56.11 adli ses ve görüntü inceleme/çözümlemeleridir; iki alan karıştırılmamalıdır.

## Her göreve özgü koşullar önce belirlenir

Bilirkişilik Yönetmeliği m.51 uyarınca görevlendirme yazısı inceleme konusunu, kapsam/sınırları, cevaplanacak soruları ve rapor süresini bildirir. Bu nedenle 56.12'de bile tüm görevlerde aynı rapor soruları, dosya sayısı, süre veya ekler bulunacağı varsayılmaz.

MİHENK her dosyada görevlendirme belgesinden şunları çıkarır:
- Görevlendiren merci ve görev/dosya referansı.
- İnceleme konusu ve sınırları.
- Cevaplanacak sorular.
- Rapor teslim süresi ve başlangıç olayı.
- Teslim edilen materyal ve varsa dizi pusulası.
- Kullanılacak rapor şablonu, içerik/ek şartları.
- Elektronik/fiziki teslim, imza ve istenmişse nüsha koşulları.
- Fiziki materyal iadesi.

Bu koşulları her görev için ayrı bir profil olarak saklar. Sekiz ses dosyası, 30 gün veya taraf sayısından fazla suret gibi tek bir örneğe ait değerler başka davalara kopyalanmaz.

## İlk kullanıcı anlatımından çıkarılan örnek akış

1. **Görevlendirme:** Bilirkişi görevi UYAP'ta görür ve portalda kabul eder.
2. **Fiziki teslim çağrısı:** Mahkeme telefonla arayarak dosyanın alınması için bilgi verebilir; tek örnekte görülmüştür.
3. **Dosya teslimi:** Fiziki dosya, ekleri ve USB gibi dijital medya imza karşılığı teslim alınır; mevcut tutanak/dizi pusulası kaydedilir.
4. **Görev kapsamı:** Görevlendirme yazısındaki inceleme konusu, sınırlar ve sorular çıkarılır. Uzmanlık dışı, eksik veya çelişkili talimat sistem tarafından işaretlenir.
5. **Materyal envanteri:** Fiziki dosya, ekler, zarf/taşıyıcı ve dijital medya ayrı envanterlenir. Her belgenin okunması varsayılmaz; teslim edilen materyal ve inceleme kapsamı bilinmelidir.
6. **Dijital içe alma:** Medya içeriği listelenir; dosya sayısı, ad, tür, boyut, süre ve hash alınır; orijinal ile çalışma kopyası ayrılır.
7. **Ön kontrol:** Beklenen/alınan/aktarılmış/işlenmiş dosyalar karşılaştırılır; eksik/bozuk dosyalar işaretlenir.
8. **Transkripsiyon:** Kullanılan motor/model/sürüm/parametreler kaydedilerek makine taslağı üretilir.
9. **Uzman dinleme ve düzeltme:** Metin sesle eşzamanlı sunulur; zaman atlama, döngüde dinleme ve belirsiz/fısıltılı/örtüşen bölüm işaretleri kullanılır.
10. **Konuşmacı sıralama:** Ayırt edilebilen konuşma sıraları nötr etiketlenebilir; kimlik/yaş/cinsiyet tespiti olarak sunulmaz.
11. **Önemli bölüm seçimi:** Uzman önemli gördüğü aralıkları kaynak dosya ve zaman konumuyla işaretler.
12. **Rapor:** Her görev için yeni ve izole bir rapor oluşturulur; doğru merci şablonu, görev soruları, yöntem, bulgular, belirsizlikler ve ekler kullanılır.
13. **Otomatik kalite kapısı:** Boş alan, cevaplanmamış soru, eksik materyal, ek eşleşmesi, yanlış referans, yer tutucu ve önceki görevden veri sızıntısı kontrol edilir.
14. **Uzman onayı:** Teknik değerlendirme, bağlam, sonuç ve raporun meslekî onayı bilirkişiye aittir.
15. **Dışa aktarma ve imza:** Görev için doğrulanmış UYAP format akışı kullanılır. E-imza/m-imza resmî araçta bilirkişi tarafından uygulanır.
16. **Resmî teslim ve iade:** Rapor UYAP'a bilirkişi tarafından gönderilir; fiziki dosya/eklerin iadesi envanterle karşılaştırılıp kaydedilir.

## Otomasyon yaklaşımı

Rutin dosya sayımı, metadata, hash, transkripsiyon taslağı, kontrol listesi, rapor üretimi ve biçim denetimleri varsayılan otomasyondur. Sistem sadece düşük güven, eksik materyal, çelişkili talimat, uzmanlık sınırı veya insan kararı gerektiren aşamada müdahale ister. Nihai teknik kanaat, e-imza ve resmî gönderim otomatikleştirilmez.

## Kaynaklar

- [Bilirkişilik Yönetmeliği m.51–55](https://rayp.adalet.gov.tr/resimler/494/dosya/bilirkisilik-yonetmeligi16-06-20254-49-pm.pdf)
- [Bilirkişiler İçin Kontrol Listesi](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/14032022110908Bilirkişiler%20için%20Kontrol%20Listesi.pdf)
- [Bilirkişi Rapor Şablonları](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisi-rapor-sablonlari14032022105509)
- [UYAP Doküman Editörü — Resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
- [SWGDE Best Practices for Forensic Audio, v2.5](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
