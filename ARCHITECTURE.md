# DevizPRO — Architecture Notes

## Structura aplicației
- `index.html`: aplicația client, structura UI, stiluri și scripturi JavaScript inline.
- `service-worker.js`: cache offline și actualizarea resurselor statice.
- `manifest.webmanifest`: metadate PWA.
- `icon-192.png`, `icon-512.png`: pictograme PWA.
- `QR-LICENSE.txt`: notă de licență pentru biblioteca QR.
- `00_MANDATORY_INSTRUCTIONS.md` și celelalte documente: protocol, specificație, istoric, decizii, explicații și teste.

## Model de execuție
Aplicație web client-side, offline-first prin Service Worker. Interfața și funcțiile sunt în principal în `index.html`; scripturile inline se execută în ordinea apariției și unele straturi extind sau suprascriu funcții anterioare. Ordinea scripturilor și sintaxa fiecărui bloc sunt critice.

## Măsurători
Documentația V42/V44 descrie încăperi, obiecte, dimensiuni, MERGE, MINUS/Clipping, fotografii și transferul cantităților în Deviz nou. V45 păstrează codul moștenit din V44 și nu schimbă logica modulului Măsurători. Verifică funcțiile reale și testele înainte de orice intervenție.

## Persistență
Nu schimba cheile localStorage/IndexedDB și nu migra structura fără backup și migrare testată. V45 nu introduce ștergerea intenționată a datelor locale.

## Service Worker
Cache-ul trebuie să aibă identificator unic per release. `ASSETS` trebuie să conțină căi existente. Verifică instalarea/activarea și încărcarea noii versiuni pe iOS/Android. Schimbarea cache-ului nu înseamnă ștergerea datelor utilizatorului.

## Documentație ca parte din arhitectura proiectului
Dosarul de documentație este memoria portabilă a proiectului, nu o componentă runtime a aplicației. Un chat nou trebuie să citească `00_MANDATORY_INSTRUCTIONS.md` și restul fișierelor după ce utilizatorul atașează ZIP-ul. Nu există mecanism prin care ZIP-ul să forțeze singur ChatGPT să le citească.

## Principii de modificare
- Patch-uri mici, localizate; păstrează arhiva de bază.
- Nu modifica blocurile `<script>` prin concatenări fragile.
- Testează fiecare script inline separat cu `node --check`.
- Testează funcțional după testul de sintaxă.
- Gesturile touch trebuie testate pe Safari iOS; Pointer Events, pointer capture și `touch-action` pot avea diferențe practice.

---

# DevizPRO — Architecture Notes (English)

## Application structure

- `index.html`: client application, UI structure, styles, and inline JavaScript.
- `service-worker.js`: offline cache and static-resource update lifecycle.
- `manifest.webmanifest`: PWA metadata.
- `icon-192.png`, `icon-512.png`: PWA icons.
- `QR-LICENSE.txt`: QR library licence note.
- Markdown/TXT/JSON documentation: continuity instructions, specification, history, decisions, explanations, tests, and project state.

## Runtime model

The application is a client-side, offline-first web app supported by a Service Worker. Most UI and behavior live in `index.html`. Inline scripts execute in document order; later layers may extend or override earlier functions. Script order and syntax are therefore important.

## Measurements

V42/V44 documentation describes rooms, objects, dimensions, MERGE, MINUS/Clipping, photos, and transfer of quantities into New Estimate. V45 inherits the V44 code and does not change Measurements logic. Inspect actual functions and run tests before modifying this module.

## Persistence and compatibility

Do not change localStorage/IndexedDB keys or schemas without a backup and tested migration. V45 does not intentionally delete local user data. A Service Worker cache version change is separate from application data storage; still verify update behavior.

## Documentation

Human-readable project documentation is maintained in Romanian and English. The machine-readable JSON state retains stable keys for tooling compatibility.


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
