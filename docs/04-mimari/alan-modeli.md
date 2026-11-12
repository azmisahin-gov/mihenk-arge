# Alan Modeli

> **Durum:** TASLAK  
> **Araştırma tarihi:** 12 Kasım 2026  
> **Kapsam notu:** İlk masa başı araştırma sürümü; hukukçu ve gerçek bilirkişi doğrulaması gerektirir.

## Ortak kavramlar

| Varlık | Alanlar (taslak) | Not |
|---|---|---|
| Workspace | id, locale, created_at, settings | Kullanıcı yerel çalışma alanı |
| Assignment | id, court/authority label, case reference (minimize), appointed_at, due_at, status | Resmî dosya numarası yerine mümkün olduğunca yerel kimlik kullanılabilir |
| AssignmentQuestion | id, assignment_id, text, order, response_state | Görev sorusu ve cevap durumu; kanaati uygulama yazmaz |
| ScopeCheck | expertise code, competence self-check, conflict check, note | Karar kullanıcıya ait |
| EvidenceItem | id, source description, received_at, original path, SHA-256, metadata, custody note | Hash + teslim kaydı; yasal zincir garantisi değil |
| DerivedArtifact | id, parent evidence id, operation, tool/version/parameters, output hash | Türevlerin kökeni |
| WorkLog | timestamp, method, instrument, operator note, artifact references | Teknik çalışma günlüğü |
| ReportDraft | assignment_id, sections, attachments, status | Taslak; resmî teslim değil |
| DeliveryRecord | channel, timestamp, user-confirmed state, proof reference | Resmî portal teslimi manuel doğrulanır |
| Expense | date, category, amount, receipt reference, status | Muhasebe kaydı; resmî ödeme değil |
| RetentionEvent | policy, decision, action, timestamp | Saklama/silme politikası hukukçu ile belirlenir |

## Uzmanlık modülü veri sınırı

56.12 modülü AudioEvidence, AudioMetadata, TranscriptRun, TranscriptSegment, TranscriptRevision ve SpeakerLabel gibi alanları tutabilir. Genel çekirdekten ayrılmalı; konuşmacı kimlik biyometrisi alanı eklenmemelidir.

## Kaynaklar

- [6754 sayılı Bilirkişilik Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/104136)
- [6100 sayılı Hukuk Muhakemeleri Kanunu — Adalet Bakanlığı Mevzuat ve İçtihat Programı](https://mevzuat.adalet.gov.tr/mevzuat/103103)
- [5271 sayılı Ceza Muhakemesi Kanunu — resmî PDF](https://aile.gov.tr/uploads/chgm/uploads/pages/kanunlar/5271-sayili-ceza-muhakemesi-kanunu.pdf)
- [forensic-transcriber GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber)
- [forensic-transcriber-next GitHub deposu](https://github.com/azmisahin-gov/forensic-transcriber-next)
