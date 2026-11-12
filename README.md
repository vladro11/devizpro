# DevizPRO V49

Aplicație web progresivă (PWA) pentru devize, măsurători și evidența lucrărilor. Interfața este în română și rusă, iar datele de lucru sunt păstrate local în browserul/dispozitivul utilizatorului.

## Deschidere
După activarea GitHub Pages, aplicația va fi disponibilă la:

https://vladro11.github.io/devizpro/

## Instalare pe iPad / iPhone
1. Deschide linkul în Safari și așteaptă încărcarea completă.
2. Apasă Share / Partajare.
3. Alege Add to Home Screen / Adaugă la ecranul principal.
4. Deschide DevizPRO din pictograma instalată.

Pe Android, deschide linkul în Chrome și folosește Install app / Add to Home screen.

## Offline și date
- Service Worker-ul V49 păstrează local fișierele aplicației și resursele incluse după prima încărcare reușită.
- Devizele, clienții, măsurătorile și celelalte date sunt stocate local pe dispozitiv; nu sunt sincronizate automat între dispozitive.
- Fă periodic backup din aplicație și păstrează o copie separată.
- Nu șterge datele site-ului/cache-ul browserului fără să ai un backup actualizat.

## Publicare
Repository-ul este configurat cu un workflow GitHub Actions pentru publicare din rădăcina ramurii `main`. În GitHub, deschide **Settings → Pages** și selectează **Source: GitHub Actions**. După salvare, fiecare actualizare pe `main` va declanșa publicarea.

## Versiune
Versiunea sursă încărcată: **V49**. Testele automate și limitele cunoscute sunt documentate în `V49_BROWSER_TEST_RESULTS.json`, `VERSION_STATE.json` și `RELEASE_NOTES_V49.md`.
