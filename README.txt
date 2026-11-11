DEVIZPRO V42 — CORECȚIE DE INTEGRARE PE BAZA V41 / V40

BAZĂ ȘI PĂSTRAREA DATELOR
- V42 pornește din arhiva V40 primită, păstrând stratul de funcții adăugat în V41; aplicația nu a fost reconstruită de la zero.
- Cheile de stocare locală existente sunt păstrate. Nu există o comandă de ștergere a datelor locale.
- Service Worker folosește un cache nou V42. La activare, cache-urile vechi DevizPRO sunt înlocuite; datele din localStorage/IndexedDB nu sunt șterse de această operație.
- Păstrează separat arhiva V40 și exportă un backup local din fiecare dispozitiv înainte de publicare.

MODIFICĂRI FUNCȚIONALE PĂSTRATE DIN V41
1. În Măsurători, transferul direct în deviz a fost înlocuit cu „Deviz nou cu această măsurătoare”.
2. În Deviz nou există selectorul de măsurătoare, implicit „Nici-o măsurătoare”, cu cele mai recente primele. Asocierea se salvează în deviz, dar nu este inclusă în PDF/export.
3. Lângă cantitatea fiecărei lucrări există rigla. Lista este organizată pe încăperi: grupurile MERGE apar primele, apoi componentele individuale și obiectele independente. Obiectele aflate în Clipping nu apar separat.
4. MERGE permite unirea a cel puțin două obiecte compatibile ca unitate. Grupul afișează denumirea, numărul componentelor și totalul; componentele rămân vizibile, editabile și selectabile separat în rigla Devizului.
5. MINUS / Clipping atașează obiectul dedus la obiectul principal. Obiectul dedus nu este oferit separat în rigla Devizului; cât timp este în Clipping, are numai modificarea dimensiunilor prin creion și revenirea din MINUS. La mutare, obiectul dedus rămâne atașat de obiectul principal.
6. Deducerea verifică unitatea calculată după numărul de dimensiuni: o dimensiune = m.l.; două = m²; trei sau mai multe = m³. Unitățile incompatibile sunt respinse cu mesaj localizat RO/RU. Deducerile nu pot depăși suprafața rămasă a obiectului principal.
7. Pentru încăperi, obiecte și grupuri de măsurători există mutare prin apăsare lungă și tragere; componentele Clipping nu se pot muta independent.
8. Pentru încăperi și obiecte/tipuri există acțiuni Cameră și Galerie; fotografiile sunt redimensionate/comprimate și stocate în înregistrarea măsurătorii.
9. Pictograma Obiect/Tip deschide direct selectorul de pictograme, iar butonul separat de pictogramă este eliminat din interfața măsurătorilor.
10. Evidența pe zone include redenumire, sortare alfabetică/după numărul de devize, ștergere cu transfer obligatoriu al conținutului și transfer multiplu de devize.
11. Controalele checkbox sunt compacte; Reminderele sunt afișate ca opțiuni compacte.
12. Drag & Drop prin apăsare lungă este disponibil pentru rândurile de lucrări, grupele/subgrupele și devizele din grupe, precum și pentru zone.
13. Textele și mesajele noi sunt localizate în română/rusă prin mecanismul de limbă existent. A fost corectată și referința lipsă la elementul `subtitle` care bloca schimbarea limbii în V40.

