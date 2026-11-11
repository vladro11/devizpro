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


## Release V46 — 12.11.2026 (actualizare funcțională)

- Baza: arhiva încărcată `DevizPRO_V45_PRO_BILINGUAL(1).zip`; codul și documentele V45 au fost păstrate ca punct de plecare.
- Interfața Măsurători primește un layout mai compact și ordonat: antet de încăpere, acțiuni grupate, carduri de obiect, sumar și stiluri responsive pentru ecrane mici.
- Fluxul nou de grupare folosește structura existentă `room.merges` / `componentIds`, pentru compatibilitate cu grupările vechi. Obiectele grupate sunt ascunse în lista principală și apar în interiorul grupării la extindere.
- Gruparea cere minimum două obiecte și verifică unitatea calculată în Măsurători. La unități diferite afișează avertizare și nu creează gruparea.
- Gruparea are meniu pentru redenumire, modificarea componenței și ștergere. Ștergerea elimină numai înregistrarea grupului; obiectele, dimensiunile și fotografiile rămân în încăpere.
- MINUS are un selector clar și buton explicit de aplicare. Sunt oferite obiecte compatibile din aceeași încăpere; logica existentă verifică unitatea și limitele cantității înainte de clipping.
- Validarea unității a fost eliminată din transferul riglei către liniile Deviz nou. Unitatea lucrării din deviz rămâne personalizată de utilizator; cantitatea preluată nu este blocată de comparația unităților.
- Eticheta publică V45 a fost eliminată din brand și titlul browserului; versiunea 46 rămâne în metadate/cache tehnic. Numele și pictogramele instalabile nu afișează numărul versiunii.
- Datele existente `dp_measurements`, `room.elements`, `photos`, `clippedTo` și `merges` nu au fost migrate sau șterse.
- Limitări explicite: biblioteca extinsă de fotografii reale (mii de imagini), editorul foto avansat, redesignul complet al tuturor modulelor și testele fizice pe iPad/Android/Windows nu sunt incluse/confirmate în acest release. Cardurile păstrează încă selectorul de tip și pictograma existentă; imaginile foto reprezentative urmează într-un release separat după stabilirea catalogului de resurse.


## Release V46 — 12 Nov 2026 (functional update)

- Base: uploaded archive `DevizPRO_V45_PRO_BILINGUAL(1).zip`; V45 source and documentation were retained as the starting point.
- Measurements receives a more compact, ordered layout: room header, grouped actions, object cards, summary, and responsive styling for small screens.
- The new grouping workflow reuses the existing `room.merges` / `componentIds` structure for compatibility with legacy groups. Grouped objects are hidden in the main list and shown inside the expanded group.
- Grouping requires at least two objects and validates the calculated unit inside Measurements. Mixed units show a warning and do not create a group.
- Each group has a menu to rename it, edit its membership, or delete the group. Deletion removes only the group record; object records, dimensions, and photos remain in the room.
- MINUS now has a clear selector and explicit apply action. Compatible objects from the same room are offered; existing clipping logic validates units and remaining quantity before applying the clip.
- Unit validation was removed from the ruler transfer into New Estimate lines. Work units in estimates remain user-defined; imported quantities are no longer blocked by a unit comparison.
- The public V45 suffix was removed from the brand and browser title; version 46 remains in technical metadata/cache only. The installed app name and icons do not show a version number.
- Existing `dp_measurements`, `room.elements`, `photos`, `clippedTo`, and `merges` data were not migrated or deleted.
- Explicit limitations: a large library of real photos (thousands of images), the advanced photo editor, a full redesign of every module, and physical iPad/Android/Windows tests are not included/confirmed in this release. Object cards still use the existing type selector and pictogram; representative photo assets are deferred to a separate release after the asset catalog is defined.
