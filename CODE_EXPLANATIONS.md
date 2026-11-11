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
