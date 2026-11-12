# DevizPRO — User Requirements Log

Acest jurnal este cumulativ. Cerințele noi se adaugă la final cu data și versiunea; cerințele vechi nu se elimină. Pentru detalii tehnice vezi `MASTER_SPEC.md` și `PENDING_WORK.md`.

## Cerințe generale istorice recuperate

- Aplicație offline pentru iPad, Android și laptop Windows; preferință pentru soluții gratuite, fără API plătit.
- Interfață exclusiv în română sau exclusiv în rusă, după limba selectată; fără amestec de limbi.
- Catalog de lucrări editabil, coduri și prețuri păstrate între versiuni.
- Devize, export PDF/print și Excel/Numbers, partajare prin aplicațiile disponibile.
- Grupe/evidență, backup/import/export și transfer între dispozitive.
- Interfață compactă, profesională, A4, semnătură opțională.

## 11–12.11.2026 — Măsurători

- Cardurile obiectelor trebuie să fie mult mai compacte, în special pe telefon.
- Pictograma obiectului în stânga sus și MOVE în dreapta sus, pe același rând.
- MOVE trebuie să aibă activare intuitivă și să nu selecteze accidental pictograma; funcționare pe touch, stylus și mouse.
- Dimensiuni doar lungime, lățime, adâncime, în metri, într-un rând compact.
- Camera și galeria minimaliste; miniaturi de la stânga la dreapta, cu trecere automată pe rând nou.
- Deschiderea fotografiei pe tot ecranul, zoom, navigare între fotografiile obiectului.
- Editor foto cu desen, contur, text, culori, grosimi, pensule, fonturi, undo/redo, salvare pe dispozitiv și copie nouă în obiect; originalul se păstrează.
- MINUS/Clipping: editare clară a dimensiunilor, salvare/anulare, restaurare, fotografii păstrate și asociate corect.
- Grupare cu checkbox, confirmare/anulare, nume, total, componente expandabile/editabile și integrare cu Deviz nou.
- Obiectele clipping sunt componente ale părintelui și nu se numără separat.
- Eliminarea semnului MINUS gri/roșu decorativ și nefuncțional; păstrarea butonului real `− Minus`.

## 12.11.2026 — Documentație și continuitate AI (V45)

- Fiecare ZIP trebuie să includă instrucțiuni explicite pentru orice asistent AI viitor.
- Asistentul trebuie să citească mai întâi instrucțiunile și documentația înainte de a modifica aplicația.
- Jurnalul conversațiilor trebuie actualizat cronologic și cumulativ, incluzând mesajele utilizatorului și răspunsurile relevante disponibile până la momentul release-ului.
- Istoricul nu se rescrie; se adaugă intrări noi. Nu se inventează mesaje din chat-uri inaccesibile.
- Documentația trebuie să explice modificările, deciziile tehnice, motivele, alternativele, codul și funcționarea comenzilor pentru ca utilizatorul să poată învăța programare.
- Se poate documenta justificarea tehnică verificabilă; nu se solicită publicarea raționamentului intern privat al modelului.
- Documentația trebuie să fie transferabilă între chat-uri/conturi prin arhivă. Utilizatorul înțelege că arhiva trebuie atașată și citită în chatul nou; nu există citire automată garantată doar prin ZIP.
- V44 nu fusese încă instalată/testată de utilizator la momentul cererii V45.

---

# DevizPRO — User Requirements Log (English)

This is a cumulative record. Add new requirements at the end with date and version; do not remove earlier requirements. See `MASTER_SPEC.md` and `PENDING_WORK.md` for details.

## General historical requirements

- Free offline application for iPad, Android, and Windows laptop; no paid API.
- App UI must be entirely Romanian or entirely Russian according to the selected language; no mixed UI.
- Editable work catalogue with persistent codes and prices.
- Estimates, PDF/print and Excel/Numbers export, and sharing through available apps.
- Groups/accounting, backup/import/export, and device-to-device transfer.
- Compact professional interface and A4 output; optional signature block.

## Measurements requirements — 11–12 November 2026

- Object cards must be much more compact, especially on phones.
- Object icon at upper left and MOVE at upper right on the same row.
- MOVE activation must be intuitive and must not accidentally select the icon; support touch, stylus, and mouse.
- Dimension fields (length, width, depth) should fit in one compact row.
- Camera/gallery controls should be small and placed at the lower right; thumbnails align left-to-right and wrap to new rows.
- Full-screen photo viewer with zoom, pan, and swipe between photos belonging to the same object.
- Photo editor with brush/pen/marker, colour and thickness, text with font and size, undo/redo, device save, and edited-copy save inside the object. Keep the original unchanged.
- Remove the inactive decorative duplicate MINUS icon; retain one working `− Minus` action.
- For clipping, the child remains part of the parent and must not appear as a separate selectable/countable quote item. Provide a clear edit-dimensions popup with Save/Cancel and restore the object and photos to the original owner.
- Add object grouping near the add/delete controls. Support selection, group naming, group totals, expandable/editable components, group photos, and selection of either the group or individual components.
- Every ZIP release must contain cumulative bilingual AI documentation, an available chat log, project history, requirements, bugs, tests, architecture, technical decisions, code explanations, and pending work.
- Include a consolidated bilingual Word document. The user wants Romanian and English, including in Word files.
- Do not claim unimplemented work is complete. Clearly state what was changed and what tests were actually run.


## 12.11.2026 — Actualizare bilingvă solicitată de utilizator (RO)

- Toate documentele pentru memoria, continuitatea și dezvoltarea DevizPRO trebuie să fie disponibile integral în română și engleză.
- Cerința se aplică și fișierului Word consolidat; utilizatorul dorește să poată citi și învăța din ambele limbi.
- La fiecare versiune viitoare, documentele noi și actualizările documentelor existente trebuie menținute bilingv.

## 12 November 2026 — User-requested bilingual update (EN)

- All documents supporting DevizPRO memory, continuity, and development must be available in full in both Romanian and English.
- This requirement also applies to the consolidated Word file; the user wants to read and learn from both languages.
- Every future release must keep new documents and updates to existing documents bilingual.


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
