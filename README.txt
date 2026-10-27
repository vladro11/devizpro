DevizPRO

Versiune de pachet: V28 (optimizare incrementală peste V27; numele aplicației rămâne DevizPRO).

Baza păstrată din V27:
- Devizele, catalogul, grupele, setările și stocarea locală existentă.
- Export individual .xlsx, PDF/imprimare și copiere text.
- Funcționare offline-first și arhitectura PWA existentă.

Optimizări V28 adăugate:
- Evidență devize compactă, cu extindere la atingere; sortare după dată, nume deviz, nume client, număr de lucrări, valoare, venit și pierdere.
- Calculator flotant mutabil, cu mod standard, suprafață, volum și calcul cu rezervă; salvarea calculelor numite.
- Secțiune locală Plăți și bonuri: plăți multiple pe deviz, metode de plată, curs salvat per tranzacție, repartizare în ordinea lucrărilor sau proporțional, avans general, istoric, rambursări și jurnal de corectări. Filtre după perioadă, metodă și valută; rapoarte PDF/imprimare, XLSX și CSV.
- Bon configurabil individual: format compact/A4, semnătură, câmpuri vizibile și QR offline cu câmpuri alese. Câmpurile goale sunt omise. Bonul este informativ și NU este bon fiscal.
- Secțiune separată pentru procese-verbale de executare, cantitate/procent, semnalarea discrepanțelor și semnături client/prestator.
- Suplimente legate de devizul inițial și istoric de versiuni pentru devizele editate.
- Export backup complet ZIP și JSON, inclusiv noile date financiare; backup local la operațiuni importante.

Notă de compatibilitate:
- Versiunea păstrează cheile de stocare V27 și adaugă dp_payments, dp_refunds, dp_payment_events, dp_work_reports și dp_calc_saved.
- Nu există sincronizare automată între dispozitive. Transferul se face prin backup exportat/importat.
- QR-ul conține doar câmpurile selectate de utilizator; nu este QR fiscal sau de verificare oficială.
- Procesele-verbale, plățile și bonurile sunt înregistrări locale. Verifică cerințele fiscale/legale aplicabile înainte de a folosi documentele ca documente oficiale.
- Păstrează V27 și exportă un backup înainte de a actualiza.
- Service worker funcționează pe HTTPS sau localhost. Testează în continuare exporturile pe dispozitivul tău înainte de utilizarea cu clienții.

QR library notice: QRCode JavaScript core by Kazuhiko Arase / qrcode-terminal vendor, MIT license. See QR-LICENSE.txt.
