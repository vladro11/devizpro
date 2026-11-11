DEVIZPRO V39 — V38 RUNTIME FIX

Baza: arhiva DevizPRO V38 furnizată pentru reparație.

REMEDIERE CRITICĂ V39
- Corectată poziționarea modulului V38: stilurile și logica pentru navigație, meniul „Mai multe”, evidența pe zone și măsurători erau introduse accidental în șablonul HTML al ferestrei de imprimare a unui deviz, nu în documentul aplicației.
- Din cauza acestei inserări, scriptul principal devenea invalid și funcțiile noi nu se executau. Modulul a fost mutat în documentul principal, în afara șablonului de imprimare.
- Verificate sintactic toate cele 8 blocuri JavaScript extrase din documentul HTML cu Node.js.
- Actualizat cache-ul service worker la V39 pentru a evita reutilizarea fișierelor V38 defecte.

FUNCȚII PĂSTRATE DIN V38
1. Bară principală cu patru destinații: Principala, Deviz Nou, Măsurători și Mai multe, cu pictograme SVG și etichete.
2. Meniul Mai multe reorganizat în categorii: Documente și evidență; Clienți și programări; Lucrări și materiale; Finanțe; Instrumente și administrare.
3. Evidență pe zone: Ciocana, Buiucani, Botanica, Rîșcani, Centru, Telecentru, Codru, Durlești, Sîngera, Stăuceni, Cricova, Trușeni și zone personalizate; zona poate fi corectată manual.
4. Modul Măsurători: relevee, încăperi, elemente/obiecte, tipuri standard și personalizate, câmpuri dimensionale configurabile, calcul automat m.l./m²/m³, unitate manuală și selectare pentru transfer în Deviz Nou.
5. Setări Măsurători: creare și editare tipuri, tipuri permanente sau temporare, configurarea câmpurilor, unități și pictograme.
6. Selector offline cu combinații tematice de pictograme pentru construcții, instalații, mobilier și obiecte casnice.
7. Marcarea elementelor deductibile și scăderea lor din totalurile calculate pe unități.
8. Backup/restaurare extinsă pentru măsurători, tipuri de măsurători și zone personalizate.
9. Modulele moștenite din baza V35.1/V38 rămân incluse: clienți, calendar, finanțe, materiale, catalog, bonuri/plăți, procese-verbale, setări, grupe și evidență.

VERIFICĂRI ȘI LIMITĂRI
- Integritatea arhivei ZIP: verificată.
- Sintaxa tuturor blocurilor JavaScript inline: verificată.
- Nu a fost posibilă certificarea tuturor fluxurilor pe iPad fizic și nu se poate promite funcționare 100% fără testare pe dispozitiv și cu datele reale.
- Înainte de instalare, exportă backupul complet din versiunea care conține datele tale și păstrează V38 separat. Nu șterge datele site-ului/browserului.
- După înlocuire, închide complet aplicația și redeschide-o. Dacă versiunea veche rămâne în cache, reîncarcă aplicația după ce ai confirmat backupul.
