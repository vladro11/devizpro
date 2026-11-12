# DevizPRO — Master Specification

Ultima actualizare: V45, 12.11.2026
Scop: document de referință obligatoriu pentru orice dezvoltare ulterioară. Citește acest fișier și toate documentele asociate înainte de modificarea codului.

## Reguli nenegociabile
- Aplicația trebuie să rămână offline-first și fără servicii plătite/API cu costuri recurente.
- Păstrează compatibilitatea cu datele existente. Nu schimba cheile localStorage/IndexedDB și nu migra structura fără migrare testată și backup.
- Nu înlocui aplicația cu un prototip și nu elimina funcții existente pentru a implementa una nouă.
- RO și RU trebuie să fie limbi UI complete și exclusive: nu amesteca limbile în aceeași interfață. Denumirile lucrărilor/categoriilor și exporturile convenite pot rămâne bilingve.
- Țintește iPhone/Android, iPad/tablete și Windows/laptop. Touch, stylus și mouse trebuie tratate distinct și testate.
- La fiecare versiune actualizează README, CHANGELOG, BUGS_AND_FIXES, TEST_CHECKLIST, ARCHITECTURE și USER_REQUIREMENTS.
- Nu declara o funcție „implementată” dacă nu există în cod și nu a trecut testul aferent. Separă: implementat, verificat automat, verificat pe dispozitiv, încă neimplementat.
- Înainte de livrare: verifică sintaxa tuturor scripturilor inline, inițializarea aplicației, Măsurători, salvarea, încărcarea datelor, limbi, export și service worker. Testează în browser automat dacă mediul permite.
- Versiunea trebuie actualizată consecvent în antet, README, numele arhivei și cache-ul Service Worker.

## Modul Măsurători — funcționalitate de bază
- Încăperi, redenumire și ștergere cu protejarea conținutului.
- Obiecte cu tip, pictogramă, dimensiuni și calcul automat.
- Dimensiuni uzuale: lungime, lățime, adâncime/înălțime în metri; interfață compactă.
- Rezultate reale/net și cantitate de lucru ușor de citit.
- MERGE grupează obiecte compatibile, dar componentele rămân editabile și pot fi selectate individual în rigla Devizului.
- MINUS/Clipping atașează obiectul dedus la obiectul principal; nu se listează separat în selectorul devizului. Restaurarea trebuie să readucă obiectul și fotografiile asociate la locul lor.
- Obiectele clipping nu trebuie să aibă acțiuni redundante sau pictograme înșelătoare.
- Asociere cu Deviz nou și selectorul de măsurători.
- Fotografii din cameră/galerie, miniaturi, persistente la salvare.

## Cerințe UI Măsurători — solicitate, încă de implementat/verificat
1. Cardurile obiectelor mult mai compacte, în special pe telefoane.
2. Pictograma principală în stânga sus; apăsarea ei schimbă pictograma obiectului.
3. MOVE în dreapta sus, pe același rând, cu indicator clar și fără activare accidentală.
4. Dimensiunile lungime/lățime/adâncime într-un rând compact, cu unitatea m; adaptare responsivă fără depășire.
5. Rezultatul real și cantitatea finală de lucru vizibile.
6. Camera și Galeria ca pictograme mici, în colțul inferior al cardului; miniaturile încep din stânga și curg la dreapta, apoi pe rândul următor.
7. Apăsarea miniaturii deschide vizualizator pe tot ecranul; navigare între fotografiile aceluiași obiect, zoom și pan.
8. Editor foto: instrumente de desen, culori, grosimi, pensule/markere, text cu fonturi și dimensiuni, undo/redo, curățare, salvare în galerie și „Salvează copia în obiect”. Originalul nu se suprascrie implicit.
9. MOVE trebuie să funcționeze cu Pointer Events și comportament adecvat touch/mouse/stylus. Nu selecta textul/pictograma în timpul tragerii. Pragul și durata apăsării trebuie validate pe iOS; nu presupune că 350 ms e universal optim.
10. MINUS: un singur buton real de scădere. Obiectul clipping are dialog clar pentru editarea dimensiunilor și acțiune de restaurare. Dialogul de editare trebuie disponibil doar pentru obiectele clipping, conform cerinței utilizatorului.
11. Grupare: buton lângă „+ Obiect” și „Șterge”; mod de selectare cu checkbox pentru obiectele independente; clipping children se tratează ca parte din obiectul părinte; bară de confirmare/anulare; dialog de nume; grup afișat cu pictogramă distinctă, nume și total; componentele și fotografiile lor rămân accesibile; grupul și componentele apar corect în selectorul Deviz nou.
12. Grupul trebuie să poată fi selectat ca o singură cantitate sau expandat pentru a selecta componentele individuale. Clipping children nu se dublează în listă/calcul.

## Cerințe foto — UX
- X în colțul dreapta sus; descărcare/salvare pe dispozitiv lângă X.
- Undo și redo alăturate în partea superioară stângă sau într-o bară de instrumente accesibilă.
- Instrumentele principale pot fi într-o bară verticală pe dreapta; pe ecrane mici trebuie să rămână accesibile fără a acoperi subiectul.
- Butonul principal de salvare a copiei în obiect trebuie să fie clar și vizibil.
- Gesturile de desen și navigare nu trebuie să intre în conflict.

