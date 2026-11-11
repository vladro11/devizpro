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


## Release V46 — 12.11.2026 (actualizare funcțională)

- Baza: arhiva încărcată `DevizPRO_V45_PRO_BILINGUAL(1).zip`; codul și documentele V45 au fost păstrate ca punct de plecare.
- Interfața Măsurători primește un layout mai compact și ordonat: antet de încăpere, acțiuni grupate, carduri de obiect, sumar și stiluri responsive pentru ecrane mici.
- Fluxul nou de grupare folosește structura existentă `room.merges` / `componentIds`, pentru compatibilitate cu grupările vechi. Obiectele grupate sunt ascunse în lista principală și apar în interiorul grupării la extindere.
- Gruparea cere minimum două obiecte și verifică unitatea calculată în Măsurători. La unități diferite afișează avertizare și nu creează gruparea.
- Gruparea are meniu pentru redenumire, modificarea componenței și ștergere. Ștergerea elimină numai înregistrarea grupului; obiectele, dimensiunile și fotografiile rămân în încăpere.
- MINUS are un selector clar și buton explicit de aplicare. Sunt oferite obiecte compatibile din aceeași încăpere; logica existentă verifică unitatea și limitele cantității înainte de clipping.
- Validarea unității a fost eliminată din transferul riglei către liniile Deviz nou. Unitatea lucrării din deviz rămâne personalizată de utilizator; cantitatea preluată nu este blocată de comparația unităților.
- Eticheta publică V45 a fost eliminată din brand și titlul browserului; versiunea 46 rămâne în metadate/cache tehnic. Numele și pictogramele instalabile nu afișează numărul versiunii.
- Datele existente `dp_measurements`, `room.elements`, `photos`, `clippedTo` și `merges` nu au fost migrate sau șterse.
- Limitări explicite: biblioteca extinsă de fotografii reale (mii de imagini), editorul foto avansat, redesignul complet al tuturor modulelor și testele fizice pe iPad/Android/Windows nu sunt incluse/confirmate în acest release. Cardurile păstrează încă selectorul de tip și pictograma existentă; imaginile foto reprezentative urmează într-un release separat după stabilirea catalogului de resurse.


## Release V46 — 12 Nov 2026 (functional update)

- Base: uploaded archive `DevizPRO_V45_PRO_BILINGUAL(1).zip`; V45 source and documentation were retained as the starting point.
- Measurements receives a more compact, ordered layout: room header, grouped actions, object cards, summary, and responsive styling for small screens.
- The new grouping workflow reuses the existing `room.merges` / `componentIds` structure for compatibility with legacy groups. Grouped objects are hidden in the main list and shown inside the expanded group.
- Grouping requires at least two objects and validates the calculated unit inside Measurements. Mixed units show a warning and do not create a group.
- Each group has a menu to rename it, edit its membership, or delete the group. Deletion removes only the group record; object records, dimensions, and photos remain in the room.
- MINUS now has a clear selector and explicit apply action. Compatible objects from the same room are offered; existing clipping logic validates units and remaining quantity before applying the clip.
- Unit validation was removed from the ruler transfer into New Estimate lines. Work units in estimates remain user-defined; imported quantities are no longer blocked by a unit comparison.
- The public V45 suffix was removed from the brand and browser title; version 46 remains in technical metadata/cache only. The installed app name and icons do not show a version number.
- Existing `dp_measurements`, `room.elements`, `photos`, `clippedTo`, and `merges` data were not migrated or deleted.
- Explicit limitations: a large library of real photos (thousands of images), the advanced photo editor, a full redesign of every module, and physical iPad/Android/Windows tests are not included/confirmed in this release. Object cards still use the existing type selector and pictogram; representative photo assets are deferred to a separate release after the asset catalog is defined.

## V46 — decizii tehnice / technical decisions

### Română
- Reutilizăm `room.merges` și `componentIds`, în loc să introducem un al doilea model de grupare. Astfel, grupările existente pot fi afișate în noul UI și nu este necesară migrare de date.
- Obiectele nu sunt mutate într-o structură nouă; grupul ține doar referințe la ID-urile lor. Această alegere păstrează fotografiile și dimensiunile la desfacere.
- Validarea unității este locală modulului Măsurători. Transferul în Deviz nou nu impune unitatea calculată, deoarece lucrările au unități definite manual de utilizator.
- Versiunea 46 rămâne în metadate/cache; eticheta de versiune nu este afișată în brand sau titlul aplicației.

### English
- Reuse `room.merges` and `componentIds` instead of introducing a second grouping model. Existing groups can therefore render in the new UI without a data migration.
- Objects are not moved into a new structure; a group stores references to their IDs only. This preserves photos and dimensions when a group is dissolved.
- Unit validation is scoped to Measurements. Transfer into New Estimate does not enforce the calculated unit because estimate work units are manually defined by the user.
- Version 46 remains in metadata/cache; the version suffix is not shown in the app brand or title.
