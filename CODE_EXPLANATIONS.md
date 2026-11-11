# DevizPRO — Code Explanations & Learning Notes

Acest document explică structura și conceptele din codul real. Se extinde la fiecare modificare. Explicațiile de mai jos descriu arhitectura identificată în V44/V45; nu reprezintă o analiză linie-cu-linie a întregului fișier de 500+ KB.

## 1. Fișiere principale

- `index.html` — documentul principal; conține structura UI, CSS și scripturile JavaScript inline.
- `service-worker.js` — gestionează cache-ul pentru funcționarea offline și actualizarea resurselor statice.
- `manifest.webmanifest` — numele aplicației instalabile, pictograma, modul de afișare și tema PWA.
- `icon-192.png`, `icon-512.png` — pictogramele aplicației.
- Fișierele Markdown/TXT — specificații, instrucțiuni și jurnalul proiectului.

## 2. Cum funcționează versiunea publică

În `index.html`:

- `<meta name="application-version" content="45">` oferă o valoare de versiune ușor de citit de instrumente și verificări.
- `<title>DevizPRO V45</title>` stabilește titlul paginii în browser.
- Elementul `#dpBuildVersion` afișează V45 în antetul aplicației.

Aceste trei valori trebuie sincronizate cu README și numele release-ului. Codul intern poate păstra nume istorice precum `dpV42Boot`; acestea identifică stratul tehnic din care provin funcțiile și nu trebuie redenumite doar pentru că release-ul a devenit V45.

## 3. Service Worker și cache

`service-worker.js` definește un nume unic de cache:

```js
const CACHE = 'devizpro-static-cache-v45-release-20261112';
```

- `install` deschide cache-ul și adaugă fișierele statice declarate în `ASSETS`.
- `skipWaiting()` permite noului Service Worker să treacă mai repede la activare.
- `activate` elimină cache-urile vechi care încep cu `devizpro-`, apoi preia controlul paginilor.
- `fetch` încearcă mai întâi cache-ul; dacă resursa nu există, o descarcă și o adaugă în cache.

**Atenție:** schimbarea numelui cache-ului nu trebuie confundată cu ștergerea datelor aplicației. Codul V45 nu adaugă o comandă de ștergere a `localStorage` sau IndexedDB.

## 4. Verificarea JavaScript inline

Deoarece scripturile sunt în interiorul `index.html`, o eroare de sintaxă într-un bloc poate împiedica inițializarea acelui script și poate rupe funcții dependente. Procedura recomandată:

1. Extrage fiecare bloc `<script>...</script>` într-un fișier temporar `.js`.
2. Rulează `node --check` pe fiecare fișier.
3. Înregistrează numărul blocurilor și rezultatul fiecăruia în `TEST_CHECKLIST.md`.
4. Sintaxa validă nu dovedește că funcția rulează corect; urmează testele funcționale în browser și pe dispozitive.

## 5. Evenimente pointer — concept pentru MOVE (cerință viitoare)

Pentru suport mouse/touch/stylus, `Pointer Events` unifică evenimente precum `pointerdown`, `pointermove`, `pointerup` și `pointercancel`. O implementare corectă trebuie să distingă între atingere, scroll, selectare și tragere; să folosească un prag de mișcare și/sau long-press; să gestioneze anularea și să fie testată pe Safari iOS. Nu presupune că un singur timp de long-press este optim pe toate dispozitivele.

**Status V45:** redesign-ul MOVE cerut nu este implementat în acest release.

## 6. Fotografii și editor — concepte pentru dezvoltare

- Miniaturile sunt previzualizări; originalul trebuie păstrat separat.
- Canvas poate fi folosit pentru desen și text peste fotografie.
- Undo/redo se poate construi dintr-un istoric de stări sau comenzi de editare.
- „Salvează copia în obiect” trebuie să exporte o imagine nouă și să o atașeze obiectului, fără a suprascrie originalul.
- Salvarea în galeria dispozitivului depinde de API-urile browserului și permisiuni; trebuie prevăzută o alternativă de descărcare.

**Status V45:** editorul avansat nu este implementat.

## 7. Cum se documentează o modificare de cod în viitor

Pentru fiecare patch, adaugă:

- Fișierul și funcția/selectoarele afectate.
- Fragmentul vechi și cel nou (doar porțiunea relevantă).
- Explicația fiecărei variabile și comenzi importante.
- De ce a fost aleasă soluția.
- Alternativele și dezavantajele lor.
- Efectul asupra datelor și compatibilității.
- Testul care demonstrează comportamentul.

---

