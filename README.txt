DevizPRO v14 PRO — BACKUP, TRANSFER ȘI REDUCERI CU CONTROL MANUAL

PORNIRE
- Deschide index.html sau publică întregul conținut al acestui folder în GitHub Pages.
- Păstrează index.html, service-worker.js, manifest.webmanifest și ambele iconuri împreună în aceeași locație.
- Folderul corect este DevizPRO_iPad_v14_PRO (nu v10/v14).

FUNCȚII PĂSTRATE ȘI NOI
- Devize bilingve RO/RU, catalog, categorii, grupe/subgrupe, totaluri și reordonare manuală din v14.
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
2. Descarcă și extrage DevizPRO_iPad_v14_PRO.zip.
3. În repo-ul public devizpro, branch main, root (/), încarcă ÎNTREGUL conținut al folderului extras și confirmă înlocuirea fișierelor cu același nume. Nu șterge repo-ul și nu schimba setarea GitHub Pages.
4. După publicare, închide complet aplicația instalată pe ecranul principal și redeschide-o. Dacă Safari păstrează versiunea veche, reîncarcă pagina; service worker-ul v14 elimină cache-urile DevizPRO vechi.
5. Înainte de utilizarea de zi cu zi, testează backup ZIP, restaurare pe un dispozitiv de test și transfer selectiv.

COMPATIBILITATE ȘI LIMITE
- Aplicația rămâne o aplicație web/PWA, nu o aplicație nativă. Este proiectată pentru Safari pe iPad/iPhone, Chrome pe Android și browsere moderne pe Windows.
- Transferul între dispozitive se face prin fișier (Files/AirDrop/cablu/aplicația preferată); nu este necesar server propriu. Bluetooth direct universal nu este promis.
- Datele aplicației sunt locale fiecărui browser/dispozitiv. GitHub Pages publică doar codul aplicației, nu sincronizează automat devizele utilizatorului.
- Backupurile locale IndexedDB pot fi eliminate de browser/sistem; copia ZIP externă este cea mai sigură.
- Testele automate de sintaxă și integritate trebuie completate cu teste reale în Safari, Android și Windows înainte de a considera versiunea verificată pe toate dispozitivele.
