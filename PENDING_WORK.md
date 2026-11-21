# DevizPRO — Plan de lucru V2 E1 → E2+

**Regulă versiuni:** V2 E1 este prima ediție a seriei V2. Modificările viitoare cresc doar numărul E: E2, E3, E4 etc.

## Cerințe confirmate în conversația din 21.11.2026

### Măsurători — card compact
- [ ] Rând compact unic: pictogramă selector în stânga, selectorul Obiect/Tip în centru, buton verde + în dreapta.
- [ ] Selectorul de pictograme se deschide numai la apăsarea pictogramei din stânga; nu se afișează o zonă separată sub câmp.
- [ ] Dimensiuni pe un rând: lungime, înălțime/lățime, adâncime, adaptate la lățimea ecranului.
- [ ] Camera și Galeria ca butoane icon-only compacte.
- [ ] Eliminare completă a butonului fără funcție „Modifică dimensiuni”.
- [ ] Vizibilitate prin pictogramă ochi: verde = vizibil, gri/roșu = ascuns.
- [ ] Acțiunea MINUS existentă se păstrează; nu se elimină și nu se dublează.

### Fereastra „+ Obiect/Tip nou”
- [ ] Numai în această fereastră apar Adaugă, Salvează în setări și X.
- [ ] Adaugă creează tipul doar în încăperea curentă.
- [ ] Salvează în setări creează tipul în încăperea curentă și îl salvează în catalogul general.
- [ ] X închide/anulează; dacă există date nesalvate, cere confirmare.

### Fotografii
- [ ] Fiecare fotografie făcută/aleasă din interiorul unui obiect se asociază acelui obiect.
- [ ] Galeria încăperii agregă automat fotografiile tuturor obiectelor, fără duplicarea fișierelor.
- [ ] Galeria încăperii permite și fotografii generale, fără obiect asociat.
- [ ] Filtrare/grupare după obiect și păstrarea relației la ștergere/editare.
- [ ] Camera și Galerie compacte, cu pictograme clare.

### Reordonare și responsive
- [ ] Drag-and-drop fiabil pentru touch, stylus și mouse.
- [ ] Butoane alternative sus/jos.
- [ ] Telefon: navigare jos; tabletă: navigare sus; desktop: meniu lateral.
- [ ] Pagini secundare cu Înapoi și fără bara principală repetată.

### Home și Setări
- [ ] Home combină dashboard financiar și organizarea zilnică a lucrărilor.
- [ ] Graficele folosesc date reale din aplicație, nu valori demonstrative.
- [ ] Setări grupate în categorii clare, fiecare pe rând separat pe telefon.
- [ ] Câmpuri personalizate acolo unde sunt utile.

## Prioritate de implementare
1. Audit date și backup; maparea funcțiilor reale V45, inclusiv MINUS și fotografii.
2. Card compact Măsurători și fereastra +.
3. Asocierea foto obiect → galerie încăpere.
4. MOVE și responsive navigation.
5. Home și Setări.
6. Teste automate, browser, apoi test pe dispozitive reale.

# DevizPRO — Pending Work / Backlog

Ultima actualizare: V45 · 12.11.2026

## Prioritatea 0 — confirmarea bazei

- [ ] Utilizatorul instalează V45 (sau V44 dacă preferă comparația) și confirmă versiunea vizibilă.
- [ ] Verifică dacă Măsurători se deschide și permite creare/editare încăpere și obiect.
- [ ] Verifică dacă datele existente au rămas intacte.
- [ ] Confirmă dacă pictograma MINUS decorativă gri/roșie a dispărut; butonul funcțional MINUS trebuie să rămână.

## Prioritatea 1 — UI compact Măsurători

- [ ] Card obiect mult mai compact pentru telefon, tabletă și desktop.
- [ ] Pictograma obiectului în stânga sus, schimbabilă la apăsare.
- [ ] MOVE în dreapta sus, pe același rând.
- [ ] MOVE prin pointer/touch/mouse/stylus, fără selectare accidentală; pragul și timpul se testează pe dispozitive.
- [ ] Lungime, lățime și adâncime într-un singur rând compact, în metri.
- [ ] Camera/Galeria ca pictograme mici în partea inferioară; miniaturi în flux stânga-dreapta.

## Prioritatea 2 — fotografie

- [ ] Viewer pe tot ecranul, zoom, pan și swipe între imaginile aceluiași obiect.
- [ ] Editor cu pensule, culori, grosimi, text, fonturi și dimensiuni.
- [ ] Undo/redo, curățare și ieșire fără pierderea originalului.
- [ ] Salvare fotografie pe dispozitiv.
- [ ] Salvare copie editată în obiect.

## Prioritatea 3 — MINUS/Clipping

- [ ] Dialog de editare a dimensiunilor clipping, disponibil doar pentru obiectele clipping.
- [ ] Salvare și anulare.
- [ ] Restaurare obiect clipping și fotografii la obiectul de origine.
- [ ] Fără pictogramă duplicată/nefuncțională.

## Prioritatea 4 — Gruparea obiectelor

