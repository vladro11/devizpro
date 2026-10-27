DevizPRO v15 PRO — BACKUP, TRANSFER ȘI REDUCERI CU CONTROL MANUAL

PORNIRE
- Deschide index.html sau publică întregul conținut al acestui folder în GitHub Pages.
- Păstrează index.html, service-worker.js, manifest.webmanifest și ambele iconuri împreună în aceeași locație.
- Folderul corect este DevizPRO_iPad_v15_PRO (nu v10/v15).

FUNCȚII PĂSTRATE ȘI NOI
- Devize bilingve RO/RU, catalog, categorii, grupe/subgrupe, totaluri și reordonare manuală din v15.
- Reducerile sunt oprite implicit la crearea unui deviz nou. Activează butonul doar când dorești să aplici reduceri.
- Backup complet în ZIP fără compresie (format ZIP standard), cu manifest și date JSON pe secțiuni.
- Restaurare completă din ZIP-ul DevizPRO sau din backup JSON mai vechi compatibil.
- Transfer total ori selectiv: toate datele, toate devizele, un grup/subgrup, un deviz, catalog/categorii sau setări.
- Importul selectiv combină datele; nu șterge înregistrările neincluse în pachet. Pentru ID-uri care se ciocnesc, aplicația cere confirmare și păstrează versiunea cu actualizare mai nouă.
- Copii locale în IndexedDB (până la 20), plus oglindire compatibilă a datelor existente din localStorage. Datele vechi nu sunt șterse în timpul migrării.
- Backup automat local la intervalul ales cât timp aplicația este deschisă; browserul poate suspenda activitatea în fundal. Descarcă periodic și păstrează un ZIP extern.
- Se solicită stocare persistentă browserului atunci când funcția este disponibilă.

PUBLICARE GITHUB PAGES
1. Deschide DevizPRO existent și descarcă backupul complet înainte de înlocuirea fișierelor.
2. Descarcă și extrage DevizPRO_iPad_v15_PRO.zip.
3. În repo-ul public devizpro, branch main, root (/), încarcă ÎNTREGUL conținut al folderului extras și confirmă înlocuirea fișierelor cu același nume. Nu șterge repo-ul și nu schimba setarea GitHub Pages.
4. După publicare, închide complet aplicația instalată pe ecranul principal și redeschide-o. Dacă Safari păstrează versiunea veche, reîncarcă pagina; service worker-ul v15 elimină cache-urile DevizPRO vechi.
5. Înainte de utilizarea de zi cu zi, testează backup ZIP, restaurare pe un dispozitiv de test și transfer selectiv.

COMPATIBILITATE ȘI LIMITE
- Aplicația rămâne o aplicație web/PWA, nu o aplicație nativă. Este proiectată pentru Safari pe iPad/iPhone, Chrome pe Android și browsere moderne pe Windows.
- Transferul între dispozitive se face prin fișier (Files/AirDrop/cablu/aplicația preferată); nu este necesar server propriu. Bluetooth direct universal nu este promis.
- Datele aplicației sunt locale fiecărui browser/dispozitiv. GitHub Pages publică doar codul aplicației, nu sincronizează automat devizele utilizatorului.
- Backupurile locale IndexedDB pot fi eliminate de browser/sistem; copia ZIP externă este cea mai sigură.
- Testele automate de sintaxă și integritate trebuie completate cu teste reale în Safari, Android și Windows înainte de a considera versiunea verificată pe toate dispozitivele.


TRANSFER ZIP v15: DevizPRO can import ZIP archives created by DevizPRO even when the archive uses standard DEFLATE compression or has a top-level folder. On the receiving device, open Settings > Backup and restore > Transfer between devices, tap the ZIP/JSON import control, and select the single ZIP file received through Telegram/Files. Choose full restore (replace) or merge (add/update without deleting records absent from the archive).


SALVARE RAPIDĂ ȘI PREȚURI INTELIGENTE (v15 actualizat)
- La salvarea unui deviz nou, acesta se păstrează în evidență, formularul „Deviz nou” se golește automat, iar fereastra de finalizare oferă export Excel/Numbers sau PDF/imprimare. Fereastra poate fi închisă cu X sau „Gata”.
- La salvarea modificărilor unui deviz deja existent, rămâne fluxul actual de editare; nu se deschide fereastra de finalizare pentru devize noi.
- PDF/imprimarea din fereastra de finalizare este bilingvă indiferent de limba interfeței. Excel/Numbers include denumirile lucrărilor și antetele în română și rusă.
- Modul implicit folosește prețul introdus manual cel mai des în devizele anterioare; dacă nu există istoric pentru o lucrare, propune media dintre minim și maxim.
- „Resetare prețuri minime”, „Resetare prețuri medii” și „Resetare prețuri maxime” forțează modul ales. „Folosește prețurile des folosite” revine la prețurile învățate din istoric și NU șterge istoricul.
- În catalog și în lista de adăugare a lucrărilor, sortarea implicită este „Cele mai des folosite”, calculată după numărul de devize salvate în care apare fiecare lucrare, nu după cât de recent a fost folosită. Se poate schimba în „Număr de ordine”, „După categorii” sau „După nume”.
- Interfața pentru noile controale și fereastra de finalizare respectă limba selectată RO/RU.
