DEVIZPRO 47 PRO — RELEASE V47 / VERSIUNEA 47

DEVIZPRO V47 PRO — DOCUMENTAȚIE ȘI CONTINUITATE AI
Data build: 12.11.2026
Bază: DevizPRO V44 PRO (V44 restaurată din V42)

SCOPUL VERSIUNII V45
V45 sincronizează identificarea publică a versiunii și introduce un sistem portabil de documentare tehnică și continuitate pentru sesiunile ChatGPT viitoare. Utilizatorul nu instalase încă V44 la momentul solicitării V45; de aceea V45 păstrează codul funcțional moștenit din V44 și nu introduce acum un redesign amplu, netestat, al modulului Măsurători.

CE S-A SCHIMBAT ÎN V45
1. Versiunea publică este sincronizată la V45 în antet, titlul paginii și meta application-version.
2. Service Worker folosește un identificator unic de cache V45.
3. A fost adăugat protocolul obligatoriu `00_MANDATORY_INSTRUCTIONS.md` pentru orice asistent AI care primește arhiva.
4. A fost adăugat `USER_CHAT_LOG_HISTORY.md` cu mesajele disponibile din conversația curentă și contextul anterior marcat explicit ca rezumat, acolo unde nu există transcriere completă.
5. Au fost adăugate jurnale de istoric, decizii tehnice, explicații de cod, backlog, stare JSON și checklist.
6. Documentația precizează clar ce este moștenit, ce este implementat, ce nu este implementat și ce nu a fost testat fizic.

CE NU S-A SCHIMBAT ÎN V45
- Codul funcțional principal al aplicației este moștenit din V44.
- V45 nu pretinde că a implementat redesign-ul compact al cardurilor Măsurători, noul MOVE, editorul foto avansat, dialogul MINUS sau fluxul nou de grupare.
- Corecția semnului MINUS decorativ este moștenită din V44 și trebuie confirmată vizual de utilizator.

FUNCȚII MOȘTENITE DESCRISE ÎN V44
- Aplicație web offline/PWA.
- Interfață RO/RU.
- Catalog de lucrări, devize, evidență și grupe conform bazei V42.
- Modul Măsurători cu încăperi, obiecte, tipuri, dimensiuni, rezultate și fotografii.
- Integrare Măsurători → Deviz nou.
- MERGE și MINUS/Clipping în forma moștenită din V42.
- Export/partajare CSV și imprimare PDF prin browser, conform funcțiilor moștenite.

DOCUMENTAȚIA AI CORE
Citește obligatoriu `00_MANDATORY_INSTRUCTIONS.md` înainte de orice modificare. Apoi citește:
- `VERSION_STATE.json`
- `PROJECT_HISTORY.md`
- `USER_CHAT_LOG_HISTORY.md`
- `MASTER_SPEC.md`
- `USER_REQUIREMENTS.md`
- `BUGS_AND_FIXES.md`
- `TEST_CHECKLIST.md`
- `ARCHITECTURE.md`
- `TECHNICAL_DECISIONS.md`
- `CODE_EXPLANATIONS.md`
- `PENDING_WORK.md`

REGULI DE CONTINUITATE
- Jurnalele sunt cumulative și append-only; nu șterge intrările vechi.
- Nu inventa mesaje din chat-uri inaccesibile. Adaugă mesajele disponibile în conversația curentă și marchează limitele istoricului.
- Nu confunda o funcție descrisă cu una implementată.
- Nu confunda verificarea sintaxei cu testarea funcțională sau testarea pe dispozitiv.
- ZIP-ul nu poate forța automat un chat nou să citească documentele. Utilizatorul trebuie să atașeze arhiva; asistentul trebuie să citească instrucțiunile și să urmeze protocolul.
- Nu publica raționamentul intern privat al modelului; documentează deciziile tehnice, alternativele, codul și testele într-o formă explicativă.

INSTALARE / ACTUALIZARE
1. Fă backup al datelor aplicației înainte de înlocuirea fișierelor.
2. Publică toate fișierele din directorul `DevizPRO`, nu doar `index.html`.
3. Deschide aplicația și verifică dacă antetul afișează V45.
4. Dacă apare versiunea veche, închide complet aplicația instalată și redeschide-o după publicarea tuturor fișierelor; nu șterge localStorage/IndexedDB ca primă soluție.
5. Testează Măsurători înainte de a considera versiunea stabilă.

STATUS TESTARE V45
- Versiune și documentație sincronizate în arhivă.
- Testarea sintaxei JavaScript și integrității ZIP trebuie consultată în `TEST_CHECKLIST.md` și în raportul de livrare.
- Nu există test fizic efectuat de asistent pe iPad, Android sau Windows.
- V45 nu este declarată stabilă până la confirmarea utilizatorului.

