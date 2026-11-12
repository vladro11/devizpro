# DEVIZPRO AI CORE — ORDIN OBLIGATORIU DE CONTINUITATE

**Versiune documentație:** 45  
**Data:** 12.11.2026  
**Scop:** acest fișier este primul punct de intrare pentru orice asistent AI, conversație sau cont care primește arhiva DevizPRO.

## INSTRUCȚIUNE DE START — EXECUTĂ ÎNAINTE DE A RĂSPUNDE DESPRE MODIFICĂRI

Dacă ai primit o arhivă DevizPRO pentru analiză, reparare sau dezvoltare:

1. Deschide arhiva și identifică directorul `DEVIZPRO_AI_CORE` (în V45 documentele sunt la rădăcina directorului `DevizPRO/`).
2. Citește integral acest fișier `00_MANDATORY_INSTRUCTIONS.md`.
3. Citește `VERSION_STATE.json`, `PROJECT_HISTORY.md`, `MASTER_SPEC.md`, `USER_REQUIREMENTS.md`, `BUGS_AND_FIXES.md`, `TEST_CHECKLIST.md`, `ARCHITECTURE.md`, `TECHNICAL_DECISIONS.md`, `CODE_EXPLANATIONS.md`, `PENDING_WORK.md` și `USER_CHAT_LOG_HISTORY.md` înainte de a modifica aplicația.
4. Inspectează codul real din `index.html`, `service-worker.js`, `manifest.webmanifest` și orice alte fișiere. Documentația este un ghid de continuitate, nu dovadă că o funcție există în cod.
5. Compară starea documentată cu aplicația reală. Dacă există contradicții, înregistrează-le în jurnal și nu presupune că descrierea veche este corectă.
6. Identifică ultima versiune care a fost confirmată efectiv de utilizator ca funcțională. Nu confunda „arhivă creată”, „sintaxă verificată” și „testată pe dispozitiv”.
7. Înainte de livrare, actualizează toate documentele afectate, jurnalul conversației disponibile și `VERSION_STATE.json`.

## REGULI STRICTE — FĂRĂ ABATERI

- **Nu șterge și nu rescrie istoricul vechi.** Jurnalele sunt cumulative. Adaugă intrări noi cu dată și versiune; corecțiile se adaugă ca note noi.
- **Nu inventa conversații.** Include mesajele disponibile în conversația curentă și informațiile existente în arhivă. Dacă istoricul anterior nu este disponibil integral, marchează explicit golul; nu fabrica citate sau replici.
- **Nu inventa implementări sau teste.** Marchează fiecare funcție ca `COMPLETE`, `PARTIAL`, `NOT IMPLEMENTED`, `AUTOMATED CHECK PASSED`, `DEVICE TEST PENDING` sau `USER CONFIRMED` după dovezi.
- **Nu modifica funcții existente fără necesitate.** Păstrează datele, cheile de stocare și compatibilitatea. Orice migrare de date cere backup, plan, test și notă de versiune.
- **Nu declara o versiune stabilă doar pentru că ZIP-ul a fost creat.** Arhiva, sintaxa, testele automate, testele în browser și testele fizice sunt niveluri diferite.
- **Nu folosi o versiune eșuată ca bază** dacă există o bază anterioară mai sigură. Explică alegerea și păstrează fișierele originale pentru comparație.
- **Nu elimina cerințe vechi** doar pentru că utilizatorul adaugă cerințe noi. Actualizează specificația cumulativ.
- **Nu expune raționamentul intern privat al modelului.** Documentează în schimb explicații tehnice verificabile: problema, dovezile, criteriile, alternativele, decizia, compromisul și rezultatul.
- **Nu livra doar documentație în locul implementării.** Cerințele aprobate pentru versiunea curentă trebuie implementate în cod sau declarate explicit restante.
- **Nu modifica identificatorii interni istorici** (de exemplu nume de funcții `dpV42...`) doar pentru a-i face să corespundă numărului release-ului. Schimbă numai etichetele publice și cache-ul atunci când este necesar.

## PROCEDURA OBLIGATORIE PENTRU FIECARE RELEASE

