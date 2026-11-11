# DevizPRO — Changelog

Istoricul este cumulativ. Nu șterge și nu rescrie intrările anterioare; adaugă corecții ca note noi.

## V45 — 12.11.2026 — AI Core & documentație cumulativă
- Bază: V44 PRO.
- Versiunea publică sincronizată la V45 în meta, titlu și antet.
- Service Worker cache incrementat la identificator V45.
- Adăugat protocolul strict `00_MANDATORY_INSTRUCTIONS.md`.
- Adăugat jurnalul conversațional disponibil `USER_CHAT_LOG_HISTORY.md`; istoricul anterior incomplet este etichetat ca rezumat, nu transcriere integrală.
- Adăugate `PROJECT_HISTORY.md`, `VERSION_STATE.json`, `TECHNICAL_DECISIONS.md`, `CODE_EXPLANATIONS.md`, `PENDING_WORK.md`.
- Actualizate README, specificația, cerințele, arhitectura, bugurile și checklist-ul.
- Codul principal al aplicației este moștenit din V44; V45 nu implementează încă redesign-ul avansat Măsurători.
- Utilizatorul nu testase V44 la momentul creării V45; V45 nu este declarată stabilă.

## V44 — 12.11.2026 — restabilizare
- Reconstruită din V42 după eșecul V43.
- Antet V44 și cache V44.
- Eliminat CSS-ul care desena semnul MINUS decorativ duplicat pe selectorul MERGE; acțiunea funcțională `− Minus` este păstrată conform documentației V44.
- Adăugată documentație inițială de proiect.
- Nu au fost implementate toate cerințele avansate pentru carduri, MOVE, editor foto, MINUS și grupare.
- Utilizatorul nu a instalat/testat V44 înainte de solicitarea V45.

## V43 — 12.11.2026 — eșec, nu release valid
- Utilizatorul a raportat că instalarea se comporta ca V42 și README-ul indica V42.
- Utilizatorul a raportat că Măsurători nu mai funcționa.
- Documentația V44 consemnează erori de sintaxă în scripturile inline `dpV38Core` și `dpV42ShareAndSpreadsheet` din arhivele V43 analizate.
- Nu se folosește ca bază.

## V42 — 11.11.2026 — bază recuperată
- README-ul V42 descrie Măsurători, MERGE, MINUS/Clipping, fotografii, integrarea cu Deviz nou și funcții de export/partajare.
- Verificarea efectuată în etapa V44 a raportat că blocurile JavaScript inline V42 treceau `node --check`.

## V1–V41 — istoric incomplet
- Arhivele originale complete nu sunt disponibile în contextul acestei versiuni.
- Nu se inventează funcții exacte pe fiecare versiune. Detaliile recuperate din documentația V42/V44 sunt marcate ca atare în `PROJECT_HISTORY.md`.

---

# DevizPRO — Changelog (English)

The changelog is cumulative. Never delete or rewrite previous entries; append corrections as new dated notes.

## V45 — 12 November 2026 — AI Core and cumulative documentation

- Base: V44 PRO.
- Public version synchronized to V45 in meta tag, page title, and visible header.
- Service Worker cache identifier incremented to V45.
- Added strict `00_MANDATORY_INSTRUCTIONS.md` protocol.
- Added available conversation record `USER_CHAT_LOG_HISTORY.md`; incomplete older history is labelled as summary, not a full transcript.
- Added project history, JSON state, technical decisions, code explanations, and backlog.
- Updated README, specification, requirements, architecture, bug log, and checklist.
- Main application code is inherited from V44; V45 does not yet implement the advanced Measurements redesign.
- User had not tested V44 when V45 was created; V45 is not declared stable.

## V45 bilingual documentation update — 12 November 2026

- Added English content alongside Romanian in every human-readable project document.
- Added a consolidated bilingual Word document for reading and learning.
- Kept application code, storage schemas, and public application version unchanged.
- Added explicit test-status notes; no physical device test is claimed.

## V44 — 12 November 2026 — restoration build

- Rebuilt from V42 after the reported V43 failure.
- Visible V44 header and V44 Service Worker cache identifier.
- Documented removal of the decorative duplicate MINUS pseudo-element while retaining the actual MINUS action; device confirmation pending.


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
