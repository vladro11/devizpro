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
