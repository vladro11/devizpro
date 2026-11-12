# DevizPRO — Test Checklist

## Release V45 — verificări automate
- [x] Toate cele 10 blocuri JavaScript inline extrase și verificate cu `node --check` — PASS.
- [ ] HTML parse valid.
- [ ] Fără ID-uri duplicate.
- [ ] Toate căile din `service-worker.js` există.
- [x] Versiunea 45 în meta, titlu, antet, README și cache — PASS.
- [ ] ZIP poate fi listat și testat cu `unzip -t`.
- [x] Fișierele AI CORE sunt incluse în arhivă — PASS.

## Teste funcționale în browser
- [ ] Aplicația pornește fără erori console.
- [ ] Schimbare limbă RO/RU fără amestec.
- [ ] Navigare între module.
- [ ] Măsurători: creare încăpere, creare obiect, editare, salvare și reîncărcare.
- [ ] MERGE și MINUS/Clipping.
- [ ] Fotografii: adăugare, miniaturi și persistență.
- [ ] Selector Măsurători în Deviz nou și cantități.
- [ ] Export PDF/print și CSV/partajare.
- [ ] Backup și restaurare pe copie de date.

## Teste pe dispozitive reale
- [ ] iPad Safari/PWA.
- [ ] Telefon iOS.
- [ ] Telefon Android Chrome/PWA.
- [ ] Windows desktop (Chrome/Edge).
- [ ] Touch, stylus și mouse pentru MOVE.

- [x] Verificarea ID-urilor: nu au fost identificate ID-uri duplicate în DOM-ul static inițial; șase șabloane dinamice conțin ID-uri reutilizate intenționat în editorul de tipuri, care trebuie să fie montat o singură dată la un moment dat.
- [x] Căile din lista `ASSETS` a Service Worker există.

## V45 — raport curent

- Versiune publică actualizată în `index.html` la 45.
- Cache Service Worker actualizat la V45.
- Documentația AI CORE adăugată.
- Testele fizice pe iPad/telefon/Windows: **NEEFECTUATE de asistent**.
- Testele funcționale Măsurători: **NEEFECTUATE de asistent**.
- Teste automate executate: 10/10 scripturi inline valide; versiunea sincronizată; ID-uri statice inspectate; toate căile Service Worker existente; ZIP verificat după creare. Nu le interpreta ca testare pe dispozitiv.

---

# DevizPRO — Test Checklist (English)

## V45 — recorded automated checks

- [x] Ten extracted inline JavaScript blocks passed `node --check` in the prior V45 build.
- [ ] HTML parser validation.
- [ ] Duplicate-ID audit.
- [ ] Verify every Service Worker asset path exists.
- [x] Version 45 synchronized in meta tag, page title, header, README, and cache identifier in the prior V45 build.
- [x] AI CORE documentation included in the archive.
- [ ] Re-run ZIP integrity check for this bilingual documentation update.
- [ ] Confirm every human-readable document has Romanian and English content.
- [ ] Confirm the bilingual Word document opens and contains all sections.

## Functional browser tests — pending

- [ ] Application starts without console errors.
- [ ] Language switch between Romanian and Russian without mixed-language UI.
- [ ] Navigation between modules.
- [ ] Measurements: create room/object, edit, save, reload.
- [ ] MERGE and MINUS/Clipping.
- [ ] Add photos, render thumbnails, and verify persistence.
- [ ] Transfer Measurements quantities into New Estimate.
- [ ] Export PDF/print and Excel/Numbers.
- [ ] Offline reload and Service Worker update.

## Physical device tests — not performed by the assistant

- [ ] iPad/iOS.
- [ ] Android phone.
- [ ] Windows laptop/desktop.

Do not mark a test as passed unless it was actually run. The prior `node --check` results do not prove browser or device functionality.


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

## V46 — verificări executate / checks performed (12.11.2026)

### Română
- [x] 11 blocuri JavaScript inline extrase și validate cu `node --check` — PASS.
- [x] HTML analizat cu parserul BeautifulSoup; 217 ID-uri statice, fără duplicate — PASS.
- [x] Toate cele 6 resurse listate în Service Worker există — PASS.
- [x] Titlul browserului este `DevizPRO`; eticheta publică V45 eliminată; meta versiune 46 — PASS.
- [x] Test logic izolat în Node: grupare cu aceeași unitate, respingere unități diferite, ștergere grup fără pierderea obiectelor, transfer cantitate în deviz fără validare unitate — PASS.
- [ ] Test interactiv complet în browser: încercat cu Chromium/Playwright, dar navigarea a fost blocată de politica mediului (`ERR_BLOCKED_BY_ADMINISTRATOR`); NU este declarat PASS.
- [ ] Teste fizice iPad/iPhone/Android/Windows — NEEXECUTATE.
- [ ] Verificare vizuală a fotografiilor reale în catalog — RESTANTĂ; V46 păstrează pictogramele existente.

### English
- [x] 11 inline JavaScript blocks extracted and validated with `node --check` — PASS.
- [x] HTML parsed with BeautifulSoup; 217 static IDs and no duplicates — PASS.
- [x] All 6 Service Worker assets exist — PASS.
- [x] Browser title is `DevizPRO`; public V45 suffix removed; version metadata set to 46 — PASS.
- [x] Isolated Node logic test: same-unit grouping, mixed-unit rejection, deleting a group without deleting object records, and estimate quantity transfer without unit validation — PASS.
- [ ] Full interactive browser test: attempted with Chromium/Playwright, but navigation was blocked by the environment policy (`ERR_BLOCKED_BY_ADMINISTRATOR`); NOT marked PASS.
- [ ] Physical iPad/iPhone/Android/Windows tests — NOT RUN.
- [ ] Visual validation of a real-photo object catalogue — PENDING; V46 retains existing pictograms.


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
