DevizPRO v9 — Devize de construcții pentru iPad

CE INCLUDE v9
- Avans încasat separat și sold rămas; avansul nu se dublează la acceptarea devizului.
- Panou principal cu venit încasat, avansuri și devize refuzate.
- Evidență generală pentru TOATE devizele, inclusiv cele repartizate în grupuri.
- Grupuri principale: maximum 50 devize în total, inclusiv subgrupe.
- Maximum 5 subgrupe pentru fiecare grup principal; maximum 10 devize în fiecare subgrupă.
- Contoare financiare pentru fiecare grup și subgrupă.
- Mutarea devizelor între grupuri/subgrupe.
- Sortare pentru grupuri și evidența devizelor după dată, numărul lucrărilor, valoarea devizului, venit și pierderi, în ordine crescătoare sau descrescătoare.
- Backup și restaurare care includ și grupurile/subgrupele.
- Exportul evidenței, catalog bilingv RO/RU, previzualizare și imprimare A4.

INSTALARE / PUBLICARE ÎN GITHUB PAGES
1. Descarcă și dezarhivează arhiva.
2. Deschide folderul DevizPRO_iPad_v9.
3. Încarcă FIȘIERELE din interiorul folderului în rădăcina depozitului GitHub (nu încărca folderul ca subfolder), suprascriind fișierele aplicației existente.
4. Fă Commit changes. GitHub Pages trebuie să publice din main / (root).
5. Pe iPad, închide complet aplicația/site-ul și redeschide-l. Service worker-ul v9 folosește un cache nou pentru a evita reutilizarea fișierelor vechi.

DATE ȘI BACKUP
Datele aplicației sunt păstrate local în browserul/dispozitivul folosit. Înainte de actualizare, deschide Setări și exportă un backup JSON. La restaurarea unui backup vechi care nu conține grupuri, devizele se restaurează fără grupări. Backupurile v9 includ și grupurile/subgrupele. Datele locale nu se transferă automat între dispozitive sau browsere.

IMPORTANT
Sintaxa JavaScript a fișierului principal a fost verificată. Testarea completă a tuturor fluxurilor în browser real și pe iPad nu a fost efectuată; după instalare, verifică adăugarea devizului, avansul, schimbarea statusului, gruparea, sortarea și exportul.

PDF
Dacă imprimarea adaugă URL-ul sau data în antet/subsol, dezactivează Headers and footers / Anteturi și subsoluri în dialogul de imprimare al browserului.
