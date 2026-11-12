# Alan Modeli

> **Durum:** Görev Profili kavramlarıyla güncellendi — teknoloji/veri tabanı seçimi değildir  
> **Güncelleme:** 13 Kasım 2026

Bu model alan kavramlarını tanımlar; tablo, sınıf, API veya veri tabanı tasarımını henüz kesinleştirmez. Gerçek görev verisi yerel ve korumalı ortamda tutulur; public GitHub'a örnek vaka kaydı konmaz.

## Ortak kavramlar

| Varlık | Alanlar (taslak) | Not |
|---|---|---|
| Workspace | id, locale, created_at, settings | Kullanıcının yerel çalışma alanı |
| Assignment | id, local_reference, authority, appointed_at, status, expertise_context | Her görevlendirme için ayrı ana kayıt |
| AssignmentSourceDocument | id, assignment_id, document_type, local_path, hash, imported_at, version | Görevlendirme, tutanak, dizi pusulası ve ek kaynak belgeler |
| FieldProvenance | entity_id, field_name, value, source_document_id, page/position, extraction_method, confidence, state | Her çıkarılmış alanın kaynağı ve güven bilgisi |
| AssignmentScope | assignment_id, subject, boundaries, exclusions, source_ref | İnceleme konusu, kapsam ve sınırlar |
| AssignmentQuestion | id, assignment_id, text, order, response_state, report_section_ref | Her cevaplanacak soru ayrı kayıt; kanaati uygulama yazmaz |
| DeadlineRule | assignment_id, duration, unit, start_event, start_date, due_date, extension, source_ref | Süre, başlangıç ve son tarih birbirinden ayrı |
| AssignmentMaterialRequirement | id, assignment_id, expected_item, source_ref, channel | Beklenen materyal ve teslim yöntemi |
| EvidenceItem | id, assignment_id, source, received_at, physical/digital, local_path, SHA-256, metadata, custody_note, state | Gerçek materyal kaydı; yerel korumalı alan |
| DerivedArtifact | id, parent_evidence_id, operation, tool/version/parameters, output_hash | Türetilmiş çıktının kökeni |
| ReportProfile | assignment_id, authority_type, template_id, template_version, required_sections, source_ref | Göreve uygun rapor yapısı |
| DeliverableRequirement | assignment_id, file_format, signature_type, copy_count, delivery_channel, physical_return | Yalnızca göreve özgü açık teslim koşulları |
| WorkLog | timestamp, method, instrument, operator_note, artifact_references | Teknik işlem günlüğü |
| ReportDraft | assignment_id, sections, attachments, version, status | Her görev için ayrı temiz çıktı |
| DeliveryRecord | assignment_id, channel, timestamp, user_confirmed_state, proof_reference | Resmî teslim kullanıcı tarafından doğrulanır |
| RetentionEvent | policy, decision, action, timestamp | Saklama/silme politikası hukukçu ile belirlenir |

## Göreve göre değişen alanlar

- Bir görevde fizikî dosya ve USB; diğerinde yalnızca UYAP elektronik erişimi olabilir.
- Materyal sayısı, türü, boyutu, süresi ve beklenen ekler sabit değildir.
- Süre, süre başlangıç olayı ve ek süre her görevlendirmede değişebilir.
- Görev soruları ve sınırlar dosyaya özeldir.
- Rapor şablonu merci/yargı türü ve görev türüne göre değişebilir.
- Suret/nüsha, çıktı biçimi, imza ve fiziki iade talimatı yalnızca açıkça belirtilen görevlere uygulanır.

## Kaynak ve çıkarım izi

Görevlendirme belgesinden çıkarılan her alan, kaynak belge ve sayfa/metin konumuna bağlanır. Metin çıkarımı/OCR/model güveni, alanın hukukî yorumunun doğruluğu anlamına gelmez. Kaynaklar çelişirse iki ifade de saklanır ve ilgili alan istisnaya alınır.

## Uzmanlık modülü sınırı

56.12 modülü AudioEvidence, AudioMetadata, TranscriptRun, TranscriptSegment, TranscriptRevision ve SpeakerLabel gibi alanlar içerebilir. Bu alanlar ortak çekirdekten ayrıdır; konuşmacı kimlik biyometrisi veya kişi teşhisi alanı eklenmez.

## Gizlilik

Gerçek dosya numarası, taraf kimliği, belge, ses, hash manifesti ve teslim kaydı hassas yerel görev verisidir. Örnek şema ve sentetik test verisi dışında public issue, fixture veya commit'e taşınmaz.

## Kaynaklar

- [Bilirkişilik Yönetmeliği — m.51–52](https://www.lexpera.com.tr/mevzuat/yonetmelikler/bilirkisilik-yonetmeligi-2)
- [Bilirkişi Rapor Şablonları — Bilirkişilik Daire Başkanlığı](https://bilirkisilik.adalet.gov.tr/Home/SayfaDetay/bilirkisi-rapor-sablonlari14032022105509)
- [UYAP Doküman Editörü — resmî yardım](https://uyap.gov.tr/Uyap-Editor-Yardim)
