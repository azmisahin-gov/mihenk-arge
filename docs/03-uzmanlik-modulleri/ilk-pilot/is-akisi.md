# 56.12 Pilot İş Akışı

> **Durum:** KULLANICI DOĞRULAMASI BEKLİYOR  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## 56.12 kapsam sınırı

Resmî 2026 listesi 56.12'yi “Ses Kayıtlarının Metin Haline Dönüştürülmesi” olarak tanımlar ve yargı mercilerince ses ve görüntü bilişim sisteminin kullanılmasına ilişkin bir istisna içerir. 56.11 ise adli ses ve görüntü inceleme/çözümlemeleridir. Bu nedenle 56.12 pilotu transkripsiyon ve insan doğrulamasıyla sınırlı tutulmalıdır.

## Önerilen çalışma akışı

1. Görev yazısı ve soru kapsamı kaydedilir.
2. Kaynak dosyanın kimden/ne şekilde alındığı yazılır.
3. Orijinal dosya salt okunur saklanır; dosya adı, boyut, format, hash, süre, örnekleme, kanal ve codec gibi teknik metadata kaydedilir.
4. Gerekliyse bir çalışma kopyası türetilir; dönüşüm parametreleri ve yazılım sürümü kaydedilir.
5. ASR motoru/model/sürüm/ayarları kaydedilir.
6. Otomatik transkript oluşturulur ve her segment AUTOMATIC olarak işaretlenir.
7. Uzman, her segmenti kayda karşı dinleyerek gözden geçirir; doğrulanamayan bölümler açıkça işaretlenir.
8. İnsan düzeltmeleri ve otomatik metin ayrı kalır; düzeltme geçmişi tutulur.
9. Son transkriptin biçimi, zaman damgası ve ekleri kontrol edilir.
10. Raporun nihai gerekçesi/kanaati uzman tarafından oluşturulur ve resmî usulle sunulur.

## Ayrı tutulması gereken işler

Konuşmacı biyometrik kimliği, ses karşılaştırması, sesin özgünlüğü, montaj/sahtecilik değerlendirmesi veya görüntü incelemesi 56.12 metne dönüştürme işinden ayrı ele alınmalıdır. Bunların 56.11 veya başka uzmanlık kodlarıyla ilişkisi uzman/hukukçu tarafından doğrulanmadan modüle dahil edilmez.

## Pilotun kanıt ihtiyacı

Bu akış mevcut uygulama beyanlarından türetilmiş ürün hipotezidir; gerçek bilirkişilerce doğrulanmış iş akışı değildir.

## Kaynaklar

- [Temel ve Alt Uzmanlık Alanları ve Aranan Nitelikler — 22.01.2026 PDF](https://bilirkisilik.adalet.gov.tr/Resimler/SayfaDokuman/20260122151908585Bilirkişilik%20Temel%20ve%20Alt%20Uzmanlık%20Alanları%20ile%20Bilirkişilerde%20Aranan%20Nitelikler.pdf)
- [SWGDE Best Practices for Forensic Audio, v2.5 (09.06.2022)](https://www.swgde.org/documents/published-complete-listing/08-a-001-swgde-best-practices-for-forensic-audio/)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
