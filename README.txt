DEVIZPRO V40 — MENIU DIRECT ȘI INTERFAȚĂ COMPACTĂ

BAZĂ
DevizPRO V39 Fix. Structura offline și modulele existente au fost păstrate.

MODIFICĂRI IMPLEMENTATE ÎN ACEST PACHET
1. Bara principală are exact patru destinații: Principală, Deviz nou, Măsurători și Mai multe.
2. Bonurile și procesele-verbale nu mai sunt injectate în bara principală; se deschid direct din Mai multe.
3. Mai multe afișează 12 intrări directe, grupate numai prin subtitluri descriptive. Fiecare modul se deschide printr-o singură apăsare.
4. Pictograme vectoriale dedicate și carduri mai mari; grilă adaptivă pentru telefon, tabletă și desktop.
5. „Releveu nou” a devenit „Măsurătoare nouă”.
6. A fost eliminată injectarea duplicată a butonului „Tip nou”.
7. Ștergerea tipurilor de măsurătoare este disponibilă inclusiv pentru tipurile standard; datele măsurătorilor deja salvate nu sunt șterse.
8. Controalele de selectare și deducere din lista măsurătorilor au fost compactate vizual.
9. Cache-ul service worker a fost incrementat la V40.

MODULE PĂSTRATE DIN V39
Devize, catalog, categorii, grupe, clienți, calendar, finanțe, materiale, bonuri/plăți, procese-verbale, evidență, zone, măsurători, setări și backup/restaurare existente.

IMPORTANT — SPECIFICAȚIA COMPLETĂ V40 NU ESTE ÎNCĂ INTEGRAL IMPLEMENTATĂ
Acest pachet este o etapă de lucru V40, nu o certificare finală a tuturor cerințelor aprobate. Funcțiile care necesită implementare separată includ: grupuri de măsurători și clipping cu alegerea suprafeței țintă; selector de măsurători în câmpul cantitate al devizului; fluxul „Salvează și creează nou / Creează fără salvare / Anulează”; editarea și mutarea înregistrărilor între zone; atașamente foto multiple la finanțe și materiale; administrarea și îmbinarea grupurilor de materiale; căutarea rapidă a devizului în selectorul materialelor; redesign complet al tuturor checkbox-urilor și localizare rusă exhaustivă. Acestea nu sunt declarate finalizate în acest pachet.

VERIFICĂRI EFECTUATE
- Integritatea ZIP verificată.
- Sintaxa tuturor celor 8 blocuri JavaScript inline verificată cu Node.js.
- Test browser automat: bara de navigare are exact 4 destinații; „Mai multe” afișează 12 module; modulul Finanțe se deschide direct; navigarea rămâne la 4 destinații.
- Testul browser fără origine HTTP locală raportează erori de acces localStorage din cauza documentului sandbox; acestea nu sunt folosite ca dovadă de defect al aplicației și nu permit certificarea completă a persistenței.
- Nu a fost testată interacțiunea pe iPad fizic și cu date reale.

SIGURANȚA DATELOR
Înainte de instalare, exportă și păstrează un backup complet din versiunea care conține datele reale. Nu șterge datele site-ului/browserului. Păstrează separat V39.
