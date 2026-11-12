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


## V48 audit and implementation note / Notă audit și implementare V48 — 2026-11-12

RO — Audit GitHub: ramura publică main a fost inspectată prin pagina repository și fișierul raw index.html. În index erau încă stilurile inițiale: antet verde simplu, navigare orizontală și carduri de bază; stratul V47 `dpV47MeasurementsRedesign` afecta în principal Măsurători, nu toate modulele. Pictograma `icon-512.png` din V47 era un D alb pe fundal verde, ceea ce explică de ce utilizatorul a perceput-o ca un pătrat verde. V48 adaugă un strat CSS global pentru pagini, formulare, butoane, carduri, navigare, ferestre și măsurători; pe ecrane ≥900 px navigarea devine bară laterală, iar pe ecrane mai mici rămâne orizontală. Au fost redesenate iconițele PWA 192/512 și declarate în manifest. Titlul rămâne DevizPRO fără versiune.

EN — GitHub audit: the public main branch was inspected through the repository page and raw index.html. The index still contained the original styling: a plain green header, horizontal navigation and basic cards; the V47 `dpV47MeasurementsRedesign` layer mainly affected Measurements, not all modules. The V47 `icon-512.png` was a white D on a green background, explaining why the user perceived it as a plain green square. V48 adds a global CSS layer for pages, forms, buttons, cards, navigation, dialogs and measurements; at widths ≥900 px navigation becomes a side rail, while smaller screens retain horizontal navigation. PWA icons 192/512 were redrawn and declared in the manifest. The title remains DevizPRO without a version number.

RO — Limitări oneste V48: biblioteca de mii de fotografii nu este încă integrată în selectorul de obiecte; editorul foto avansat și reproiectarea completă MOVE nu sunt implementate în acest build. Logica existentă V47 de grupare și clipping a fost păstrată. Nu s-a putut obține o captură de browser headless: Chromium a depășit limita de timp în mediul curent. `node --check` pentru scripturile inline a trecut; ZIP-ul a trecut `unzip -t`. Testele pe dispozitive reale nu au fost efectuate. Nu se declară V48 completă pentru cerințele totale.

EN — Honest V48 limitations: a library of thousands of photos is not yet integrated into the object picker; the advanced photo editor and full MOVE redesign are not implemented in this build. Existing V47 grouping and clipping logic was retained. A headless browser screenshot could not be obtained: Chromium exceeded the execution time limit in the current environment. `node --check` for inline scripts passed; the ZIP passed `unzip -t`. Real-device tests were not performed. V48 is not declared complete against the full requirements.

---

## V49 — redesign global și repararea fluxurilor Măsurători (12.11.2026)

### Baza și corecția de audit
- Baza de lucru: arhiva V48 încărcată de utilizator. V49 este construită local; nu a fost publicată automat în GitHub.
- Auditul V48 a găsit o problemă de domeniu JavaScript: patch-ul de Măsurători rula într-un IIFE separat și apela funcții/stări (`calcElement`, `rooms`, `saveMeasures`, `v41ObjectHtml` etc.) care trăiau în closure-ul modulului V38. În plus, `showPage` și funcțiile de editare apelau randarea locală veche, nu randarea globală V47. De aceea codul modificat nu controla efectiv ecranul și unele operații puteau eșua.
- V49 introduce un bridge explicit către modulul Măsurători și un setter care conectează rendererul nou cu toate funcțiile vechi ce îl apelează. S-a eliminat și filtrul care ștergea din navigare toate butoanele în afară de patru.

