# DevizPRO V49 — Module & Function Inventory / Inventar module și funcții

## Scop / Purpose

RO: Acest document este inventarul de nivel arhitectural al modulelor și al funcțiilor identificate în codul V48/V49. Nu este o certificare că fiecare funcție a fost testată. Stările de test sunt în `V49_BROWSER_TEST_RESULTS.json` și `VERSION_STATE.json`.

EN: This document is the architectural-level inventory of modules and functions identified in the V48/V49 source. It is not a certification that every function has been tested. Test status is recorded in `V49_BROWSER_TEST_RESULTS.json` and `VERSION_STATE.json`.

## 1. Navigare și interfață / Navigation and UI

- Scop / Purpose: page switching, language switching, responsive navigation, swipe navigation, dynamic UI refresh.
- Funcții-cheie / Key functions: `showPage`, `setLang`, `initSwipeNavigation`, `pageJump`, `refreshAll`, `injectUI`, `bindDynamicEventsOnly`.
- V49: 14 direct navigation destinations; desktop side rail; horizontal navigation on narrow screens; active state tracks the exact page ID.
- Dependențe / Dependencies: `#nav` buttons use `data-page`; every target must have a matching `.page` ID; dynamic pages may be created at runtime.

## 2. Principală / Home dashboard

- Scop / Purpose: totals and recent quotes, entry point to common workflows.
- Funcții / Functions: `refreshAll`, `renderLedger` (shared summary data), `showPage`.
- V49: four quick-action cards (New Estimate, Measurements, Work Catalog, Settings/Backup), local images, recommended workflow note.
- Date / Data: reads quotes, status and totals; no separate business records are created by quick-action cards.

## 3. Deviz nou / New Estimate

- Scop / Purpose: compose an estimate from manually selected catalog works, set quantities/prices, reductions/advance, save and export.
- Funcții / Functions: `newQuote`, `resetQuoteForm`, `addLine`, `updateLine`, `removeLine`, `clearLines`, `renderLinesAndPreview`, `renderPreview`, `saveQuote`, `loadQuote`, `printQuote`, `quoteCsv`, `quoteText`, `copyCurrentQuoteText`.
- Interacțiuni / Interactions: Work Catalog supplies names/codes/units/prices; Measurements can transfer quantities; Groups/Ledger read saved quotes; export/print uses the current quote snapshot.
- Regulă / Rule: work units remain user-defined; the calculated unit validation in Measurements must not block manually configured estimate lines.

## 4. Catalog lucrări / Work Catalog

- Scop / Purpose: maintain construction work names, codes, units, categories and prices.
- Funcții / Functions: `renderCatalog`, `sortWorks`, `suggestedPrice`, `suggestedPriceForMode`, `getPriceHistory`, `learnManualPrices`, `savePriceHistory`, `resetFrequentPrices`, `openWorkForm`, `submitWork`, `deleteWork` (where defined in dynamic UI).
- Date / Data: `dp_catalog`, `dp_price_history`, `dp_price_mode`, `dp_categories`.
- Cerință / Requirement: preserve the existing bilingual Romanian/Russian work names and all user-entered codes, units and prices during migration.

## 5. Categorii / Categories

- Scop / Purpose: organize catalog work items.
- Funcții / Functions: `renderCategories`, `addCategory`, `renameCategory`, `deleteCategory`, `fillCategorySelects`.
- Date / Data: `dp_categories`; linked by category identifiers in catalog records.

## 6. Măsurători / Measurements

- Scop / Purpose: rooms, measured objects, dimensions, photos, grouping, clipping, and quantity transfer into New Estimate.
- Funcții core / Core functions: `dpMeasureNew`, `dpMeasureAddRoom`, `dpAddMeasureObject`, `dpSetMeasureValue`, `calcElement`, `v41Net`, `saveMeasures`, `renderMeasureRooms`, `renderSavedMeasures`, `dpV41ApplyRuler`, `dpV41StartClip`, `dpV41ApplyClip`, `dpV41RestoreClip`, `dpV41EditClip`, `dpV41PhotoPick`.
- V49 functions: `objHtml`, `dpV46StartGrouping`, `dpV46ToggleObject`, `dpV46ConfirmGrouping`, `dpV47CreateGroup`, `dpV46GroupMenu`, `dpV46EditGroupObjects`, `dpV46SaveGroupObjects`, `dpV46RenameGroup`, `dpV46DeleteGroup`, `dpV49PhotoView`, `dpV49PhotoEdit`.
- Date / Data: `dp_measurements`, `dp_measure_types`, `dp_measure_temp_types`; room objects use `elements`, photos use `photos`, clipping uses `clippedTo`, groups use `merges` and `componentIds`.
- Calcul / Calculation: length only → linear metres; length+width or length+height → area; length+width+depth → volume. The actual field/type configuration controls unit; quote work units are not used for this validation.
- Interacțiuni / Interactions: group/clipping rules are internal to Measurements; `dpV41ApplyRuler` transfers quantity to estimate line without enforcing the manually chosen quote unit.

## 7. Grupe / Groups

- Scop / Purpose: organize saved estimates into main groups/subgroups, move and reorder quotes, summarize totals.
- Funcții / Functions: `renderQuoteGroups`, `createQuoteGroup`, `createSubgroup`, `renameQuoteGroup`, `deleteQuoteGroup`, `moveGroup`, `assignQuoteGroup`, `addQuoteToGroup`, `removeQuoteFromGroup`, `moveQuoteInGroup`, `groupStats`, `groupText`.
- Date / Data: `dp_groups`, `dp_quotes`.
- Notă / Note: estimate grouping is separate from object grouping inside Measurements.

## 8. Evidență și zone / Ledger and zones

