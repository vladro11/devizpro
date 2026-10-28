DevizPRO V31 — remedieri incrementale peste V30

IMPORTANT
- Păstrează o copie a versiunii V30 și exportă backupul complet înainte de actualizare.
- Aplicația rămâne offline-first și păstrează cheile și structura principală de stocare existente.
- Nu s-a reconstruit aplicația de la zero.

Modificări V31
1. Corectată ordinea identificării pictogramelor: ștergerea unui proces-verbal folosește pictograma de ștergere, nu pe cea de imprimare/descărcare. Butoanele cu text explicativ din Setări nu mai sunt înlocuite accidental cu pictograme.
2. Pictograma de căutare globală din dreapta jos este acum o lupă SVG clară.
3. Eliminat exportul Excel/Numbers din devizul curent, lista devizelor și fereastra de export a devizului salvat. Eliminat exportul CSV/Excel din partea de bonuri și exportul CSV din partea de procese-verbale; rapoartele respective se deschid pentru imprimare/Salvare ca PDF.
4. Ștergerea definitivă a unui bon șterge și istoricul corectărilor/anulărilor/rambursărilor legat de acel bon, inclusiv înregistrările de audit asociate. Acțiunea cere confirmare.
5. Secțiunile din meniu și titlurile pentru Bonuri și Procese-verbale au denumiri română/rusă; ferestrele dinamice se reconstruiesc în limba aleasă.
6. Bonurile, rapoartele de plăți, procesele-verbale și documentele de rambursare au etichete și titluri bilingve în PDF, indiferent de limba interfeței. Procesele-verbale noi păstrează denumirile lucrărilor în ambele limbi.
7. Aliniate mai uniform controalele și butoanele din Setări; păstrat textul integral pentru „Șterge semnătura” și „Exportă pachet de transfer”.
8. Actualizată versiunea cache offline la V31.

Notă de testare
- Arhiva și sintaxa JavaScript sunt verificate automat.
- Nu s-a pretins testare completă pe un iPad fizic; verifică interacțiunile în aplicația ta după import și păstrează backupul V30.


Modificări de remediere V32 (27.10.2026)
1. Titlul secțiunii Bonuri este acum „Bonuri și Plăți” / „Квитанции и платежи”.
2. La schimbarea limbii, secțiunile Bonuri și Plăți și Procese-verbale sunt reconstruite în limba selectată, fără a modifica datele salvate.
3. Bifa pentru emiterea bonului este compactă, pătrată și verde când este selectată.
4. În istoricul plăților a fost eliminată pictograma redundantă de editare; „Corectare” rămâne, iar ștergerea este ultima acțiune, în dreapta, evidențiată cu roșu.
5. Butoanele de acțiune din istoricul plăților și procesele-verbale folosesc pictograme SVG cu dimensiuni și contrast explicite.
6. Pictogramele de acțiune din Evidență au stiluri forțate pentru a evita afișarea ca cercuri goale.
7. La apăsarea unei pictograme din meniul superior se afișează denumirea localizată a secțiunii.
8. Cache-ul service worker a fost incrementat la v32 pentru a preveni încărcarea versiunii anterioare.

Verificare tehnică: toate blocurile JavaScript din index.html trec verificarea sintaxei Node.js. Interacțiunile trebuie verificate în browserul țintă după instalare.


VERSIUNEA V33 — 28.10.2026
- Locații/grupări în deviz, cu denumire editabilă și subtotal separat la export.
- Reordonarea lucrărilor și locațiilor prin tragere sau săgeți sus/jos.
- Ascundere/reactivare lucrări și locații; elementele ascunse nu intră în total sau PDF/imprimare.
- Ștergere locație separat sau împreună cu lucrările ei.
- Fereastra de după salvare simplificată pentru export PDF/imprimare și închidere reparată.
- Numele aplicației rămâne DevizPRO.
