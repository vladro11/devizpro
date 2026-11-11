# DevizPRO — Istoric general al proiectului

**Actualizat:** V45 · 12.11.2026  
**Notă privind acuratețea:** istoricul exact al tuturor arhivelor V1–V41 nu este disponibil în această sesiune. Nu completăm golurile prin presupuneri.

## V1–V40 — istoric incomplet

Utilizatorul a descris proiectul ca aplicație web locală/offline pentru devize de construcții, pornită dintr-un catalog Excel. Cerințele istorice cunoscute includ catalog bilingv RO/RU, devize, export, evidență/grupe, backup și utilizare pe iPad/Android/Windows. Detaliile exacte pe fiecare număr de versiune nu sunt certificate fără arhivele respective.

## V41 — strat de funcționalități menționat în istoricul proiectului

README-ul V42 și documentația V44 indică existența unui strat de funcții V41 pentru Măsurători și alte extensii. Detaliile sunt moștenite din documentația proiectului, nu revalidate individual în această versiune.

## V42 — 11.11.2026 — bază recuperată

- Arhiva conține `index.html`, `service-worker.js`, `manifest.webmanifest`, pictograme și documentație minimală.
- README-ul V42 descrie integrarea Măsurători → Deviz nou, încăperi, obiecte, MERGE, MINUS/Clipping, fotografii și reordonare.
- Verificarea efectuată în sesiunea V44 a raportat că toate blocurile JavaScript inline din V42 treceau `node --check`.
- V42 a fost aleasă ca bază de recuperare după eșecul V43.

## V43 — 12.11.2026 — release eșuat

- Utilizatorul a raportat că arhiva instalată se comporta ca V42 și README-ul indica tot V42.
- Utilizatorul a raportat că Măsurători nu mai funcționa.
- Verificarea documentată în V44 a identificat erori de sintaxă în scripturile inline `dpV38Core` și `dpV42ShareAndSpreadsheet` din arhivele V43 analizate.
- Descărcarea V43 a eșuat pentru utilizator; un link redenumit nu a rezolvat problema de încredere în build.
- Concluzie: V43 nu este bază validă.

## V44 — 12.11.2026 — restabilizare

- Reconstruită din arhiva V42 originală, nu din V43.
- Eticheta antetului V44 și cache-ul Service Worker V44 au fost setate.
- README și documentele proiectului au fost adăugate.
- CSS-ul care desena semnul MINUS decorativ duplicat pe selectorul MERGE a fost eliminat conform notelor V44; acțiunea funcțională `− Minus` a fost păstrată.
- Nu au fost implementate toate cerințele UI avansate pentru Măsurători; acestea au rămas documentate ca restante.
- Utilizatorul nu a instalat/testat V44 înainte de a cere V45.

## V45 — 12.11.2026 — continuitate și documentare

- Baza: arhiva V44 furnizată în conversație.
- Public version metadata, titlul paginii și antetul au fost sincronizate la V45; identificatorul cache Service Worker a fost incrementat la V45.
- A fost introdus protocolul AI obligatoriu, istoricul conversațiilor disponibil, jurnalul deciziilor tehnice, explicații de cod, starea versiunii și lucrările restante.
- Nu au fost făcute redesign-uri ale modulului Măsurători în V45; prioritatea a fost documentarea și sincronizarea versiunii, deoarece utilizatorul nu testase încă V44.
- V45 nu este declarată stabilă până când utilizatorul nu confirmă instalarea și testarea Măsurătorilor.

## Regula pentru completări

Fiecare release viitor adaugă o secțiune nouă la final. Nu se rescriu secțiunile anterioare. Dacă o informație istorică este corectată, se adaugă o notă de corecție datată, cu motiv și sursă.

---

# DevizPRO — Project History (English)

**Updated:** V45 bilingual documentation update · 12 November 2026  
**Accuracy note:** The complete exact history of every V1–V41 archive is not available in this session. Missing details must not be invented.

## V1–V40 — incomplete historical record

The project is a free, offline-first local web application for construction estimates, originally based on an Excel work-price catalogue. Known historical requirements include a Romanian/Russian bilingual work catalogue, estimates, PDF/print and Excel/Numbers export, accounting/groups, backups, and use on iPad, Android, and Windows. Exact per-version changes are not certified without the corresponding archives.

## V41 — feature layer referenced by project history

The V42 README and V44 documentation refer to a V41 feature layer for Measurements and other extensions. These details are inherited from project documentation and have not been independently revalidated in this release.

## V42 — 11 November 2026 — recovered baseline

- Archive includes `index.html`, `service-worker.js`, `manifest.webmanifest`, icons, and minimal documentation.
- Its README describes Measurements-to-New Estimate integration, rooms, objects, MERGE, MINUS/Clipping, photos, and reordering.
- During the V44 session, all extracted inline JavaScript blocks were reported to pass `node --check`.

## V43 — 11–12 November 2026 — reported failure

The user reported that V43 appeared identical to V42 and Measurements stopped working. V43 is therefore not treated as a user-confirmed stable baseline.

## V44 — 12 November 2026 — restoration build

V44 was rebuilt from V42 after the V43 report. Its documentation records removal of a decorative duplicate MINUS pseudo-element while retaining the actual `− Minus` action. The user had not yet confirmed the visual result on a device.

## V45 — 12 November 2026 — versioning and AI continuity

V45 inherited the V44 application code, synchronized public version labels and Service Worker cache identity, and added a portable AI documentation system. It did not implement the requested Measurements redesign. Physical device testing was not performed by the assistant.

## V45 bilingual documentation update

This update adds English content alongside Romanian in the project documents and provides a consolidated bilingual Word file. Application functionality and data structures remain unchanged.
