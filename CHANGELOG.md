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


## V2 E1 — 21.11.2026
### Schimbări aplicate
- Începută seria nouă de ediții: V2 E1.
- Versiunea V45 eliminată din antetul vizibil al aplicației.
- Titlul filei browserului și meta application-version actualizate la V2 E1.
- Cache-ul Service Worker actualizat la identificatorul unic V2 E1.
- Codul și datele moștenite sunt păstrate; nu s-au schimbat cheile localStorage/IndexedDB.

### Plan confirmat pentru edițiile următoare
- Carduri Măsurători compacte; pictograma selectorului în stânga selectorului de tip; butonul plus în dreapta.
- Acțiunile Adaugă / Salvează în setări / X apar numai în fereastra deschisă prin plus.
- MINUS existent se păstrează și se integrează în cardul compact.
- Fotografii asociate obiectului și agregate automat în galeria încăperii; fotografii generale ale încăperii separat.
- Pictograme personalizate, recente și biblioteca aplicației.
- Reordonare prin drag-and-drop și butoane sus/jos.
- Home, navigare adaptivă telefon/tabletă/desktop, butoane Înapoi și Setări reorganizate.

### Testare și limite
- Verificarea sintaxei JavaScript și integrității arhivei se execută pentru E1.
- Testarea în browser și pe iPad/telefon/desktop nu este efectuată de acest build.
- Redesign-ul funcțional rămâne în lucru; vezi PENDING_WORK.md.


## V2 E2 — 21.11.2026 — Measurements compact upgrade
### Implementat
- Bază: V2 E1 furnizată de utilizator; codul aplicației și cheile de stocare moștenite au fost păstrate.
- Titlul filei browserului și meta application-version actualizate la V2 E2; Service Worker cache actualizat la V2 E2. Nu există etichetă de versiune vizibilă în interfață.
- Cardurile obiectelor din Măsurători au fost reorganizate: pictogramă în stânga, selector Obiect/Tip la mijloc și buton + în dreapta.
- Dimensiunile sunt compacte și folosesc `inputmode=decimal`; pe telefon se așază într-un rând de trei coloane (sau se adaptează când tipul are patru câmpuri).
- Camera și Galeria sunt controale compacte numai cu pictogramă; fotografiile existente, fluxul de import și miniaturile au fost păstrate.
- Adăugat dialog pentru tip nou cu două acțiuni: Adaugă (tip temporar pentru măsurătoarea curentă) și Salvează în setări (catalog general + încăperea curentă).
- Adăugate butoane sus/jos pentru reordonarea încăperilor și obiectelor; drag-and-drop moștenit este păstrat, nu eliminat.
- Păstrate fluxurile existente MERGE, MINUS/Clipping, transferul în Deviz nou și schema de date.
### Nu sunt încă implementate
- Pictograme complet personalizate (upload/desenare, redenumire și ștergere) și secțiunea „recente”.
- Comutator de vizibilitate cu ochi; checkbox-ul existent „Pentru deviz” rămâne selecție pentru deviz și nu este reinterpretat ca vizibilitate.
- Redesign complet MOVE fără drag-and-drop; butoanele sus/jos sunt alternativa sigură adăugată.
- Galerie de încăpere care agregă fotografiile obiectelor fără duplicarea fișierelor.
- Navigare diferită telefon/tabletă/desktop în întregime; E2 introduce bara de jos pe telefoane, păstrând navigarea existentă pe ecrane mai mari.
- Home dashboard extins și reorganizarea completă a Setărilor.
### Testare
- Toate cele 11 blocuri JavaScript inline trec `node --check`.
- Parser HTML: document parsabil; 0 ID-uri duplicate statice.
- Service Worker: toate căile ASSETS verificate.
- ZIP: verificare integritate efectuată după împachetare.
- Browser real și dispozitive fizice: neconfirmate; lansarea headless Chromium nu a putut fi finalizată în mediul de lucru.
- E2 nu este declarată stabilă până la testarea pe dispozitive și confirmarea utilizatorului.

## V2 E2 — 21 November 2026 — Compact Measurements upgrade (English)
### Implemented
- Base: user-supplied V2 E1; inherited application code and storage keys preserved.
- Browser tab title and application-version metadata updated to V2 E2; Service Worker cache updated. No version label is shown inside the app UI.
- Measurement object cards now place the icon at left, Object/Type selector in the middle, and + at right.
- Dimension fields are compact and use decimal input mode; phone layout adapts to three columns (or four when the type has four dimensions).
- Camera and Gallery controls are compact icon-only buttons; existing photo import, storage, and thumbnails are retained.
- Added a new-type dialog with Add (temporary/current measurement) and Save to settings (permanent catalogue and current room) actions.
- Added up/down reorder controls for rooms and objects. The inherited drag-and-drop remains available.
- Existing MERGE, MINUS/Clipping, New Estimate transfer, and data schema are retained.
### Not yet implemented
- Fully custom pictograms with upload/drawing, rename/delete, and recent-items section.
- Eye-based visibility control; existing “For estimate” checkbox remains estimate selection and is not repurposed as visibility.
- Full replacement of drag-and-drop; up/down buttons are the added reliable alternative.
- Room gallery aggregation of object photos without duplicate files.
- Fully adaptive navigation across phone/tablet/desktop; E2 adds bottom navigation on phones while retaining existing navigation on larger screens.
- Expanded Home dashboard and complete Settings redesign.
### Tests
- All 11 inline JavaScript blocks pass `node --check`.
- HTML parser: parseable document; zero duplicate static IDs.
- Service Worker asset paths checked.
- ZIP integrity checked after packaging.
- Full browser and physical-device tests remain unconfirmed; headless Chromium did not complete in the working environment.
- E2 is not declared stable until device testing and user confirmation.
