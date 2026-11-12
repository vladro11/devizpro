# DevizPRO — Troubleshooting & Recovery / Diagnosticare și recuperare

Acest ghid oferă alternative de diagnostic, nu promite că orice problemă are aceeași cauză. Înainte de orice intervenție asupra datelor, exportă un backup ZIP și lucrează pe o copie.

## 30 situații și alternative / 30 situations and recovery options

### 1. Pagina arată versiunea veche
Verifică fișierul index.html publicat, meta application-version și titlul; apoi verifică cache-ul Service Worker și data ultimului deploy.

**EN — The page shows an old version:** Check the deployed index.html, application-version meta tag, and title; then inspect the Service Worker cache and latest deployment timestamp.

### 2. Stilurile noi nu apar
Confirmă că assets/css/devizpro-shell.css există în repository, calea este relativă corectă și resursa răspunde 200; verifică apoi ordinea CSS.

**EN — New styles do not appear:** Confirm assets/css/devizpro-shell.css exists in the repository, the relative path is correct, and the asset returns 200; then inspect CSS cascade order.

### 3. Navigarea arată doar patru pagini
Caută filtrul care elimină butoane din #nav; verifică cele 14 data-page și dacă fiecare id există.

**EN — Only four navigation pages appear:** Search for code filtering/removing #nav buttons; verify all 14 data-page values and matching page IDs.

### 4. Un modul se deschide gol
Verifică pagina cu id corect, funcția showPage și erorile console; confirmă că rendererul corect este conectat.

**EN — A module opens blank:** Check the page ID, showPage handler, console errors, and whether the intended renderer is connected.

### 5. Măsurători nu se randază
Verifică bridge-ul dintre IIFE-uri: rooms, calcElement, saveMeasures și dpSetMeasurementRenderer; rulează testul de randare cu o încăpere minimă.

**EN — Measurements does not render:** Check the cross-IIFE bridge for rooms, calcElement, saveMeasures, and dpSetMeasurementRenderer; run a minimal room-render test.

### 6. Gruparea nu apare
Confirmă că dpV46StartGrouping este conectată la buton și că modul de selecție nu este ascuns de CSS.

**EN — Grouping does not appear:** Confirm dpV46StartGrouping is wired to the button and selection mode is not hidden by CSS.

### 7. Gruparea refuză obiectele
Compară unitățile calculate din numărul și tipul câmpurilor; nu compara cu unitatea unei lucrări din Deviz.

**EN — Grouping rejects objects:** Compare units calculated from the number/type of measurement fields; do not compare with a New Estimate work unit.

### 8. Gruparea dublează totalul
Verifică componentIds și filtrele care ascund obiectele membre din lista principală; totalul trebuie calculat o singură dată.

**EN — Grouping double-counts totals:** Check componentIds and the filter hiding members from the main list; each member must be counted once.

### 9. Obiectele dispar la desfacerea grupului
Verifică dacă se șterge numai înregistrarea group, nu r.elementele; restaurează din backup dacă datele au fost eliminate.

**EN — Objects disappear after ungrouping:** Verify that only the group record is removed, not r.elements; restore from backup if records were deleted.

### 10. Minus nu oferă obiecte
Verifică dacă există obiecte negrupate în aceeași încăpere și cu aceeași unitate calculată.

**EN — MINUS offers no objects:** Check whether ungrouped objects exist in the same room with the same calculated unit.

### 11. Minus permite scădere prea mare
Verifică comparația cantității scăzute cu v41Net înainte de a seta clippedTo.

**EN — MINUS allows an oversized deduction:** Check the deducted quantity against v41Net before setting clippedTo.

### 12. Copilul clipping apare separat
Verifică filtrul roots = obiecte fără clippedTo și randarea copilului în interiorul părintelui.

**EN — A clipped child appears separately:** Check that roots excludes objects with clippedTo and the child renders inside its parent.

### 13. Cantitatea nu intră în Deviz
Verifică dpV41ApplyRuler și updateLine; unitatea manuală a lucrării nu trebuie suprascrisă.

**EN — Quantity does not transfer to estimate:** Check dpV41ApplyRuler and updateLine; the manually defined work unit must not be overwritten.

### 14. Prețurile catalogului par goale
Verifică încărcarea catalogului și cheile de stocare; nu importa un catalog gol peste datele utilizatorului.

**EN — Catalogue prices appear empty:** Check catalogue loading and storage keys; do not import an empty catalogue over user data.

### 15. Pictograma PWA lipsește
Verifică manifestul, căile icon-192.png/icon-512.png și răspunsurile serverului; apoi reinstalează shortcut-ul doar după backup.

**EN — PWA icon is missing:** Check the manifest, icon-192.png/icon-512.png paths, and server responses; reinstall the shortcut only after backup.

### 16. Logo-ul se vede neclar
Folosește SVG pentru documente și PNG 1024 pentru platformele care nu acceptă SVG; nu mări un thumbnail mic.

**EN — Logo looks blurry:** Use SVG for documents and the 1024 px PNG where SVG is unsupported; do not upscale a small thumbnail.