# DevizPRO — Code Explanations & Learning Notes (English)

This document explains the identified source structure and programming concepts. It is extended after each code change. These notes describe the architecture inspected in V44/V45; they are not a line-by-line audit of the entire 500+ KB file.

## 1. Main files

- `index.html` — main document containing UI markup, CSS, and inline JavaScript.
- `service-worker.js` — controls offline caching and static-resource updates.
- `manifest.webmanifest` — installable PWA name, icons, display mode, and theme metadata.
- `icon-192.png`, `icon-512.png` — application icons.
- Markdown/TXT files — project specifications, instructions, and logs.

## 2. Public version identifiers

In `index.html`:

- `<meta name="application-version" content="45">` exposes a machine-readable application version.
- `<title>DevizPRO V45</title>` sets the browser tab/page title.
- The visible header label tells the user which build is open.

These values should agree with the README and archive name. The Service Worker cache name must also be unique for a release so the browser can fetch updated static files.

## 3. Service Worker cache

The Service Worker caches static resources to support offline use. Incrementing the cache identifier creates a new cache namespace. On activation, old project caches may be removed according to the cleanup code. This cache is not the same as localStorage or IndexedDB, where user-created business data may be stored.

## 4. Inline JavaScript and script order

Because much of the application is in one HTML file, scripts can depend on functions and variables declared earlier. Later scripts may wrap or override earlier functions. Extract and syntax-check every inline script separately, then test runtime behavior in a browser. A successful syntax check does not prove that the application initializes correctly.

## 5. Safe development method

1. Make a backup of the full archive.
2. Locate the actual function and data flow before editing.
3. Change the smallest possible code surface.
4. Preserve storage keys and existing records.
5. Run syntax checks and targeted functional tests.
6. Test touch, stylus, and mouse separately where relevant.
7. Update bilingual documentation and record limitations.

## 6. Learning note

A release label is metadata, not a feature implementation. Updating a title or cache identifier does not redesign a screen or repair its event handlers. Always compare source diffs and test behavior before describing a feature as complete.


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

## V46 — explicații cod / code notes

### Română
- `dpV46StartGrouping(ri)` activează modul de selecție pentru o încăpere. Lista de ID-uri selectate este păstrată temporar în `window.dpV46GroupMode`; nu copiază și nu mută obiectele.
- `dpV46ConfirmGrouping(ri)` recuperează obiectele după ID, exclude obiectele clipping și compară unitățile rezultate prin `calcElement`. Numai după validare cere numele și adaugă un obiect în `room.merges` cu `componentIds`.
- `renderMeasureRooms` (override V46) afișează grupurile ca elemente compacte colapsate. Obiectele membre sunt randate în interior numai la extindere. Înregistrările originale `room.elements` nu sunt mutate.
- `dpV46GroupMenu`, `dpV46RenameGroup`, `dpV46EditGroupObjects`, `dpV46SaveGroupObjects` și `dpV46DeleteGroup` gestionează numele și componența grupului. Ștergerea grupului șterge numai metadata din `room.merges`.
- `dpV41StartClip` este înlocuit cu un dialog de selecție explicit. Aplicarea apelează logica existentă `dpV41ApplyClip`, care verifică unitatea și limita disponibilă, apoi păstrează relația `clippedTo`.
- `dpV41ApplyRuler` este suprascris astfel încât să transfere cantitatea și eticheta sursei fără să compare unitatea liniei de deviz cu unitatea calculată în Măsurători.

### English
- `dpV46StartGrouping(ri)` enables selection mode for a room. Selected object IDs are held temporarily in `window.dpV46GroupMode`; objects are neither copied nor moved.
- `dpV46ConfirmGrouping(ri)` resolves objects by ID, excludes clipped children, and compares calculated units through `calcElement`. Only after validation does it request a name and append a `room.merges` record with `componentIds`.
- The V46 `renderMeasureRooms` override displays groups as compact collapsed entries. Member objects are rendered inside the expanded group only. Original `room.elements` records are not moved.
- `dpV46GroupMenu`, `dpV46RenameGroup`, `dpV46EditGroupObjects`, `dpV46SaveGroupObjects`, and `dpV46DeleteGroup` manage group name and membership. Deleting a group removes only metadata from `room.merges`.
- `dpV41StartClip` is replaced with an explicit selection dialog. Applying calls the existing `dpV41ApplyClip` logic, which validates unit and available quantity, then retains the `clippedTo` relationship.
- `dpV41ApplyRuler` is overridden to transfer quantity and source label without comparing the estimate-line unit with the unit calculated in Measurements.
