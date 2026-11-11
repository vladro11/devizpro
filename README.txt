DEVIZPRO V37 — actualizare incrementală peste V36 (cu V35.1 păstrată ca referință)

BAZĂ ȘI SIGURANȚĂ
- V37 pornește de la V36, care include incremental modulele din V35.1 și modulul Măsurători. V35.1 originală rămâne arhivă de referință separată.
- Nu s-a reconstruit aplicația de la zero. Cheile localStorage existente sunt păstrate.
- Înainte de instalare: exportă un backup complet ZIP/JSON din aplicația curentă. Păstrează separat arhivele V35.1 și V36.
- Actualizarea nu șterge intenționat datele locale. Testează restaurarea backupului înainte de a folosi aplicația pentru date noi.

MODIFICĂRI V37
1. Navigarea principală are pictograme SVG redesenate, mai clare, și etichete vizibile: Principală, Deviz Nou, Măsurători, Mai multe. Pictograma Deviz Nou folosește document cu plus.
2. Meniul Mai multe folosește pictograme SVG coerente pentru categorii și module.
3. Denumirea modulului este simplificată la „Măsurători” / „Замеры”; nu se folosește termenul Revenue în etichetele vizibile.
4. Previzualizarea A4 din Deviz Nou se scalează automat ca foaia completă să încapă pe lățimea disponibilă, în portret și landscape. Conținutul lung rămâne derulabil vertical. Actualizarea previzualizării existente rămâne automată.
5. Modulul Măsurători permite scăderea individuală a golurilor de tip ușă, fereastră sau alt gol pentru elementele de tip perete. Suprafața brută, golurile scăzute, suprafața netă și cantitatea de lucru sunt afișate separat. Regula de rotunjire 0,40 este păstrată.
6. Releveele salvate au acțiuni „Creează deviz” și „Importă în deviz”. Cantitățile pozitive sunt transferate în poziții editabile, grupate pe încăperi/locații. Prețul este inițial 0 și trebuie completat în deviz. Sursa și valorile de măsurare sunt păstrate ca metadate în linia importată.
7. Interfața a primit reguli responsive suplimentare pentru telefoane, tablete și ecrane mari, inclusiv zone tactile și scalare A4.
8. Cache-ul service worker este incrementat pentru V37.

LIMITĂRI / VERIFICARE NECESARĂ
- Compatibilitatea este optimizată la nivel de layout web responsive, dar nu poate fi certificată pentru fiecare model de iPad, Android, Windows sau macOS fără testare fizică pe acele dispozitive și browsere.
- Previzualizarea arată foaia completă scalată; paginarea finală pe mai multe foi este realizată la imprimare/Salvare ca PDF de motorul browserului. Nu este încă un motor de paginare PDF cu foi A4 separate desenate individual în editor.
- Transferul din releveu creează poziții de lucrări generice, cu preț 0, pentru a nu inventa corespondențe sau prețuri din catalog. Verifică și completează denumirile/prețurile înainte de salvare.
- Scăderea golurilor este implementată pentru pereți. Deducerile duplicate trebuie evitate manual; fiecare gol adăugat este o intrare separată.
- Nu s-a pretins testare completă pe iPad fizic, Android sau desktop.

TESTARE TEHNICĂ
- Se verifică sintaxa tuturor blocurilor JavaScript cu Node.js.
- După instalare, verifică: deschiderea paginilor, navigarea, adăugarea și salvarea măsurătorilor, scăderea golurilor, transferul în deviz, actualizarea previzualizării, schimbarea orientării, exportul PDF și backup/restaurare.
