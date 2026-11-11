DEVIZPRO V41 — ACTUALIZARE FUNCȚIONALĂ PE BAZA V40

BAZĂ ȘI PĂSTRAREA DATELOR
- V41 pornește din arhiva V40 primită; aplicația nu a fost reconstruită de la zero.
- Cheile de stocare locală existente sunt păstrate. Nu există o comandă de ștergere a datelor locale.
- Service Worker folosește un cache nou V41. La activare, cache-urile vechi DevizPRO sunt înlocuite; datele din localStorage/IndexedDB nu sunt șterse de această operație.
- Păstrează separat arhiva V40 și exportă un backup local din fiecare dispozitiv înainte de publicare.

MODIFICĂRI V41 IMPLEMENTATE
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
- Sintaxa tuturor blocurilor JavaScript inline și a service-worker.js a fost verificată cu Node.js.
- Structura HTML a fost parsată; nu au fost găsite ID-uri duplicate în document.
- Test UI Chromium/Playwright cu un adaptor de stocare temporar în memorie: aplicația se încarcă; navigarea funcționează; schimbarea limbii RO/RU funcționează; selectorul de măsurători se populează; se pot crea încăperi și obiecte; MERGE a calculat 20,00 m² pentru 4 pereți; Clipping a atașat o componentă și a recalculat grupul la 14,00 m²; rigla a afișat grupul și componentele; lista zonelor s-a randat; importul unei imagini de test a produs o miniatură fără erori JavaScript.
- Aceste teste cu stocare temporară nu certifică limitele reale de localStorage ale fiecărui browser și nu înlocuiesc testarea cu datele reale ale utilizatorului.

LIMITĂRI / TESTARE PE DISPOZITIVE
- Nu a fost posibilă testarea fizică pe Android, iPhone, iPad sau Windows în această sesiune.
- Camera, galeria, permisiunile browserului, persistența fotografiilor, stocarea locală și gesturile de tragere trebuie probate pe dispozitive reale. Comportamentul camerei depinde de browser și de permisiunile acordate.
- Prin urmare, arhiva este o versiune V41 de testare, nu o certificare că totul este „perfect” pe toate dispozitivele.

INSTALARE
1. Exportă backup din V40 pe fiecare dispozitiv și păstrează ZIP-ul V40.
2. Înlocuiește fișierele din repository cu conținutul arhivei V41; nu șterge datele site-ului/browserului.
3. Deschide aplicația cu internet o singură dată pentru a descărca noul cache V41, apoi verifică funcționarea offline.
4. Dacă dispozitivul păstrează temporar interfața veche, închide complet aplicația/browserul și redeschide site-ul; nu șterge stocarea locală.
5. Testează întâi pe o copie a datelor. Păstrează backup-ul V40 până când confirmi că V41 funcționează corect pe fiecare dispozitiv.