VERIFICĂRI EFECTUATE ÎN MEDIUL DE CONSTRUIRE
- Sintaxa tuturor celor 10 blocuri JavaScript inline și a service-worker.js a fost verificată cu Node.js; fără erori de sintaxă.
- Structura HTML a fost parsată; nu au fost găsite ID-uri duplicate.
- Test UI Chromium/Playwright cu stocare temporară: aplicația și scriptul principal se inițializează fără erori JavaScript; funcțiile de catalog, căutare, calcul și salvare sunt disponibile; versiunea afișată este V42.
- Măsurători: creare încăpere și obiecte, pictogramă selectabilă, butoane cameră/galerie, mânere de tragere; MERGE pentru 4 pereți a afișat 40,00 m²; după MINUS, grupul a păstrat eticheta „Pereți (4)” și a recalculat totalul net la 38,00 m²; rigla a afișat grupul și cele 3 componente independente, fără copilul aflat în MINUS.
- Importul unei imagini PNG de test a generat miniatură. Selectorul de măsurători și rigla au fost deschise în fluxul Deviz nou.
- Grupe și zone: mânerele de reordonare au fost randate; butonul rapid de partajare a apărut în Evidență și în rândul devizului din grup.
- Export: fișierul CSV a fost descărcat cu antet bilingv și deschis în test; un adaptor de test pentru Web Share a confirmat transmiterea unui fișier CSV în obiectul de partajare. Meniul real de partajare al iOS/Android nu a fost testat pe dispozitiv fizic.
- Schimbarea limbii RO/RU și randarea etichetelor de zone în rusă au fost verificate fără erori.
- Testele cu stocare temporară nu certifică limitele reale de localStorage/IndexedDB ale fiecărui browser și nu înlocuiesc testarea cu datele reale ale utilizatorului.
LIMITĂRI / TESTARE PE DISPOZITIVE
- Nu a fost posibilă testarea fizică pe Android, iPhone, iPad sau Windows în această sesiune.
- Camera, galeria, permisiunile browserului, persistența fotografiilor, stocarea locală și gesturile de tragere trebuie probate pe dispozitive reale. Comportamentul camerei depinde de browser și de permisiunile acordate.
- Prin urmare, arhiva este o versiune V42 de testare, nu o certificare că totul este „perfect” pe toate dispozitivele.

INSTALARE
1. Exportă backup din V40 pe fiecare dispozitiv și păstrează ZIP-ul V40.
2. Înlocuiește fișierele din repository cu conținutul arhivei V42; nu șterge datele site-ului/browserului.
3. Deschide aplicația cu internet o singură dată pentru a descărca noul cache V42, apoi verifică funcționarea offline.
4. Dacă dispozitivul păstrează temporar interfața veche, închide complet aplicația/browserul și redeschide site-ul; nu șterge stocarea locală.
5. Testează întâi pe o copie a datelor. Păstrează backup-ul V40 până când confirmi că V42 funcționează corect pe fiecare dispozitiv.


CORECȚII V42
- A fost reparată o eroare de structură JavaScript moștenită din V40 în funcția de imprimare a devizelor salvate: șablonul HTML nu era închis, iar scriptul principal nu se putea inițializa. Funcțiile de bază (catalog, salvare deviz, căutare, calcul și evidență) sunt acum încărcate corect.
- Corecția de integrare: stratul V41 era încărcat după apelul inițial init() din V40. V42 execută o inițializare explicită după încărcarea tuturor extensiilor, astfel încât randerele V41 pentru Măsurători, zone, grupuri și Deviz nou să fie aplicate imediat, nu doar după prima interacțiune.
- Este afișată versiunea V42 lângă marca DevizPRO, pentru confirmarea vizuală a versiunii încărcate.
- Cache-ul Service Worker a fost incrementat la V42 pentru a forța descărcarea fișierelor noi fără ștergerea localStorage/IndexedDB.
- Au fost completate câteva etichete și placeholder-e noi pentru limba rusă.
- Verificarea Chromium confirmă că scriptul principal, inițializarea V42, salvarea unui deviz și partajarea CSV rulează fără erori JavaScript în testul cu stocare temporară.

NOTĂ IMPORTANTĂ
V42 este o versiune de testare corectată. Verificarea automată nu înlocuiește testarea pe dispozitivele reale și cu datele proprii. Nu șterge datele browserului; exportă backup înainte de actualizare.


EXPORT ȘI PARTAJARE V42
- Fereastra de după salvarea devizului include acum și export Excel / Apple Numbers în format CSV bilingv (UTF-8 BOM, separator punct și virgulă, valori numerice cu virgulă zecimală).
- Butonul Partajează încearcă să trimită fișierul CSV prin meniul nativ de partajare iOS/Android, unde utilizatorul poate alege WhatsApp, Viber, Telegram, Mail sau altă aplicație instalată. Dacă partajarea fișierelor nu este suportată, aplicația descarcă CSV-ul și oferă partajarea textului prin WhatsApp, Telegram, Viber sau e-mail.
- În Evidență și în rândurile devizelor din Grupe există acum acțiune rapidă de partajare.
- PDF-ul rămâne disponibil prin fereastra de imprimare a browserului („Salvează ca PDF”). Browserul nu permite generarea/atașarea directă a unui PDF fără un motor PDF separat; utilizatorul poate salva PDF-ul din imprimare și îl poate distribui din sistemul dispozitivului.
