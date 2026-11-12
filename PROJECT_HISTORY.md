# DevizPRO — Istoric general al proiectului

**Actualizat:** V45 · 12.11.2026  
**Notă privind acuratețea:** istoricul exact al tuturor arhivelor V1–V41 nu este disponibil în această sesiune. Nu completăm golurile prin presupuneri.

## V1–V40 — istoric incomplet

Utilizatorul a descris proiectul ca aplicație web locală/offline pentru devize de construcții, pornită dintr-un catalog Excel. Cerințele istorice cunoscute includ catalog bilingv RO/RU, devize, export, evidență/grupe, backup și utilizare pe iPad/Android/Windows. Detaliile exacte pe fiecare număr de versiune nu sunt certificate fără arhivele respective.

## V41 — strat de funcționalități menționat în istoricul proiectului

README-ul V42 și documentația V44 indică existența unui strat de funcții V41 pentru Măsurători și alte extensii. Detaliile sunt moștenite din documentația proiectului, nu revalidate individual în această versiune.

## V42 — 11.11.2026 — bază recuperată

- Arhiva conține `index.html`, `service-worker.js`, `manifest.webmanifest`, pictograme și documentație minimală.
- README-ul V42 descrie integrarea Măsurători → Deviz nou, încăperi, obiecte, MERGE, MINUS/Clipping, fotografii și reordonare.
- Verificarea efectuată în sesiunea V44 a raportat că toate blocurile JavaScript inline din V42 treceau `node --check`.
- V42 a fost aleasă ca bază de recuperare după eșecul V43.

## V43 — 12.11.2026 — release eșuat

- Utilizatorul a raportat că arhiva instalată se comporta ca V42 și README-ul indica tot V42.
- Utilizatorul a raportat că Măsurători nu mai funcționa.
- Verificarea documentată în V44 a identificat erori de sintaxă în scripturile inline `dpV38Core` și `dpV42ShareAndSpreadsheet` din arhivele V43 analizate.
- Descărcarea V43 a eșuat pentru utilizator; un link redenumit nu a rezolvat problema de încredere în build.
- Concluzie: V43 nu este bază validă.

## V44 — 12.11.2026 — restabilizare

- Reconstruită din arhiva V42 originală, nu din V43.
- Eticheta antetului V44 și cache-ul Service Worker V44 au fost setate.
- README și documentele proiectului au fost adăugate.
- CSS-ul care desena semnul MINUS decorativ duplicat pe selectorul MERGE a fost eliminat conform notelor V44; acțiunea funcțională `− Minus` a fost păstrată.
- Nu au fost implementate toate cerințele UI avansate pentru Măsurători; acestea au rămas documentate ca restante.
- Utilizatorul nu a instalat/testat V44 înainte de a cere V45.

## V45 — 12.11.2026 — continuitate și documentare

- Baza: arhiva V44 furnizată în conversație.
- Public version metadata, titlul paginii și antetul au fost sincronizate la V45; identificatorul cache Service Worker a fost incrementat la V45.
- A fost introdus protocolul AI obligatoriu, istoricul conversațiilor disponibil, jurnalul deciziilor tehnice, explicații de cod, starea versiunii și lucrările restante.
- Nu au fost făcute redesign-uri ale modulului Măsurători în V45; prioritatea a fost documentarea și sincronizarea versiunii, deoarece utilizatorul nu testase încă V44.
- V45 nu este declarată stabilă până când utilizatorul nu confirmă instalarea și testarea Măsurătorilor.

## Regula pentru completări

Fiecare release viitor adaugă o secțiune nouă la final. Nu se rescriu secțiunile anterioare. Dacă o informație istorică este corectată, se adaugă o notă de corecție datată, cu motiv și sursă.

---

# DevizPRO — Project History (English)

**Updated:** V45 bilingual documentation update · 12 November 2026  
**Accuracy note:** The complete exact history of every V1–V41 archive is not available in this session. Missing details must not be invented.

## V1–V40 — incomplete historical record

The project is a free, offline-first local web application for construction estimates, originally based on an Excel work-price catalogue. Known historical requirements include a Romanian/Russian bilingual work catalogue, estimates, PDF/print and Excel/Numbers export, accounting/groups, backups, and use on iPad, Android, and Windows. Exact per-version changes are not certified without the corresponding archives.

## V41 — feature layer referenced by project history

The V42 README and V44 documentation refer to a V41 feature layer for Measurements and other extensions. These details are inherited from project documentation and have not been independently revalidated in this release.

## V42 — 11 November 2026 — recovered baseline

- Archive includes `index.html`, `service-worker.js`, `manifest.webmanifest`, icons, and minimal documentation.
- Its README describes Measurements-to-New Estimate integration, rooms, objects, MERGE, MINUS/Clipping, photos, and reordering.
- During the V44 session, all extracted inline JavaScript blocks were reported to pass `node --check`.

## V43 — 11–12 November 2026 — reported failure

