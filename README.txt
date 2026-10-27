DevizPRO

Versiune de pachet: V29 — optimizare incrementală peste V28/V27. Nu este o aplicație reconstruită.

Păstrate din versiunea de bază:
- Devize, catalog, grupe, clienți, setări, istoric și cheile de stocare existente.
- Export PDF/imprimare, XLSX, copiere text și funcționare offline-first.
- Plăți, rambursări, istoricul corectărilor, bonuri, procese-verbale, suplimente și backup.

Optimizări V29:
- Calculatorul flotant are un buton cu pictogramă de calculator, pornește în stânga la mijloc, poate fi mutat prin atingere/tragere și păstrează poziția doar pe durata deschiderii aplicației. Poziția se resetează la o nouă deschidere. Corectat evenimentul dublu care împiedica deschiderea calculatorului.
- Formularul de proces-verbal este mult mai compact, iar după salvare se curăță câmpurile pentru următorul proces-verbal. Lista proceselor-verbale este compactă, poate fi sortată după dată/client/număr și permite ștergerea confirmată, cu înregistrarea evenimentului.
- Bonurile au configurare compactă individuală: format compact/A4, semnătură, selectarea câmpurilor, setări avansate ascunse sub pictograma creion și date prestator/firma. Câmpurile goale sau nebifate nu se tipăresc.
- QR-ul bonului este o imagine pătrată PNG/JPG/WEBP încărcată de utilizator. Nu se generează și nu se pretinde a fi un cod fiscal oficial.
- Bonurile pot fi editate la nivelul datelor afișate (client, prestator, dată, observație) fără a modifica valorile contabile ale plății. Anularea unui bon îl scoate din încasările active, dar păstrează înregistrarea și jurnalul.
- Butoane icon-only pentru export/print în secțiunile financiare. Înainte de export/print apare selectarea perioadei: azi, 7 zile, 2 săptămâni, o lună, 3 luni, 6 luni, un an sau toate înregistrările.
- Căutarea globală acceptă mai mulți termeni (ex. „lucrarea 206”), deschide secțiunea potrivită și pentru catalog filtrează după cod și derulează la lucrarea găsită.
- Îmbunătățiri de spațiere și layout pentru ecrane mici și orientare landscape.
- Textele noi și rapoartele exportate sunt bilingve română/rusă acolo unde se aplică.

Compatibilitate și siguranță:
- Păstrează cheile de stocare V27/V28; noile câmpuri sunt adăugate în setările/înregistrările existente.
- Nu există cont, server sau sincronizare automată. Transferul între dispozitive se face prin backup exportat/importat.
- Înainte de actualizare, păstrează V28 și exportă un backup complet al datelor.
- Bonurile sunt documente informative de evidență și nu înlocuiesc un bon fiscal oficial.
- Sintaxa JavaScript a scripturilor inline a fost verificată cu Node.js. Testul automat de rulare în browser nu a putut fi finalizat în mediul de lucru; verifică funcțiile pe iPad și pe calculator înainte de utilizarea cu clienții.