### 17. Fotografiile nu se încarcă offline
Verifică dacă toate assets/objects/*.webp sunt incluse în Service Worker CORE și au fost cache-uite online cel puțin o dată.

**EN — Photos fail offline:** Check that all assets/objects/*.webp files are in Service Worker CORE and were cached after at least one online load.

### 18. Editorul nu deschide fotografia
Verifică dacă sursa este data URL validă și dacă FileReader/Image a terminat încărcarea; testează o singură fotografie mai mică.

**EN — Editor cannot open a photo:** Verify the source is a valid data URL and FileReader/Image loading has completed; test with one smaller photo.

### 19. Copia editată nu se salvează
Verifică target.photos, saveMeasures și spațiul local; exportă backup, apoi încearcă o copie JPEG mai mică.

**EN — Edited copy is not saved:** Check target.photos, saveMeasures, and local storage capacity; export a backup, then retry with a smaller JPEG copy.

### 20. Undo/redo nu revine corect
Verifică indexul istoricului și dacă snapshot este adăugat după fiecare acțiune completă, nu la fiecare pointermove.

**EN — Undo/redo behaves incorrectly:** Check the history index and ensure snapshots are added after completed actions, not on every pointermove.

### 21. MOVE nu pornește
Verifică data-v41-handle, listenerul pointerdown și pragul 520 ms; mișcarea mai mare de 12 px înainte de hold anulează long-press pentru a permite scroll.

**EN — MOVE does not start:** Check data-v41-handle, pointerdown listener, and 520 ms hold; movement over 12 px before hold cancels long-press to allow scrolling.

### 22. MOVE începe accidental
Mărește pragul de hold sau distanța de mișcare; testează separat mouse, deget și stylus.

**EN — MOVE starts accidentally:** Increase the hold threshold or movement threshold; test mouse, finger, and stylus separately.

### 23. Navigarea mobilă taie modulele
Folosește scroll orizontal în #nav și verifică overflow-x; nu reduce butoanele sub o țintă tactilă utilizabilă.

**EN — Mobile navigation clips modules:** Use horizontal scrolling in #nav and check overflow-x; do not shrink buttons below usable touch targets.

### 24. Pagina are scroll orizontal nedorit
Identifică elementul cu lățime fixă în DevTools și verifică la 390/412/834 px; corectează grid-template și min-width.

**EN — Page has unwanted horizontal scroll:** Identify fixed-width elements in DevTools and test at 390/412/834 px; correct grid-template and min-width.

### 25. Limba este amestecată
Verifică data-ro/data-ru și toate șirurile create dinamic; nu hardcoda etichete într-o singură limbă în noile componente.

**EN — Language is mixed:** Check data-ro/data-ru and dynamically generated strings; do not hardcode one-language labels in new components.

### 26. Service Worker păstrează o versiune veche
Incrementează numele cache-ului, verifică lista CORE, publică toate fișierele și așteaptă activarea noului worker; nu șterge storage de business.

**EN — Service Worker keeps an old version:** Increment the cache name, verify CORE, publish all files, and wait for the new worker to activate; do not clear business storage.

### 27. Aplicația nu pornește fără internet
Deschide o dată online după deploy pentru a popula cache-ul; verifică dacă toate resursele inițiale sunt în CORE și dacă fetch fallback funcționează.

**EN — App does not start offline:** Open once online after deployment to populate cache; verify initial resources are in CORE and fetch fallback works.

### 28. Backup ZIP nu se importă
Verifică integritatea ZIP, fișierele manifest, dimensiunea și versiunea formatului; testează întâi într-un profil de browser separat.

**EN — ZIP backup will not import:** Check ZIP integrity, manifest files, size, and format version; test first in a separate browser profile.

### 29. Transferul între dispozitive eșuează
Verifică dacă ambele dispozitive au versiuni compatibile, permisiuni de fișier și aceeași selecție de categorii; folosește export/import ZIP ca alternativă.

**EN — Cross-device transfer fails:** Check compatible versions, file permissions, and matching category selections; use ZIP export/import as a fallback.

### 30. Datele par pierdute după update
Nu șterge datele site-ului. Verifică același domeniu/origin, backup local, IndexedDB și storage keys; restaurează numai pe o copie de test.

**EN — Data appears lost after update:** Do not clear site data. Check the same domain/origin, local backup, IndexedDB, and storage keys; restore only on a test copy.

### 31. PDF/Excel are conținut greșit
Compară datele sursă cu preview-ul și exportul; verifică limbă, orientare, coloane bilingve, totaluri și separator zecimal.

**EN — PDF/Excel content is wrong:** Compare source data, preview, and export; check language, orientation, bilingual columns, totals, and decimal separators.

## Regula de siguranță / Safety rule

RO: Înainte de orice migrare, restaurare sau schimbare de storage, exportă backup ZIP și păstrează arhiva anterioară. Nu șterge `localStorage`, IndexedDB sau datele site-ului pentru a rezolva un cache stale.

EN: Before any migration, restore, or storage change, export a ZIP backup and keep the previous archive. Do not clear `localStorage`, IndexedDB, or site data to solve a stale cache.