The user reported that V43 appeared identical to V42 and Measurements stopped working. V43 is therefore not treated as a user-confirmed stable baseline.

## V44 — 12 November 2026 — restoration build

V44 was rebuilt from V42 after the V43 report. Its documentation records removal of a decorative duplicate MINUS pseudo-element while retaining the actual `− Minus` action. The user had not yet confirmed the visual result on a device.

## V45 — 12 November 2026 — versioning and AI continuity

V45 inherited the V44 application code, synchronized public version labels and Service Worker cache identity, and added a portable AI documentation system. It did not implement the requested Measurements redesign. Physical device testing was not performed by the assistant.

## V45 bilingual documentation update

This update adds English content alongside Romanian in the project documents and provides a consolidated bilingual Word file. Application functionality and data structures remain unchanged.


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


---

## V47 — corectare după feedback și redesign vizual global (12.11.2026)

### Ce s-a schimbat efectiv în cod
- A fost adăugat un sistem vizual global pentru toate ecranele: antet, navigare, carduri, indicatori, formulare, butoane, tabele, ferestre modale și elemente responsive.
- Paleta este verde/alb, cu suprafețe luminoase, colțuri rotunjite, umbre discrete și stări de interacțiune.
- Numele public al aplicației rămâne `DevizPRO`; numărul versiunii este numai în metadatele tehnice și cache.
- Fluxul de creare a grupării folosește acum un dialog dedicat pentru nume, nu prompt-ul nativ al browserului.
- Aplicarea MINUS verifică unitatea și cantitatea disponibilă înainte să închidă dialogul; o operație invalidă nu mai închide fereastra și nu modifică obiectele.
- A fost păstrată compatibilitatea cu structura de date existentă V45/V46; nu se șterg intenționat localStorage/IndexedDB.
- Comanda/selectorul MERGE și butonul secundar gol de editare au fost eliminate din markup-ul obiectelor randate în Măsurători.

### Ce NU este încă finalizat
- Biblioteca mare de fotografii reale (ținta discutată: 2.000–3.000) și selectorul vizual complet de tipuri de obiecte.
- Editorul foto avansat (desen, culori, grosime, text, undo/redo, copie editată și păstrarea originalului).
- Redesignul MOVE și testarea gesturilor tactile.
- Testare fizică iPad, Android și Windows.
- Verificare interactivă completă în browser: execuția Chromium headless a depășit limita de timp a mediului; nu se declară test browser PASS.

### Teste reale efectuate
- Toate cele 11 blocuri JavaScript inline au trecut `node --check`.
- Parsarea HTML a reușit; au fost numărate 218 ID-uri în documentul sursă.
- Integritatea arhivei ZIP se verifică separat înainte de livrare.
- Nu au fost efectuate teste pe dispozitive fizice și nu se pretinde că au fost.

### Regulă de continuare
V47 este o etapă de corectare și redesign global, nu o versiune finală a produsului. Următoarea versiune numerică este V48. Înainte de alte funcții, trebuie testate pe dispozitiv gruparea, MINUS, layout-ul tuturor modulelor și păstrarea datelor. Nu se schimbă istoricul anterior; acest addendum se adaugă cronologic.

## V47 — correction after feedback and global visual redesign (12 Nov 2026)

### Actual source-code changes
- Added an application-wide visual system covering the header, navigation, cards, metrics, forms, buttons, tables, modal dialogs, and responsive layouts.
- Applied a green-and-white palette, brighter surfaces, rounded corners, subtle shadows, and interaction states.
- The public app name remains `DevizPRO`; the version number is limited to technical metadata and cache identifiers.
- Group creation now uses a dedicated name dialog instead of the browser's native prompt.
- MINUS validates the unit and available quantity before closing the dialog; an invalid operation keeps the dialog open and does not modify objects.
- Existing V45/V46 data structures are retained; no intentional localStorage/IndexedDB deletion was added.
- The MERGE selector and the redundant empty edit button are removed from rendered measurement-object markup.

### Still NOT complete
- Large photographic asset library (the discussed target is 2,000–3,000 images) and a complete visual object-type picker.
- Advanced photo editor (drawing, colors, brush thickness, text, undo/redo, edited copies, original preservation).
- MOVE redesign and touch-gesture testing.
- Physical iPad, Android, and Windows testing.
- Full interactive browser verification: headless Chromium exceeded the environment time limit; browser testing is NOT marked PASS.

### Tests actually performed
- All 11 inline JavaScript blocks passed `node --check`.
- HTML parsing succeeded; 218 IDs were counted in the source document.
- ZIP integrity is checked separately before delivery.
- No physical-device testing was performed or claimed.

### Continuity rule
V47 is a correction and global redesign stage, not a final product release. The next numeric release is V48. Before adding more features, test grouping, MINUS, all-module layouts, and data preservation on a device. Previous history remains intact; this addendum is appended chronologically.