### Modificări efective
- Redesign comun pentru toate paginile: antet, logo, navigare laterală pe desktop, navigare orizontală pe mobil/tabletă, carduri, câmpuri, butoane, tabele, ferestre, statistici și stări responsive.
- Pagina Principală are patru carduri de acces rapid și un flux recomandat; imaginile sunt locale.
- Logo separat în `Logo/`: SVG vectorial, PNG transparent, lockup orizontal PNG/SVG și icon 1024. Pictograme PWA 192/512 sunt regenerate. Numele public și pictograma nu conțin numărul versiunii.
- Navigarea are 14 destinații directe și respectă ordinea cerută: Principală, Deviz nou, Evidență, Grupe, Măsurători, module administrative, Catalog, Categorii, Setări.
- Cardurile de obiect din Măsurători au fost reconstruite: imagine reprezentativă offline, selector de tip, MOVE, dimensiuni compacte, total, Minus, ștergere și controale foto.
- Bibliotecă foto inițială: 10 fișiere WebP locale pentru perete, tencuială, fereastră, ușă, podea, cameră, țevi, acoperiș și casă. Ținta de 2.000–3.000 imagini nu este încă atinsă.
- Viewer foto pe tot ecranul: navigare între fotografiile obiectului, zoom și pan.
- Editor foto: pensulă, marker, culoare, grosime, text, font (Arial/Georgia/Verdana/Courier New), mărime text, undo/redo, resetare, descărcare pe dispozitiv și salvarea unei copii noi în obiect. Originalul nu este suprascris.
- MOVE folosește Pointer Events și prag de apăsare 520 ms; tragerea a fost verificată în Chromium cu reordonare efectivă. Gesturile pe iPad/Android și stylus trebuie confirmate pe dispozitive.
- Gruparea: selectare discretă, Confirmare/Refuz, dialog nume, validare strictă a unității în Măsurători, editare membri, redenumire și desfacere fără pierderea obiectelor.
- MINUS: selector pentru obiect compatibil, validare unitate și cantitate disponibilă, clipping nested în obiectul părinte. Obiectul copil nu este numărat separat în totalul principal.
- Transferul riglei în Deviz nou a fost testat cu o unitate personalizată (`unitate-personalizata`); cantitatea se transferă fără validarea unității calculată din Măsurători.
- Cheile și structurile de date existente nu au fost intenționat șterse sau redenumite. Grupurile reutilizează `room.merges` / `componentIds`, clipping păstrează `clippedTo`, fotografiile rămân în `photos`.
- Service Worker V49 cache-uiește CSS, logo și toate imaginile locale pentru acces offline după instalare/încărcare inițială.

### Teste Chromium automate efectuate
- 11/11 blocuri JavaScript inline: `node --check` PASS; Service Worker: `node --check` PASS.
- HTML parsată; 220 ID-uri statice; fără ID-uri duplicate (rezultat în checklist).
- 14 butoane de navigare, 16 secțiuni `.page`; toate cele 14 destinații accesate în simulare. Pagina „Mai multe” expune 12 carduri de acces.
- RO/RU: schimbarea limbii verificată pentru `lang` și etichetele de navigare.
- Măsurători: unități m.l., m² și m³ afișate conform numărului de dimensiuni.
- Salvare măsurătoare în storage shim, transfer riglă cu unitate personalizată, grupare create/edit/rename/delete, respingere unități diferite, MINUS valid/invalid și păstrarea obiectelor după desfacerea grupării.
- Viewer foto și editor: zoom, desen, undo/redo, text/font, copie salvată; originalul rămâne neschimbat.
- MOVE: tragere cu pointer a reordonat două obiecte în simulare.
- Responsive: 390 px, 412 px și 834 px — overflow orizontal 0 în simulare.
- Fără erori JavaScript de runtime și fără erori console în testul automat.

### Limite și verificări rămase
- Browserul a fost testat prin Chromium/Playwright cu HTML încărcat în context de simulare și `localStorage` înlocuit cu un shim în memorie; nu a fost un test de producție pe domeniul GitHub Pages. Service Worker nu a fost activat în acel test.
- Nu au fost efectuate teste fizice pe iPad, Android sau Windows și nu se pretinde compatibilitate confirmată pe dispozitive reale.
- Biblioteca foto este un starter de 10 imagini, nu 2.000–3.000.
- Redesignul global stabilește un sistem coerent pentru toate modulele; unele formulare și fluxuri vechi încă necesită reproiectare individuală și QA de business.
- Exporturile PDF/Excel, partajarea WhatsApp/Viber/Telegram/e-mail, import/export backup și sincronizarea între dispozitive trebuie testate separat pe dispozitive reale.
- V49 nu a fost împinsă în repository-ul GitHub al utilizatorului.

### Fișiere noi/actualizate
`assets/css/devizpro-shell.css`, `assets/objects/*.webp`, `Logo/*`, `design/V49_*`, `V49_BROWSER_TEST_RESULTS.json`, `TROUBLESHOOTING_AND_RECOVERY.md`.


## V49 — global redesign and Measurements workflow repair (12 Nov 2026)