---

DEVIZPRO V45 PRO — BILINGUAL DOCUMENTATION UPDATE
Date: 12 November 2026
Base: DevizPRO V45 PRO (application code inherited from V44, restored from V42)

PURPOSE OF THIS UPDATE
All human-readable project continuity documents are now intended to be available in Romanian and English. A consolidated Word document is included for convenient reading, sharing, and learning. The application code and data model are not changed by this documentation-only update.

WHAT IS INCLUDED
- The complete DevizPRO application and its existing assets.
- Romanian-English versions of the AI continuity instructions, requirements, specification, project history, chat-history record, architecture, technical decisions, code explanations, bug log, tests, backlog, and changelog.
- `DevizPRO_AI_CORE_BILINGUAL.docx`, a Word reference containing the documentation in both languages.
- `VERSION_STATE.json`, retained as machine-readable project state; its stable keys are not translated to avoid breaking tools.

APPLICATION CHANGE STATUS
This is a documentation update to V45, not a new functional application release. The app's public version remains V45. No new compact Measurements cards, redesigned MOVE interaction, advanced photo editor, clipping dialog, or object-grouping workflow is claimed as implemented here.

TEST STATUS
The ZIP is checked for archive integrity and documentation presence. This update does not constitute a physical iPad, Android, or Windows test. Refer to `TEST_CHECKLIST.md` and `VERSION_STATE.json` for exact status.

IMPORTANT
Read `00_MANDATORY_INSTRUCTIONS.md` first in every future AI session. Then read all AI CORE documents and inspect the actual code before making changes. Never assume documentation proves a feature exists.


ROMÂNĂ / ENGLISH
Toate documentele text AI CORE au secțiuni complete în română și engleză. Fișierul Word consolidat este `DevizPRO_AI_CORE_BILINGUAL.docx`. `VERSION_STATE.json` păstrează cheile tehnice stabile și include câmpuri descriptive bilingve.
All AI CORE text documents contain Romanian and English sections. The consolidated Word file is `DevizPRO_AI_CORE_BILINGUAL.docx`. `VERSION_STATE.json` keeps stable technical keys and includes bilingual descriptive fields.


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


V46 RELEASE STATUS / STAREA RELEASE-ULUI V46

ROMÂNĂ
V46 include noul flux de grupare în Măsurători, carduri compacte, dialogul MINUS revizuit și eliminarea validării unităților la transferul cantității în Deviz nou. Numărul versiunii nu apare în brand sau titlul browserului. Documentația și fișierul Word au fost actualizate bilingv.
Verificări: 11/11 scripturi inline valide; 217 ID-uri statice fără duplicate; resursele Service Worker prezente; teste logice izolate PASS; integritatea ZIP va fi verificată după împachetare. Testul browser complet a fost blocat de politica mediului, iar testele pe iPad/Android/Windows trebuie făcute de utilizator. Biblioteca de fotografii reale și editorul foto avansat sunt încă restante.

ENGLISH
V46 includes the new Measurements grouping workflow, compact cards, revised MINUS dialog, and removal of unit validation when transferring quantities into New Estimate. The version number is not shown in the app brand or browser title. Core documentation and the Word file have been updated bilingually.
Checks: 11/11 inline scripts valid; 217 static IDs with no duplicates; Service Worker assets present; isolated logic tests PASS; ZIP integrity will be checked after packaging. Full browser testing was blocked by the environment policy, and iPad/Android/Windows tests remain for the user. The real-photo library and advanced photo editor remain pending.

DESIGN REFERENCE / REFERINȚĂ VIZUALĂ
ROMÂNĂ: `design/DESIGN_REFERENCE_V46_CONCEPT.png` este macheta conceptuală preferată pentru direcția estetică a modulului Măsurători; nu este o captură a aplicației implementate.
ENGLISH: `design/DESIGN_REFERENCE_V46_CONCEPT.png` is the preferred conceptual mock-up for the Measurements visual direction; it is not a screenshot of the implemented application.


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


V47 / ROMÂNĂ: Redesign vizual global și corecții pentru grupare și MINUS. Vezi CHANGELOG.md și VERSION_STATE.json pentru diferența dintre funcțiile implementate, cele nefinalizate și testele efectuate.
V47 / ENGLISH: Global visual redesign and grouping/MINUS fixes. See CHANGELOG.md and VERSION_STATE.json for the distinction between implemented, unfinished, and tested features.
