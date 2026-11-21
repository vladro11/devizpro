# DevizPRO — Test Checklist

## Release V45 — verificări automate
- [x] Toate cele 10 blocuri JavaScript inline extrase și verificate cu `node --check` — PASS.
- [ ] HTML parse valid.
- [ ] Fără ID-uri duplicate.
- [ ] Toate căile din `service-worker.js` există.
- [x] Versiunea 45 în meta, titlu, antet, README și cache — PASS.
- [ ] ZIP poate fi listat și testat cu `unzip -t`.
- [x] Fișierele AI CORE sunt incluse în arhivă — PASS.

## Teste funcționale în browser
- [ ] Aplicația pornește fără erori console.
- [ ] Schimbare limbă RO/RU fără amestec.
- [ ] Navigare între module.
- [ ] Măsurători: creare încăpere, creare obiect, editare, salvare și reîncărcare.
- [ ] MERGE și MINUS/Clipping.
- [ ] Fotografii: adăugare, miniaturi și persistență.
- [ ] Selector Măsurători în Deviz nou și cantități.
- [ ] Export PDF/print și CSV/partajare.
- [ ] Backup și restaurare pe copie de date.

## Teste pe dispozitive reale
- [ ] iPad Safari/PWA.
- [ ] Telefon iOS.
- [ ] Telefon Android Chrome/PWA.
- [ ] Windows desktop (Chrome/Edge).
- [ ] Touch, stylus și mouse pentru MOVE.

- [x] Verificarea ID-urilor: nu au fost identificate ID-uri duplicate în DOM-ul static inițial; șase șabloane dinamice conțin ID-uri reutilizate intenționat în editorul de tipuri, care trebuie să fie montat o singură dată la un moment dat.
- [x] Căile din lista `ASSETS` a Service Worker există.

## V45 — raport curent

- Versiune publică actualizată în `index.html` la 45.
- Cache Service Worker actualizat la V45.
- Documentația AI CORE adăugată.
- Testele fizice pe iPad/telefon/Windows: **NEEFECTUATE de asistent**.
- Testele funcționale Măsurători: **NEEFECTUATE de asistent**.
- Teste automate executate: 10/10 scripturi inline valide; versiunea sincronizată; ID-uri statice inspectate; toate căile Service Worker existente; ZIP verificat după creare. Nu le interpreta ca testare pe dispozitiv.

---

# DevizPRO — Test Checklist (English)

## V45 — recorded automated checks

- [x] Ten extracted inline JavaScript blocks passed `node --check` in the prior V45 build.
- [ ] HTML parser validation.
- [ ] Duplicate-ID audit.
- [ ] Verify every Service Worker asset path exists.
- [x] Version 45 synchronized in meta tag, page title, header, README, and cache identifier in the prior V45 build.
- [x] AI CORE documentation included in the archive.
- [ ] Re-run ZIP integrity check for this bilingual documentation update.
- [ ] Confirm every human-readable document has Romanian and English content.
- [ ] Confirm the bilingual Word document opens and contains all sections.

## Functional browser tests — pending

- [ ] Application starts without console errors.
- [ ] Language switch between Romanian and Russian without mixed-language UI.
- [ ] Navigation between modules.
- [ ] Measurements: create room/object, edit, save, reload.
- [ ] MERGE and MINUS/Clipping.
- [ ] Add photos, render thumbnails, and verify persistence.
- [ ] Transfer Measurements quantities into New Estimate.
- [ ] Export PDF/print and Excel/Numbers.
- [ ] Offline reload and Service Worker update.

## Physical device tests — not performed by the assistant

- [ ] iPad/iOS.
- [ ] Android phone.
- [ ] Windows laptop/desktop.

Do not mark a test as passed unless it was actually run. The prior `node --check` results do not prove browser or device functionality.


## V2 E1 — verificări pentru acest build
- [ ] Versiunea nu apare în antetul vizibil al aplicației.
- [ ] Titlul filei browserului afișează DevizPRO V2 E1.
- [ ] Meta application-version este 2-E1.
- [ ] Service Worker folosește cache V2 E1 și toate resursele există.
- [ ] Toate blocurile JavaScript inline trec `node --check`.
- [ ] ZIP trece `unzip -t`.
- [ ] Test de pornire în browser și verificare date persistente.
- [ ] Test pe iPad, telefon și desktop — încă neefectuat.


## V2 E2 — verificări efectuate
- [x] 11/11 blocuri JavaScript inline trec `node --check`.
- [x] Document HTML parsabil cu BeautifulSoup; 0 ID-uri duplicate în DOM-ul static.
- [x] Toate resursele din lista Service Worker există.
- [x] Titlu/meta/cache sincronizate la V2 E2.
- [x] Arhiva ZIP verificată după creare.
- [ ] Test interactiv browser: NECONFIRMAT (Chromium headless nu a finalizat pornirea în mediul disponibil).
- [ ] iPad/telefon/desktop: NEtestate fizic.
- [ ] Verificare funcțională completă pentru dialog tip nou, fotografii, MINUS, MERGE și reordonare: necesită dispozitiv.

## V2 E2 — checks performed (English)
- [x] All 11 inline JavaScript blocks pass `node --check`.
- [x] HTML parses with BeautifulSoup; zero duplicate IDs in the static DOM.
- [x] All Service Worker asset paths exist.
- [x] Title/meta/cache synchronized to V2 E2.
- [x] ZIP archive integrity checked after packaging.
- [ ] Interactive browser test: NOT CONFIRMED (headless Chromium did not finish startup in the available environment).
- [ ] iPad/phone/desktop: NOT physically tested.
- [ ] Full functional validation of new type dialog, photos, MINUS, MERGE, and reorder: requires device testing.
