# DevizPRO — Bugs and Fixes

## Deschise / necesită confirmare
- [ ] Utilizatorul trebuie să confirme că V45 apare în antet după publicarea tuturor fișierelor.
- [ ] Test pe iPad și telefon: Măsurători se deschide și funcționează.
- [ ] Confirmă vizual dispariția semnului MINUS decorativ gri/roșu din selectorul MERGE.
- [ ] Verifică butonul funcțional `− Minus`.
- [ ] Cardurile compacte, MOVE nou, editorul foto avansat, dialogul clipping și gruparea nouă sunt încă neimplementate.

## Corecții documentate
### V45
- Sincronizate etichetele publice ale versiunii la 45 și cache-ul Service Worker.
- Adăugat sistemul de documentare și continuitate AI.

### V44
- Eliminat CSS-ul pseudo-element care afișa semnul MINUS decorativ duplicat pe selectorul MERGE, conform documentației V44.
- Acțiunea reală `− Minus` a fost păstrată.
- Utilizatorul nu a confirmat încă vizual rezultatul pe dispozitiv.

## Eșecuri istorice relevante
### V43
- Utilizatorul a raportat că versiunea instalată părea V42 și README indica V42.
- Utilizatorul a raportat că Măsurători nu funcționa.
- Verificarea arhivei V44 a identificat erori de sintaxă în două blocuri inline V43 analizate.
- Utilizatorul a raportat `Download failed`.

## Regula de raportare
Nu muta un bug la „închis” doar pentru că a fost editat codul. Închide-l numai după testul aferent; până atunci folosește „corecție aplicată — confirmare necesară”.

---

# DevizPRO — Bugs and Fixes (English)

## Open items / user confirmation required

- [ ] User confirms V45 appears in the application header after installation/update.
- [ ] Test on iPad and phone that Measurements opens and works.
- [ ] Visually confirm removal of the decorative grey/red MINUS sign in the MERGE selector.
- [ ] Verify the actual `− Minus` button still works.
- [ ] Compact cards, redesigned MOVE, advanced photo editor, clipping dialog, and new grouping flow remain unimplemented unless a later source change proves otherwise.

## Recorded fixes

### V45
- Public version labels synchronized to 45 and Service Worker cache identifier updated.
- Portable AI continuity documentation added.
- Bilingual documentation update adds English sections and a consolidated Word reference; application logic is unchanged.

### V44
- CSS pseudo-element that displayed the decorative duplicate MINUS sign in the MERGE selector was removed, according to V44 documentation.
- The real `− Minus` action was retained.
- The user has not yet visually confirmed this correction on a device.

## Reporting rule

A documented fix is not automatically a verified fix. Record the source change, automated test, browser test, device test, and user confirmation separately.


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


## V48 — 2026-11-12: global visual redesign / redesign vizual global

RO: V48 adaugă un strat global de design pentru toate paginile aplicației: paletă verde/alb, fundaluri, carduri, navigare, formulare, butoane, tabele, ferestre modale și adaptare responsive. Au fost refăcute pictogramele PWA 192/512 px cu simbol casă + DP și manifestul declară explicit pictogramele. Titlul public rămâne „DevizPRO”, fără număr de versiune. Cache-ul Service Worker este V48. Nu s-au șters chei localStorage sau IndexedDB. Logica existentă de grupare și clipping din V47 a fost păstrată, nu rescrisă în acest pas.

EN: V48 adds a global design layer across all application pages: green/white palette, backgrounds, cards, navigation, forms, buttons, tables, modals and responsive behavior. PWA icons (192/512 px) were redrawn with a house + DP mark and explicitly declared in the manifest. The public title remains “DevizPRO” without a version number. Service Worker cache is V48. No localStorage or IndexedDB keys were intentionally deleted. Existing V47 grouping and clipping logic was retained, not rewritten in this step.

RO: Verificări automate planificate/efectuate: sintaxa JS inline, integritatea ZIP, încărcarea paginii în Chromium headless și captură de ecran. Acestea nu echivalează cu testare completă pe iPad/Android sau cu verificarea fiecărui flux de business.

EN: Automated checks planned/performed: inline JavaScript syntax, ZIP integrity, page load in headless Chromium and screenshot capture. These do not equal full iPad/Android testing or verification of every business workflow.


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

