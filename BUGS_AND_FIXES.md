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
