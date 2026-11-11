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