## Alte cerințe globale cunoscute
- Export PDF/print și Excel/Numbers/CSV; partajare nativă când browserul permite.
- Backup manual și automat configurabil, export/import și transfer între dispozitive, fără server propriu.
- Păstrarea catalogului de lucrări și a datelor între versiuni.
- Interfață compactă, profesională, A4 bine formatată; fără link inutil în PDF.
- Semnătură opțională, implicit dezactivată.
- Nu introduce costuri sau integrare ChatGPT API plătită.

## Criteriu de acceptare
O versiune nu este gata doar pentru că fișierul ZIP există. Trebuie să treacă testele din TEST_CHECKLIST.md și să aibă versiunea/cache/README sincronizate. Orice test neefectuat se marchează ca neefectuat.


## Protocol documentație și continuitate AI — introdus în V45
- Orice asistent care primește arhiva trebuie să citească mai întâi `00_MANDATORY_INSTRUCTIONS.md`, apoi `VERSION_STATE.json` și toate documentele AI CORE indicate în README.
- Jurnalul conversațional (`USER_CHAT_LOG_HISTORY.md`) și istoricul tehnic sunt cumulative/append-only. Nu șterge intrări vechi.
- Include mesajele disponibile în chatul curent; nu pretinde acces la alte chat-uri și nu inventa transcrieri lipsă.
- Documentează deciziile tehnice, alternativele, codul, funcționarea comenzilor și testele, astfel încât utilizatorul să poată învăța. Nu publica raționamentul intern privat al modelului.
- Fiecare release actualizează README, changelog, istoric, starea JSON, jurnalul chatului, decizii, explicații, teste, buguri și backlog.
- Nu considera instrucțiunile din ZIP executate automat: asistentul trebuie să citească fișierele după ce arhiva este atașată în noul chat.
- V45 este release de documentare/versionare pe baza V44; nu reprezintă implementarea redesign-ului Măsurători.

---

# DevizPRO — Master Specification (English)

**Last updated:** V45 bilingual documentation update · 12 November 2026  
This is the mandatory reference for future development. Read it together with every AI CORE document before editing the source.

## Non-negotiable rules

- Keep the application offline-first and free of paid services or recurring API costs.
- Preserve existing user data. Do not change localStorage/IndexedDB keys or schemas without a tested migration and backup.
- Do not replace the application with a prototype or remove existing features to implement a new one.
- Romanian and Russian must be complete, exclusive UI languages. Never mix them in the same interface. Work names/categories and agreed export fields may remain bilingual.
- Target iPhone/Android, iPad/tablets, and Windows/laptop. Treat touch, stylus, and mouse input deliberately and test each where possible.
- Update README, CHANGELOG, BUGS_AND_FIXES, TEST_CHECKLIST, ARCHITECTURE, and USER_REQUIREMENTS at every release.
- Do not call a feature implemented unless it exists in the code and passes its relevant test. Separate implemented, automated-check passed, browser-tested, device-tested, user-confirmed, and not implemented.
- Before release, check inline JavaScript syntax, startup, Measurements, persistence, languages, exports, and Service Worker. Use browser testing when available.
- Keep version labels, README, archive name, and Service Worker cache identifier consistent.

## Measurements — required baseline

- Create, rename, and delete rooms without losing unrelated content.
- Create and edit objects with dimensions in metres.
- Transfer calculated quantities into New Estimate.
- Support MERGE and MINUS/Clipping without double-counting clipped child objects.
- Attach photos and preserve them with the correct object.
- Keep object cards highly compact, especially on phones.
- Place the object icon at upper left and MOVE at upper right on one row. MOVE must work reliably with touch, stylus, and mouse without accidental icon activation.
- Keep length, width, and depth inputs on one compact row where screen width permits.
- Photo thumbnails flow left-to-right and wrap naturally. The viewer supports full-screen display, zoom/pan, and swiping through photos of the same object.
- The photo editor supports drawing tools, colour, thickness, text, undo/redo, saving to the device, and saving an edited copy while preserving the original.
- Grouped objects remain selectable as a group or by component. Clipped children belong to their parent and are not separately counted.

## Documentation and learning

All human-readable project documents must be complete in Romanian and English. Explain actual code changes, architecture, technical trade-offs, tests, and limitations in a way that helps the user learn. Keep conversation and project logs cumulative. Never fabricate unavailable transcripts or private internal reasoning.


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

## V46 design reference / Referință de design V46
- RO: `design/DESIGN_REFERENCE_V46_CONCEPT.png` este reper vizual conceptual, nu dovadă de implementare. Păstrează stilul compact, cardurile clare și ierarhia verde/alb; fotografiile reale pentru tipurile de obiecte rămân cerință separată.
- EN: `design/DESIGN_REFERENCE_V46_CONCEPT.png` is a conceptual visual reference, not proof of implementation. Preserve its compact styling, clear cards, and green/white hierarchy; real photos for object types remain a separate requirement.


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
