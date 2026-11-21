DEVIZPRO V2 E2 — UPGRADE
Data build: 21.11.2026
Bază: DevizPRO V2 E1 furnizată de utilizator.

CE ESTE NOU ÎN E2
- Card Măsurători compact: pictogramă stânga, selector tip pe același rând, buton + în dreapta.
- Dimensiuni compacte și adaptare pentru ecrane mici.
- Camera și Galeria au butoane icon-only.
- Dialog Tip nou: Adaugă numai în măsurătoarea curentă sau Salvează în setări pentru catalogul general și încăperea curentă.
- Butoane sus/jos pentru mutarea încăperilor și obiectelor. Drag-and-drop moștenit rămâne activ.
- Versiunea nu este afișată în interfață; este prezentă doar în titlul filei și identificatorii tehnici.

CE A FOST PĂSTRAT
- Cheile și structurile de date existente.
- MERGE, MINUS/Clipping, fotografii și transfer Măsurători → Deviz nou.
- Catalog, devize, clienți, finanțe, documente, offline/PWA și limbile RO/RU.

ÎNCĂ NELIVRAT ÎN E2
- Pictograme complet personalizate și secțiunea recente.
- Comutator de vizibilitate cu ochi.
- Galerie de încăpere cu agregarea fotografiilor obiectelor.
- Înlocuirea completă a drag-and-drop cu un sistem comun pentru toate modulele.
- Navigare complet adaptivă telefon/tabletă/desktop și ascundere în subpagini.
- Home dashboard extins și Setări reorganizate.

TESTARE
- Sintaxă JavaScript inline: 11/11 PASS.
- Parsare HTML: PASS; ID-uri statice duplicate: 0.
- Căi Service Worker: PASS.
- Integritate ZIP: verificată la împachetare.
- Test browser interactiv și dispozitive fizice: PENDING.
- Nu considera E2 stabilă până la testarea pe iPad/telefon/desktop.

DEVIZPRO V2 E1 — PRIMA EDIȚIE A SERIEI V2
Data build: 21.11.2026
Bază tehnică: arhiva V45 PRO, păstrată ca motor funcțional și structură de date

NUMEROTARE NOUĂ
- Seria nouă începe cu V2 E1.
- Următoarele actualizări vor fi V2 E2, V2 E3, V2 E4 etc.
- Se schimbă numai numărul E la fiecare ediție; V2 rămâne seria principală.
- Versiunea nu este afișată în interfața aplicației. Ea apare numai în titlul filei browserului și în identificarea tehnică a buildului.
- Numele instalat/PWA rămâne simplu: DevizPRO.

CE CONȚINE EDIȚIA E1
1. Începe noua serie de versiuni V2 E.
2. Elimină eticheta V45 din antetul aplicației.
3. Actualizează titlul filei browserului, metadatele și cache-ul Service Worker la V2 E1.
4. Păstrează codul funcțional, structura de date, cheile locale și funcțiile moștenite din V45.
5. Înregistrează cerințele aprobate pentru refacerea Măsurătorilor, galeriilor foto, MINUS, navigării, Home și Setărilor ca plan de implementare incrementală.

LIMITĂ IMPORTANTĂ E1
E1 este ediția de pornire a noii numerotări și fundația pentru modificările următoare. Redesign-ul complet descris în conversație nu este încă implementat în această arhivă. Nu se declară implementate funcții care sunt doar proiectate.

DEVIZPRO V45 PRO — DOCUMENTAȚIE ȘI CONTINUITATE AI
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
