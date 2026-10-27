DEVIZPRO v21 MULTIPLATFORM — EASY MODE
Versiune web/PWA adaptivă pentru telefon, tabletă și PC

CE ESTE ACEASTĂ VERSIUNE
- Păstrează aplicația DevizPRO existentă și funcțiile sale; nu este o rescriere de la zero.
- Adaugă/reglează comportamentul vizual pentru ecrane înguste, tablete și ecrane desktop.
- Include căutarea globală din versiunea anterioară, interfața RO/RU și sistemele existente de catalog, devize, evidență, backup/restore și export.
- Folderul acestei arhive se numește explicit DevizPRO_v21_MULTIPLATFORM, pentru a nu-l confunda cu folderul vechi v19.

FIȘIERE
- index.html — aplicația propriu-zisă.
- manifest.webmanifest — numele și setările PWA.
- service-worker.js — cache pentru încărcare offline după prima încărcare pe HTTPS/localhost.
- icon-192.png și icon-512.png — iconurile aplicației.

CUM O DESCHIZI
1. Extrage arhiva ZIP completă.
2. Pentru o verificare simplă, deschide index.html într-un browser modern. Unele funcții PWA/offline pot să nu fie disponibile prin deschiderea directă a fișierului.
3. Pentru instalare ca aplicație și cache offline, publică ÎNTREGUL conținut al folderului pe o adresă HTTPS (de exemplu, proiectul GitHub Pages existent), fără să amesteci fișiere din arhive diferite.
4. Pe iPhone/iPad deschide pagina în Safari; pe Android în Chrome; pe Windows într-un browser modern. Opțiunea de instalare diferă în funcție de browser și sistem.
5. După actualizarea unei versiuni publicate, închide complet aplicația instalată și redeschide-o. Service worker-ul v21 folosește o cheie de cache nouă și curăță cache-urile DevizPRO mai vechi.

IMPORTANT — DATELE ȘI BACKUPUL
- Înainte de a înlocui o versiune pe care o folosești deja, deschide acea versiune și exportă un backup complet ZIP. Păstrează copia în Files/iCloud Drive sau în alt loc separat.
- Datele existente sunt păstrate de browser în stocarea locală (localStorage/IndexedDB). Nu șterge datele site-ului și nu dezinstala versiunea veche înainte de a avea backup.
- Aplicația nu sincronizează automat datele între iPad, telefon și PC. Pentru mutarea datelor folosește funcția de transfer/backup din aplicație.
- GitHub Pages găzduiește codul aplicației, nu datele personale ale devizelor.
- O copie ZIP externă este mai sigură decât să te bazezi numai pe stocarea locală a browserului.

CE S-A SCHIMBAT ÎN V21
- Numele folderului și metadatele aplicației au fost aliniate la v21 MULTIPLATFORM.
- Regulile responsive sunt organizate explicit pentru telefoane compacte (până la 380 px), telefoane (381–650 px), tablete (651–1100 px) și desktop (peste 1100 px).
- Pe ecrane mici, câmpurile și rândurile de lucrări se rearanjează în coloane mai înguste; tabelele și previzualizările pot derula orizontal în loc să împingă întreaga pagină în afara ecranului.
- Sunt respectate zonele sigure ale ecranelor iPhone/iPad și setarea de accesibilitate pentru reducerea animațiilor.
- Cache-ul PWA a fost actualizat pentru a solicita noua versiune a fișierelor.
- Cheile locale de stocare ale datelor utilizatorului au fost păstrate pentru a evita schimbarea inutilă a spațiului de date.

LIMITĂRI ȘI VERIFICARE
- Aceasta rămâne o aplicație web/PWA, nu o aplicație nativă separată pentru fiecare sistem.
- Testele efectuate la livrare: verificarea integrității ZIP, verificarea sintaxei JavaScript inline și verificarea fișierelor de configurare.
- Nu pretindem testare completă pe dispozitive fizice. Înainte de folosirea zilnică, verifică pe dispozitivul tău: creare/salvare deviz, schimbare RO/RU, export PDF/imprimare, backup ZIP și restaurare pe o copie de test.
- Dacă datele vechi nu apar după publicare, nu reseta aplicația. Deschide versiunea veche și exportă backupul; apoi folosește funcția de restaurare/transfer.