- Scop / Purpose: accepted/refused estimates, financial summaries, zone-based organization.
- Funcții / Functions: `renderLedger`, `printLedgerQuote`, `groupQuotes`, `locationTotal`, `dpGuessZone`, `addLocation`, `deleteLocation`, `renderTransferQuoteChecklist`, `exportTransferPackage`, `importTransferPackage`.
- Date / Data: `dp_quotes`, `dp_custom_zones`, `dp_zone_aliases`, `dp_zone_deleted`, `dp_zone_order`.

## 9. Clienți / Clients

- Scop / Purpose: maintain client records and associate clients with estimates.
- Funcții / Functions: `ensureClientsFromData`, client form handlers in dynamic UI, `render...` handlers in page scripts.
- Date / Data: `dp_clients`.

## 10. Calendar / Appointments

- Scop / Purpose: appointment dates and reminders.
- Funcții / Functions: `checkReminders`, `initReminderChecks`, `choosePeriod`, `periodStart`, `inPeriod`, `inSelectedPeriod`.
- Date / Data: `dp_appointments`.

## 11. Finanțe, plăți și bonuri / Finance, payments and receipts

- Scop / Purpose: expenses, advances, payment events, refunds, receipts, payment balances and reports.
- Funcții / Functions: `savePayment`, `correctPayment`, `refundPayment`, `getPaymentBalance`, `paymentTotals`, `filteredPayments`, `generateReceipt`, `printReceipt`, `printReceiptCopy`, `printRefund`, `deleteReceipt`, `editReceipt`, `openReceiptOptions`, `runPeriodReport`, `printPaymentsReport`.
- Date / Data: `dp_expenses`, `dp_payments`, `dp_payment_events`, `dp_refunds`, receipt settings and generated receipt records.

## 12. Materiale / Materials

- Scop / Purpose: store materials and associate them with construction tasks/costs.
- Funcții / Functions: page-specific render and form handlers; `render...` functions are defined in the main source and dynamic UI blocks.
- Date / Data: `dp_materials`.

## 13. Rapoarte de lucrări / Work reports

- Scop / Purpose: record work reports and print them.
- Funcții / Functions: `saveWorkReport`, `deleteWorkReport`, `renderWorkReports`, `printWorkReport`.
- Date / Data: `dp_work_reports`.

## 14. Setări / Settings

- Scop / Purpose: language, theme, company information, signature, price editing permissions, backup interval, and app preferences.
- Funcții / Functions: `fillSettings`, `applySettings`, `saveSettingsFromUI`, `setupSettingsButtons`, `toggleAdminMode`, `requireAdmin`, `applyThemePreset`, `applyFullPackage`, `setOrientation`, `setPriceMode`, `saveBackupInterval`.
- Date / Data: `dp_settings`, `dp_price_mode`, `dp_calc_position`.

## 15. Backup, transfer, import/export / Backup, transfer, import/export

- Scop / Purpose: protect data and move selected records between devices.
- Funcții / Functions: `backupData`, `restoreData`, `makeZip`, `readZip`, `readPackageFile`, `packageFiles`, `exportTransferPackage`, `importTransferPackage`, `downloadBlob`, `downloadCSV`, `quoteCsv`.
- Date / Data: snapshot includes relevant localStorage state and selected transfer entities; IndexedDB mirror uses `openDpDB`, `mirrorStateToIndexedDB`, `openDpDB`.
- V49 note: Service Worker cache is technical/static asset storage and must never be treated as the business-data backup.

## 16. Calculator / Calculator utility

- Scop / Purpose: on-screen calculation panel.
- Funcții / Functions: `calc`, `calcCompute`, `calcDisplay`, `calcKey`, `setCalcMode`, `saveCalc`, `renderSavedCalcs`, `makeCalcLauncherDraggable`, `positionCalcPanel`, `restoreCalcPosition`.
- Date / Data: `dp_calc_saved`, `dp_calc_position`.

## 17. Data keys observed / Chei de date observate

`dp_appointments`, `dp_calc_position`, `dp_calc_saved`, `dp_catalog`, `dp_categories`, `dp_clients`, `dp_custom_zones`, `dp_expenses`, `dp_groups`, `dp_materials`, `dp_measure_temp_types`, `dp_measure_types`, `dp_measurements`, `dp_payment_events`, `dp_payments`, `dp_price_history`, `dp_price_mode`, `dp_quote_measure_id`, `dp_quotes`, `dp_refunds`, `dp_settings`, `dp_work_reports`, `dp_zone_aliases`, `dp_zone_deleted`, `dp_zone_order`.

## 18. Module dependency summary / Rezumat dependențe

- Catalog → New Estimate: work title, code, unit and price.
- Measurements → New Estimate: measured quantity and descriptive context; quote unit remains user-defined.
- New Estimate → Groups/Ledger/Clients/Payments/Receipts: saved estimate records are the common business source.
- Groups → Ledger: group membership and group totals are derived from saved quotes.
- Settings → all modules: language, theme, business identity, signature and permissions.
- Backup → all persistent data: backup/restore must include the selected business datasets and preserve compatibility.
- Service Worker → static app files only: HTML/CSS/logo/image assets, not business records.

## 19. Audit boundary / Limita inventarului

RO: Funcțiile de mai sus sunt identificate în sursă, dar nu toate au fost exercitate în browser în V49. QA pentru PDF/Excel/CSV, bonuri, plăți, rapoarte, import/export backup, transfer, sincronizare și permisiuni rămâne backlog.

EN: The functions above were identified in source, but not all were exercised in the V49 browser run. QA for PDF/Excel/CSV, receipts, payments, reports, backup import/export, transfer, synchronization, and permissions remains in the backlog.
