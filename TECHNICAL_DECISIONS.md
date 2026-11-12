# DevizPRO — Technical Decisions Journal

Jurnal cumulativ al deciziilor tehnice. Documentează motivele tehnice și alternativele, nu raționamentul intern privat al modelului.

## TD-045-001 — Folosirea V44 ca bază pentru V45

- **Context:** utilizatorul nu a instalat/testat încă V44; V43 a fost raportată ca eșuată, iar V44 a fost creată ca restabilizare din V42.
- **Decizie:** V45 se construiește direct din arhiva V44 furnizată. Nu se încearcă acum redesign-ul complet al Măsurători.
- **Motiv:** prioritatea este să existe o versiune clar identificată și o documentație portabilă, fără a introduce încă un strat UI netestat înainte ca utilizatorul să confirme că baza V44 funcționează.
- **Alternative:** (a) implementarea imediată a tuturor cerințelor Măsurători; (b) revenirea directă la V42. Prima variantă are risc de regresie înainte de testarea V44; a doua ar elimina corecțiile/documentația V44. S-a ales continuitatea V44.
- **Impact cod:** schimbate doar etichetele publice ale versiunii și identificatorul cache-ului Service Worker. Funcțiile interne istorice `dpV42...` nu au fost redenumite.
- **Risc/rămâne:** V44/V45 nu au fost testate fizic pe iPad, telefon sau Windows de către asistent.

## TD-045-002 — Documentație portabilă AI CORE

- **Context:** utilizatorul dorește ca un alt chat/cont să poată continua proiectul prin încărcarea arhivei.
- **Decizie:** instrucțiuni obligatorii, stare JSON, istoric conversațional, istoric de proiect, specificație, buguri, teste, decizii, explicații de cod și lucrări restante.
- **Motiv:** un set de fișiere text poate fi transferat odată cu ZIP-ul și inspectat de orice asistent care primește arhiva.
- **Limită:** ZIP-ul nu poate forța automat citirea și nu poate accesa alte conversații neatașate. Protocolul cere citirea explicită după încărcarea arhivei.

## TD-045-003 — Jurnal append-only și delimitarea transcriptului

- **Decizie:** jurnalele sunt cumulative; nu se șterg intrări vechi. Mesajele disponibile se păstrează cât mai aproape de original; informațiile recuperate ca rezumat sunt etichetate ca rezumat.
- **Motiv:** evitarea fabricării unui istoric complet când conversațiile vechi nu sunt disponibile în chatul curent.

## TD-045-004 — Explicații tehnice în locul raționamentului intern privat

- **Decizie:** se documentează problema, dovezile, alternativele, criteriile, decizia tehnică, codul și rezultatele testelor. Nu se publică raționamentul intern privat al modelului.
- **Motiv:** utilizatorul poate învăța programare din explicații verificabile, fără a pretinde acces la procese interne private.

---

# DevizPRO — Technical Decisions Journal (English)

Cumulative decision log. Document technical reasons, alternatives, consequences, and risks—not private hidden model reasoning.

## TD-045-001 — Use V44 as the V45 baseline

- **Context:** The user had not installed/tested V44 yet; V43 was reported as failing, and V44 was created as a restoration from V42.
- **Decision:** Build V45 directly from the V44 archive. Do not attempt the full Measurements redesign in this release.
- **Reason:** Establish a clearly identified baseline and portable documentation without introducing a large, untested UI layer before the user confirms V44 works.
- **Alternatives:** (a) implement all Measurements requests immediately; (b) return directly to V42. Option (a) risks regressions before V44 is tested; option (b) would discard V44 corrections/documentation. Continuity from V44 was selected.
- **Code impact:** Only public version labels and the Service Worker cache identifier changed. Historical internal function names such as `dpV42...` were not renamed.
- **Remaining risk:** The assistant did not physically test V44/V45 on iPad, phone, or Windows.

## TD-045-002 — Portable AI CORE documentation

- **Context:** The user wants another chat/account to continue development after receiving the archive.
- **Decision:** Include mandatory instructions, JSON state, conversation history, project history, specification, requirements, bug log, tests, architecture, technical decisions, code explanations, and backlog.
- **Reason:** Plain files travel with the ZIP and can be inspected by any assistant that receives the archive. They cannot force another chat to read them automatically; the user must upload the archive and the assistant must follow the startup instructions.

## TD-045-003 — Romanian-English documentation

- **Context:** The user wants to learn from the project documentation and understands English.
- **Decision:** Provide complete Romanian and English content in every human-readable project document and a consolidated bilingual Word file.
- **Reason:** Parallel language content improves portability and makes technical terminology accessible. Machine-readable JSON keys remain stable to avoid breaking tooling.
- **Application impact:** None; this is documentation-only.


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

## V46 — decizii tehnice / technical decisions

### Română
- Reutilizăm `room.merges` și `componentIds`, în loc să introducem un al doilea model de grupare. Astfel, grupările existente pot fi afișate în noul UI și nu este necesară migrare de date.
- Obiectele nu sunt mutate într-o structură nouă; grupul ține doar referințe la ID-urile lor. Această alegere păstrează fotografiile și dimensiunile la desfacere.
- Validarea unității este locală modulului Măsurători. Transferul în Deviz nou nu impune unitatea calculată, deoarece lucrările au unități definite manual de utilizator.
- Versiunea 46 rămâne în metadate/cache; eticheta de versiune nu este afișată în brand sau titlul aplicației.

### English
- Reuse `room.merges` and `componentIds` instead of introducing a second grouping model. Existing groups can therefore render in the new UI without a data migration.
- Objects are not moved into a new structure; a group stores references to their IDs only. This preserves photos and dimensions when a group is dissolved.
- Unit validation is scoped to Measurements. Transfer into New Estimate does not enforce the calculated unit because estimate work units are manually defined by the user.
- Version 46 remains in metadata/cache; the version suffix is not shown in the app brand or title.


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
