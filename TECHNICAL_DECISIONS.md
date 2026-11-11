# DevizPRO — Technical Decisions Journal

Jurnal cumulativ al deciziilor tehnice. Documentează motivele tehnice și alternativele, nu raționamentul intern privat al modelului.

## TD-045-001 — Folosirea V44 ca bază pentru V45

- **Context:** utilizatorul nu a instalat/testat încă V44; V43 a fost raportată ca eșuată, iar V44 a fost creată ca restabilizare din V42.
- **Decizie:** V45 se construiește direct din arhiva V44 furnizată. Nu se încearcă acum redesign-ul complet al Măsurători.
- **Motiv:** prioritatea este să existe o versiune clar identificată și o documentație portabilă, fără a introduce încă un strat UI netestat înainte ca utilizatorul să confirme că baza V44 funcționează.
- **Alternative:** (a) implementarea imediată a tuturor cerințelor Măsurători; (b) revenirea directă la V42. Prima variantă are risc de regresie înainte de testarea V44; a doua ar elimina corecțiile/documentația V44. S-a ales continuitatea V44.
- **Impact cod:** schimbate doar etichetele publice ale versiunii și identificatorul cache-ului Service Worker. Funcțiile interne istorice `dpV42...` nu au fost redenumite.
- **Risc/rămâne:** V44/V45 nu au fost testate fizic pe iPad, telefon sau Windows de către asistent.

## TD-045-002 — Documentație portabilă AI CORE

- **Context:** utilizatorul dorește ca un alt chat/cont să poată continua proiectul prin încărcarea arhivei.
- **Decizie:** instrucțiuni obligatorii, stare JSON, istoric conversațional, istoric de proiect, specificație, buguri, teste, decizii, explicații de cod și lucrări restante.
- **Motiv:** un set de fișiere text poate fi transferat odată cu ZIP-ul și inspectat de orice asistent care primește arhiva.
- **Limită:** ZIP-ul nu poate forța automat citirea și nu poate accesa alte conversații neatașate. Protocolul cere citirea explicită după încărcarea arhivei.

## TD-045-003 — Jurnal append-only și delimitarea transcriptului

- **Decizie:** jurnalele sunt cumulative; nu se șterg intrări vechi. Mesajele disponibile se păstrează cât mai aproape de original; informațiile recuperate ca rezumat sunt etichetate ca rezumat.
- **Motiv:** evitarea fabricării unui istoric complet când conversațiile vechi nu sunt disponibile în chatul curent.

## TD-045-004 — Explicații tehnice în locul raționamentului intern privat

- **Decizie:** se documentează problema, dovezile, alternativele, criteriile, decizia tehnică, codul și rezultatele testelor. Nu se publică raționamentul intern privat al modelului.
- **Motiv:** utilizatorul poate învăța programare din explicații verificabile, fără a pretinde acces la procese interne private.

---

# DevizPRO — Technical Decisions Journal (English)

Cumulative decision log. Document technical reasons, alternatives, consequences, and risks—not private hidden model reasoning.

## TD-045-001 — Use V44 as the V45 baseline

- **Context:** The user had not installed/tested V44 yet; V43 was reported as failing, and V44 was created as a restoration from V42.
- **Decision:** Build V45 directly from the V44 archive. Do not attempt the full Measurements redesign in this release.
- **Reason:** Establish a clearly identified baseline and portable documentation without introducing a large, untested UI layer before the user confirms V44 works.
- **Alternatives:** (a) implement all Measurements requests immediately; (b) return directly to V42. Option (a) risks regressions before V44 is tested; option (b) would discard V44 corrections/documentation. Continuity from V44 was selected.
- **Code impact:** Only public version labels and the Service Worker cache identifier changed. Historical internal function names such as `dpV42...` were not renamed.
- **Remaining risk:** The assistant did not physically test V44/V45 on iPad, phone, or Windows.

## TD-045-002 — Portable AI CORE documentation

- **Context:** The user wants another chat/account to continue development after receiving the archive.
- **Decision:** Include mandatory instructions, JSON state, conversation history, project history, specification, requirements, bug log, tests, architecture, technical decisions, code explanations, and backlog.
- **Reason:** Plain files travel with the ZIP and can be inspected by any assistant that receives the archive. They cannot force another chat to read them automatically; the user must upload the archive and the assistant must follow the startup instructions.

## TD-045-003 — Romanian-English documentation

- **Context:** The user wants to learn from the project documentation and understands English.
- **Decision:** Provide complete Romanian and English content in every human-readable project document and a consolidated bilingual Word file.
- **Reason:** Parallel language content improves portability and makes technical terminology accessible. Machine-readable JSON keys remain stable to avoid breaking tooling.
- **Application impact:** None; this is documentation-only.