- [ ] Buton Grupare lângă +Obiect și Șterge.
- [ ] Mod checkbox și bară de confirmare/anulare.
- [ ] Dialog pentru numele grupului.
- [ ] Total agregat, expandare componente și editare individuală.
- [ ] Fotografiile tuturor componentelor afișate în grup.
- [ ] Integrare în selectorul Deviz nou; grup sau componente individuale.
- [ ] Clipping children nu se dublează în total și listă.

## Prioritatea 5 — testare și release

- [ ] Testează Măsurători pe iPad, telefon și desktop.
- [ ] Testează salvare/încărcare și backup/restore.
- [ ] Testează limbile RO/RU.
- [ ] Testează export și partajare.
- [ ] Verifică versiunea publică, manifestul, Service Worker și cache-ul.
- [ ] Actualizează documentația și jurnalul conversației înainte de fiecare ZIP.

---

# DevizPRO — Pending Work / Backlog (English)

**Last updated:** V45 bilingual documentation update · 12 November 2026

## Priority 0 — confirm the baseline

- [ ] User installs V45 and confirms the visible version label.
- [ ] Verify Measurements opens and allows room/object creation and editing.
- [ ] Confirm existing data remains intact.
- [ ] Confirm the decorative grey/red MINUS icon is gone and the real MINUS action remains functional.

## Priority 1 — compact Measurements UI

- [ ] Make object cards substantially more compact on phone, tablet, and desktop.
- [ ] Put the changeable object icon at upper left.
- [ ] Put MOVE at upper right on the same row.
- [ ] Make MOVE reliable for pointer/touch/mouse/stylus and prevent accidental icon activation; tune hold/drag behavior through device testing.
- [ ] Fit length, width, and depth fields into one compact row where possible; retain metre units.
- [ ] Reduce camera/gallery control size and place them at lower right.
- [ ] Display photo thumbnails left-to-right with automatic wrapping.

## Priority 2 — photo viewer/editor

- [ ] Full-screen viewer with zoom, pan, and swipe between photos for the same object.
- [ ] Editor with brush, pen, marker, colour, thickness, text/font/size, undo/redo.
- [ ] Save image to device and save edited copy to object; never overwrite original.
- [ ] Clear tool layout: close at upper right, device save beside it, vertical tools on right, undo/redo near upper left, and a clear save-copy action.

## Priority 3 — MINUS/Clipping and grouping

- [ ] Remove only the decorative inactive duplicate minus icon; retain the working `− Minus` action.
- [ ] Clipped child belongs to its parent and is not separately listed or counted in New Estimate.
- [ ] Provide a dimensions editor with Save/Cancel and restore object/photos to the original owner.
- [ ] Add object grouping controls, multi-select, group naming, group totals, expandable/editable components, and aggregated photos.
- [ ] Allow selecting either a group or its components in the estimate selector without double counting.

## Priority 4 — validation and release

- [ ] Test persistence, language exclusivity, exports, offline startup, and Service Worker updates.
- [ ] Test on iPad, Android phone, and Windows.
- [ ] Update all Romanian-English documents, chat log, changelog, and JSON state.
- [ ] Package and integrity-check the complete ZIP.


## V2 E2 — stare după upgrade (21.11.2026)
- [x] Card compact: pictogramă stânga, selector central, plus dreapta.
- [x] Câmpuri dimensionale compacte și responsive.
- [x] Camera/Galerie icon-only.
- [x] Dialog tip nou: Add temporar vs Save to settings permanent.
- [x] Reordonare sus/jos pentru încăperi și obiecte.
- [x] Titlu și cache V2 E2; versiunea nu apare în UI.
- [ ] Pictograme personalizate, redenumire/ștergere și recente.
- [ ] Ochi vizibilitate separat de selecția „Pentru deviz”.
- [ ] Agregare fotografii obiect → galerie încăpere.
- [ ] Reordonare sigură pentru grupe și toate modulele; evaluare eliminare drag-and-drop după testare.
- [ ] Navigare completă telefon/tabletă/desktop și ascundere bară în subpagini.
- [ ] Home dashboard cu date reale și carduri configurabile.
- [ ] Setări grupate și optimizate.
- [ ] Teste funcționale în browser și pe iPad/telefon/desktop.

## V2 E2 — state after upgrade (English)
- [x] Compact card: icon left, selector center, plus right.
- [x] Responsive compact dimension inputs.
- [x] Icon-only Camera/Gallery.
- [x] New type dialog: temporary Add vs permanent Save to settings.
- [x] Up/down reordering for rooms and objects.
- [x] V2 E2 title/cache; no version label inside app UI.
- [ ] Custom icons, rename/delete, and recent section.
- [ ] Visibility eye, separate from “For estimate” selection.
- [ ] Object-photo aggregation into room gallery.
- [ ] Safe reorder for groups/all modules; decide on removing drag-and-drop only after testing.
- [ ] Fully responsive navigation and hiding primary nav in subpages.
- [ ] Home dashboard with real data and configurable cards.
- [ ] Grouped and optimized Settings.
- [ ] Browser and physical iPad/phone/desktop functional tests.
