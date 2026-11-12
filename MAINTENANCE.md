# Pocket Budget — user and maintenance guide

Public app: https://recruitpeely929-coder.github.io/pocket-budget/
Source: https://github.com/recruitpeely929-coder/pocket-budget
Source ZIP: https://github.com/recruitpeely929-coder/pocket-budget/archive/refs/heads/main.zip

## Your records and backups
Records live in your browser on this device. They are not in the GitHub repository and do not sync automatically between your phone and laptop. Website hosting and the saved app do not require a running ChatGPT session. Hosting remains subject to your GitHub account and GitHub Pages availability.

In Settings & backup, select Export backup. Save the JSON file in Downloads and keep another copy somewhere you trust, such as Drive. Export weekly, before closing a month, before changing devices, and before clearing browser data. The in-app reminder appears after seven days. The last-export date indicates an export was requested; confirm the downloaded file exists.

Restore only when recovering or moving records, not as a daily routine. Choose a JSON backup, review its dates and record counts, then confirm replacement. Restore replaces all current records; it does not merge devices. The app first saves one local recovery copy. Settings → Previous records / recovery lets you download it or preview restoring it. Restoring again replaces that recovery slot with the records you are about to replace. Local recovery is not a substitute for an external backup and is lost if site storage is cleared.

To move devices: export on the old device, transfer the file, open the exact same app URL on the new device, and restore there. Then use one primary device to avoid conflicting versions.

## Recording and correcting purchases
Use Add expense, choose a spendable fund, amount and date, then save. Description is optional; a blank uses the fund name. Overspending requires an eligible donor. Big spending / Emergency has no fund.

Edit changes an active month's expense. Its old automatic cover transfer is reversed and a replacement is calculated from the edited expense. Choose a donor again if needed. Manual transfers stay independent. Delete also reverses a linked automatic cover transfer. Undo in transfer history returns money only if the receiving fund can return it.

Repeat opens a draft in the latest active month, with the old amount, fund and description and today's date (or a valid date within that selected month). Review and save; nothing is added until you confirm. Closed months can be viewed and repeated but cannot be edited.

## Closing a month and extra savings
Start the next calendar month in Settings, or select a new month and choose Start month. A review shows expenses, transfers, carryover, extra savings and yearly provisions. Resolve regular deficits and budget over-allocation first. Confirming closes the old month and creates the new one with your saved defaults. Skipped calendar months are not invented.

Fund balance = monthly allocation + opening carryover + transfers received − transfers sent − fund expenses.

Extra savings = sum of positive remaining balances in funds that reset. Carryover funds and yearly provisions are excluded. The regular savings allocation is separate. Monthly and cumulative extra savings use closed months only; the active month is a preview. This records the amount to set aside; it does not move money in a bank account.

## Yearly renewals
Maintenance, insurance, road tax, gym and custom yearly provisions are reserved monthly and cannot be used as everyday spending or transfer funds. Monthly pies include their monthly allocations. Actual yearly payments are recorded separately and included in actual payment-month totals, not counted again in the pies or extra savings.

A renewal period lasts one year from initiation. Actual payment date is independent. Leave initiation blank for TBA and edit it later. Additional payments can be assigned to the same period. Annual deficits are allowed. Reminders on Overview show dates within 30 days, due today, overdue and TBA. They appear only when the app is open; they are not Android push notifications. Add a new renewal period after renewing so the old period stops being the current reminder.

## Hosting and updating
This is a buildless static app on GitHub Pages, published from the main branch. Settings → Help & maintenance provides the source ZIP and this guide. The source ZIP contains the app; export your records separately.

Files:
- index.html: app shell, branding and versioned asset references.
- app.js: screens, forms, backups, reminders and charts.
- core.js: integer-cent calculations, validation and data migration.
- style.css: desktop and mobile styles.
- sw.js: offline shell caching, with network-first requests.
- manifest.json and PNG/ICO assets: install metadata and icons.
- tests/: calculation and interaction regression checks.

To develop: install a current Node.js version, serve the folder over HTTP (for example `python3 -m http.server 8000`), and open localhost in a browser. Do not rely on opening index.html directly. Use a test browser profile and artificial records. Never commit personal backup JSON files.

Before publishing, run every test with `for f in tests/*.cjs; do node "$f" || exit 1; done`, plus `node --check app.js` and `node --check core.js`. Verify phone-width layout, adding/editing/repeating/deleting expenses, covering overspending, transfer undo, month review, saving/restoring a downloaded backup, recovery, yearly dates and pie taps.

When changing files, update asset query versions in index.html and the matching sw.js asset list; increment the shell cache version. Preserve the localStorage key `pocket-budget-v2` and migrate older data instead of resetting it. Current payload version is 3. Closed-month history preserves carryover. Publish to main and confirm the Pages workflow succeeds. Retain commit history for rollback. A code rollback may not reverse data migrations, so export records first.

## Troubleshooting
- Old appearance: refresh while online, then close and reopen the app. Do not clear site data to update it.
- Missing records: check you opened the same URL, browser and device; then restore your latest external JSON backup if needed.
- Cannot close a month: cover all regular deficits and reduce over-allocated budgets.
- Cannot undo a transfer: receiving money has already been spent or transferred onward; reassign available money first.
- No reminder date: initiation is TBA or no period has been entered.
- A source ZIP is not a financial backup.
