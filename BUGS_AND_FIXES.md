# DevizPRO — Bugs and Fixes

## Deschise / necesită confirmare
- [ ] Utilizatorul trebuie să confirme că V45 apare în antet după publicarea tuturor fișierelor.
- [ ] Test pe iPad și telefon: Măsurători se deschide și funcționează.
- [ ] Confirmă vizual dispariția semnului MINUS decorativ gri/roșu din selectorul MERGE.
- [ ] Verifică butonul funcțional `− Minus`.
- [ ] Cardurile compacte, MOVE nou, editorul foto avansat, dialogul clipping și gruparea nouă sunt încă neimplementate.

## Corecții documentate
### V45
- Sincronizate etichetele publice ale versiunii la 45 și cache-ul Service Worker.
- Adăugat sistemul de documentare și continuitate AI.

### V44
- Eliminat CSS-ul pseudo-element care afișa semnul MINUS decorativ duplicat pe selectorul MERGE, conform documentației V44.
- Acțiunea reală `− Minus` a fost păstrată.
- Utilizatorul nu a confirmat încă vizual rezultatul pe dispozitiv.

## Eșecuri istorice relevante
### V43
- Utilizatorul a raportat că versiunea instalată părea V42 și README indica V42.
- Utilizatorul a raportat că Măsurători nu funcționa.
- Verificarea arhivei V44 a identificat erori de sintaxă în două blocuri inline V43 analizate.
- Utilizatorul a raportat `Download failed`.

## Regula de raportare
Nu muta un bug la „închis” doar pentru că a fost editat codul. Închide-l numai după testul aferent; până atunci folosește „corecție aplicată — confirmare necesară”.

---

# DevizPRO — Bugs and Fixes (English)

## Open items / user confirmation required

- [ ] User confirms V45 appears in the application header after installation/update.
- [ ] Test on iPad and phone that Measurements opens and works.
- [ ] Visually confirm removal of the decorative grey/red MINUS sign in the MERGE selector.
- [ ] Verify the actual `− Minus` button still works.
- [ ] Compact cards, redesigned MOVE, advanced photo editor, clipping dialog, and new grouping flow remain unimplemented unless a later source change proves otherwise.

## Recorded fixes

### V45
- Public version labels synchronized to 45 and Service Worker cache identifier updated.
- Portable AI continuity documentation added.
- Bilingual documentation update adds English sections and a consolidated Word reference; application logic is unchanged.

### V44
- CSS pseudo-element that displayed the decorative duplicate MINUS sign in the MERGE selector was removed, according to V44 documentation.
- The real `− Minus` action was retained.
- The user has not yet visually confirmed this correction on a device.

## Reporting rule

A documented fix is not automatically a verified fix. Record the source change, automated test, browser test, device test, and user confirmation separately.


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