### Baseline and audit correction
- Working baseline: the V48 archive uploaded by the user. V49 was built locally; it was not automatically published to GitHub.
- The V48 audit found a JavaScript scope problem: the Measurements patch ran in a separate IIFE and called functions/state (`calcElement`, `rooms`, `saveMeasures`, `v41ObjectHtml`, etc.) held inside the V38 module closure. In addition, `showPage` and edit functions still called the old local renderer instead of the patched global renderer. Therefore the modified code did not actually control the screen and some operations could fail.
- V49 adds an explicit bridge to the Measurements module and a renderer setter so legacy functions call the new renderer. It also removes the filter that deleted every navigation button except four.

### Actual source changes
- Shared visual system across all pages: header, branding, desktop side navigation, horizontal mobile/tablet navigation, cards, fields, buttons, tables, dialogs, metrics, and responsive states.
- Home dashboard now has four quick-action cards and a recommended workflow; imagery is local.
- Separate `Logo/` folder: vector SVG, transparent PNG, horizontal PNG/SVG lockup, and 1024 px icon. PWA icons 192/512 were regenerated. Public name and icon do not display a version number.
- Navigation exposes 14 direct destinations and follows the requested order: Home, New Estimate, Ledger, Groups, Measurements, admin modules, Work Catalog, Categories, Settings.
- Measurements object cards were rebuilt with offline representative photos, type selector, MOVE, compact dimensions, totals, MINUS, delete, and photo controls.
- Starter photo library: 10 local WebP assets for wall, plaster, window, door, floor, ceiling, room, pipes, roof, and house. The 2,000–3,000 image target is not yet reached.
- Full-screen photo viewer supports navigation between an object's photos, zoom, and pan.
- Photo editor supports brush, marker, color, thickness, text, font (Arial/Georgia/Verdana/Courier New), text size, undo/redo, reset, device download, and saving a new copy to the object. The original is not overwritten.
- MOVE uses Pointer Events and a 520 ms hold threshold; pointer dragging and actual reordering were verified in Chromium. iPad/Android and stylus gestures still require physical-device confirmation.
- Grouping: discreet selection, Confirm/Refuse, naming dialog, strict unit validation within Measurements, membership editing, rename, and ungrouping without losing objects.
- MINUS: compatible-object selector, unit and remaining-quantity validation, and clipping nested under the parent. The child object is not counted separately in the main total.
- Ruler transfer into New Estimate was tested with a custom work unit (`unitate-personalizata`); quantity transfers without enforcing the calculated Measurements unit.
- Existing data keys and structures were not intentionally deleted or renamed. Groups reuse `room.merges` / `componentIds`; clipping retains `clippedTo`; photos remain in `photos`.
- V49 Service Worker caches the CSS, logo, and all local images for offline use after initial installation/fetch.

### Automated Chromium tests performed
- 11/11 inline JavaScript blocks: `node --check` PASS; Service Worker: `node --check` PASS.
- HTML parsed; 220 static IDs; no duplicate IDs (see test checklist).
- 14 navigation buttons and 16 `.page` sections; all 14 destinations visited in simulation. The More page exposes 12 quick-access cards.
- RO/RU language switching checked for document `lang` and navigation labels.
- Measurements: m.l., m², and m³ output verified according to dimension count.
- Measurement save using a storage shim, custom-unit ruler transfer, grouping create/edit/rename/delete, mixed-unit rejection, valid/invalid MINUS, and object preservation after ungrouping.
- Photo viewer and editor: zoom, drawing, undo/redo, text/font, saved copy; original remained unchanged.
- MOVE: pointer drag reordered two objects in simulation.
- Responsive widths: 390 px, 412 px, and 834 px — zero horizontal overflow in simulation.
- No JavaScript runtime errors and no console errors in the automated test.

### Limitations and remaining verification
- Browser testing used Chromium/Playwright with HTML loaded in a simulation context and `localStorage` replaced by an in-memory shim; this was not a production-domain GitHub Pages test. The Service Worker was not activated in that test.
- No physical iPad, Android, or Windows tests were performed; real-device compatibility is not claimed as confirmed.
- The photo library is a 10-image starter set, not 2,000–3,000 images.
- The global redesign establishes a coherent system across all modules; some legacy forms and workflows still need individual redesign and business QA.
- PDF/Excel export, WhatsApp/Viber/Telegram/email sharing, backup import/export, and cross-device sync still require separate testing on real devices.
- V49 has not been pushed to the user's GitHub repository.

### New/updated files
`assets/css/devizpro-shell.css`, `assets/objects/*.webp`, `Logo/*`, `design/V49_*`, `V49_BROWSER_TEST_RESULTS.json`, `TROUBLESHOOTING_AND_RECOVERY.md`.