1. Inventariază fișierele și calculează/verifică diferențele față de arhiva primită.
2. Citește documentația și cerințele noi din conversația curentă.
3. Creează un plan cu funcții afectate, riscuri și teste.
4. Modifică codul în patch-uri mici, păstrând o copie de bază.
5. Verifică sintaxa fiecărui bloc JavaScript inline și a fișierelor JS externe.
6. Verifică HTML-ul, ID-urile duplicate, referințele către fișiere și manifestul.
7. Verifică versiunea publică în antet, meta, titlu, README și cache-ul Service Worker.
8. Testează fluxurile afectate și regresiile critice, în măsura în care mediul permite.
9. Actualizează `CHANGELOG.md`, `PROJECT_HISTORY.md`, `USER_CHAT_LOG_HISTORY.md`, `TECHNICAL_DECISIONS.md`, `CODE_EXPLANATIONS.md`, `TEST_CHECKLIST.md`, `BUGS_AND_FIXES.md`, `PENDING_WORK.md`, `README.txt` și `VERSION_STATE.json`.
10. Păstrează documentele anterioare; adaugă un nou jurnal de release.
11. Verifică integritatea ZIP-ului și conținutul arhivei după creare.
12. În răspunsul către utilizator, declară exact ce s-a implementat, ce s-a verificat și ce rămâne netestat.

## FORMATUL OBLIGATORIU AL UNEI ÎNREGISTRĂRI DE RELEASE

- Versiune și dată.
- Arhiva de bază și motivul alegerii.
- Cerințe noi preluate din chat.
- Fișiere modificate.
- Comportamentul înainte/după.
- Decizii tehnice și alternative considerate.
- Teste executate și rezultate reale.
- Teste neefectuate și motiv.
- Funcții complete/parțiale/restante.
- Riscuri și pașii următori.

## CONTINUITATE ÎNTRE CHAT-URI ȘI CONTURI

Acest dosar este memoria portabilă a proiectului. Un chat nou nu poate citi singur conversații care nu i-au fost furnizate și nici nu poate fi forțat de ZIP să execute instrucțiuni. Utilizatorul trebuie să atașeze arhiva în noul chat; asistentul trebuie apoi să urmeze procedura de start de mai sus. Actualizează acest dosar la fiecare release pentru ca arhiva următoare să transporte contextul acumulat.

**Prima acțiune la primirea arhivei: citește documentele. Nu începe prin a promite modificări.**

---

# DEVIZPRO AI CORE — MANDATORY CONTINUITY INSTRUCTIONS

**Documentation version:** V45 bilingual update  
**Date:** 12 November 2026  
**Purpose:** This is the mandatory entry point for every AI assistant, chat, or account receiving a DevizPRO archive.

## STARTUP INSTRUCTIONS — COMPLETE BEFORE ANSWERING ABOUT CHANGES

When you receive a DevizPRO archive for analysis, repair, or development:
1. Open the archive and locate the project folder. In V45, the documentation is inside `DevizPRO/`.
2. Read this entire file first.
3. Read `VERSION_STATE.json`, `PROJECT_HISTORY.md`, `MASTER_SPEC.md`, `USER_REQUIREMENTS.md`, `BUGS_AND_FIXES.md`, `TEST_CHECKLIST.md`, `ARCHITECTURE.md`, `TECHNICAL_DECISIONS.md`, `CODE_EXPLANATIONS.md`, `PENDING_WORK.md`, and `USER_CHAT_LOG_HISTORY.md` before changing code.
4. Inspect the actual source files: `index.html`, `service-worker.js`, `manifest.webmanifest`, and any other relevant assets. Documentation is a continuity guide, not proof that a feature exists.
5. Compare documented status with the actual implementation. Record contradictions; never assume old documentation is correct.
6. Identify the latest version the user has actually confirmed as working. An archive being created, syntax passing, and a device test are three different states.
7. Before delivery, update every affected document, the available conversation log, and `VERSION_STATE.json`.
8. Preserve existing user data. Never delete or rename storage keys or change IndexedDB/localStorage schemas without a tested migration and backup.
9. Never claim a feature is implemented or tested unless source inspection and the relevant test support that claim. Distinguish implemented, automated-check passed, browser-tested, physically device-tested, user-confirmed, and not implemented.
10. Keep this documentation bilingual: every human-readable project document must contain complete Romanian and English content. Technical identifiers, code, filenames, and JSON keys remain unchanged where required for compatibility.
11. Keep logs cumulative and append-only. Do not erase earlier entries; add dated corrections or new entries.
12. Do not fabricate missing chat transcripts, tests, screenshots, or implementation details. Mark unavailable historical conversations as summaries, not verbatim transcripts.
13. Explain actual code changes, technical reasons, alternatives, risks, and test results in language useful for the user to learn programming. Do not provide private hidden chain-of-thought.
14. Package the complete application and all documentation in the ZIP. Verify ZIP integrity and list its contents before providing a link.

