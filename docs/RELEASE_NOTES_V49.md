# DevizPRO V49 — Release Notes / Note de lansare

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