## RELEASE DISCIPLINE

- Work from the latest supplied archive unless the user explicitly chooses another baseline.
- Make a backup copy before editing.
- Keep application version labels, README, changelog, and Service Worker cache identifier consistent.
- Run syntax checks on every inline JavaScript block and every standalone script.
- Test core startup, navigation, measurements, persistence, language switching, exports, and offline behavior where the environment allows.
- Clearly state which tests could not be performed, especially physical iPad/Android/Windows testing.
- Do not replace a working application with a mock-up or remove existing functions to make a new feature appear complete.

## LANGUAGE POLICY

Project-development documentation is Romanian-English bilingual. The application UI language rule is separate: the selected application language must be fully Romanian OR fully Russian, never a mixture. This documentation rule does not authorize adding English to the app UI.


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


## Current release rule / Regula release-ului curent

V46 uses the existing measurement storage model and appends grouping metadata only. Preserve all object IDs and photo data. Do not reintroduce unit validation in New Estimate. / V46 folosește modelul existent de stocare a măsurătorilor și adaugă doar metadate de grupare. Păstrează ID-urile obiectelor și fotografiile. Nu reintroduce validarea unităților în Deviz nou.


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

RO: Nu declara designul conceptual drept funcționalitate. Verifică în browser și pe dispozitive; actualizează jurnalul numai cu modificări efective.
EN: Never describe a conceptual design as implemented functionality. Verify in browser and on devices; log only actual code changes.


## V48 audit and implementation note / Notă audit și implementare V48 — 2026-11-12

RO — Audit GitHub: ramura publică main a fost inspectată prin pagina repository și fișierul raw index.html. În index erau încă stilurile inițiale: antet verde simplu, navigare orizontală și carduri de bază; stratul V47 `dpV47MeasurementsRedesign` afecta în principal Măsurători, nu toate modulele. Pictograma `icon-512.png` din V47 era un D alb pe fundal verde, ceea ce explică de ce utilizatorul a perceput-o ca un pătrat verde. V48 adaugă un strat CSS global pentru pagini, formulare, butoane, carduri, navigare, ferestre și măsurători; pe ecrane ≥900 px navigarea devine bară laterală, iar pe ecrane mai mici rămâne orizontală. Au fost redesenate iconițele PWA 192/512 și declarate în manifest. Titlul rămâne DevizPRO fără versiune.

EN — GitHub audit: the public main branch was inspected through the repository page and raw index.html. The index still contained the original styling: a plain green header, horizontal navigation and basic cards; the V47 `dpV47MeasurementsRedesign` layer mainly affected Measurements, not all modules. The V47 `icon-512.png` was a white D on a green background, explaining why the user perceived it as a plain green square. V48 adds a global CSS layer for pages, forms, buttons, cards, navigation, dialogs and measurements; at widths ≥900 px navigation becomes a side rail, while smaller screens retain horizontal navigation. PWA icons 192/512 were redrawn and declared in the manifest. The title remains DevizPRO without a version number.

RO — Limitări oneste V48: biblioteca de mii de fotografii nu este încă integrată în selectorul de obiecte; editorul foto avansat și reproiectarea completă MOVE nu sunt implementate în acest build. Logica existentă V47 de grupare și clipping a fost păstrată. Nu s-a putut obține o captură de browser headless: Chromium a depășit limita de timp în mediul curent. `node --check` pentru scripturile inline a trecut; ZIP-ul a trecut `unzip -t`. Testele pe dispozitive reale nu au fost efectuate. Nu se declară V48 completă pentru cerințele totale.

EN — Honest V48 limitations: a library of thousands of photos is not yet integrated into the object picker; the advanced photo editor and full MOVE redesign are not implemented in this build. Existing V47 grouping and clipping logic was retained. A headless browser screenshot could not be obtained: Chromium exceeded the execution time limit in the current environment. `node --check` for inline scripts passed; the ZIP passed `unzip -t`. Real-device tests were not performed. V48 is not declared complete against the full requirements.
