# Pocket Budget

A mobile-friendly personal budget tracker. No subscription, server, API key, or database is needed to run this static app. All financial records remain in the visitor's browser. The public source contains default allocations only, never entered spending records.

## Publish free with GitHub Pages

1. Create a public GitHub repository, e.g. `pocket-budget`.
2. Upload everything inside the `website` folder to the repository root. Upload the files themselves, not the ZIP.
3. In the repository open Settings → Pages.
4. Under Build and deployment, choose Deploy from a branch, select `main`, folder `/ (root)`, and Save.
5. GitHub will show your address, normally `https://YOUR-USERNAME.github.io/pocket-budget/`.
6. Open it in Android Chrome → menu (⋮) → Add to Home screen.

GitHub's free service remains subject to its current terms and limits. ChatGPT Plus is not required to open or use an independently hosted copy.

## Important: storage and moving devices

The app stores records under the website's browser origin. Export a JSON backup from Settings regularly. To move from the ChatGPT-hosted copy to GitHub Pages, or from phone to laptop, export at the old address and restore at the new one. They do not automatically sync. Private browsing or clearing site data may erase records. Backups contain financial information; store them safely.

The GitHub Pages copy caches its shell for offline use after an online visit, subject to browser cache retention. The ChatGPT-hosted copy does not install this cache because it is behind account access controls.

## Budget rules

- Default income and main budget: RM2,400. Both are editable separately.
- Default allocations follow the supplied example. Savings RM310.84 is an allocation only, not a savings account.
- Each fund has an allocation and a carry-forward/reset switch. Personal & Social and Miscellaneous carry forward by default.
- Add a new category by typing its name when adding/editing a fund. Funds can be renamed. Set allocation to zero to stop funding one while preserving its records.
- Changes can optionally become future month defaults. Closed months keep their original values.
- A regular expense exceeding available funds requires a donor fund. A transfer covers the shortfall. Transfers do not increase total spending.
- Fund cards retain spending above original allocation plus carryover, even after a transfer covers it, and show the donor fund.
- Manual transfers can redistribute money in advance. Donors cannot go below zero.
- Category deficits must be covered before starting a later month. Over-allocation beyond the main budget also blocks month closing.
- Starting a later month closes the previous active month. Closed months remain readable and cannot be edited, to preserve downstream carryover accuracy. Export backups before advancing.
- New months use saved default allocations. Only unused positive balances in funds marked carry-forward are carried into the next recorded month. Deficits never carry.
- Big spending / Emergency has no fund. It is included in total spending but does not reduce fund balances or require a category transfer. Its external funding is outside the tracker.

## Reports

Monthly overview; spending by category and fund; budget versus actual; original overspending; transfer history and sources; month-to-month comparison; carryover breakdown. No spending pace or forecast.

## Backups and CSV

JSON backup contains all months, defaults, entries, transfers, and carryover rules. Restore validates structure and rollover consistency, then replaces local records after confirmation. CSV export includes expenses for the selected month; transfers remain in the JSON backup and transfer history.

## Validation

Core automated tests verify exact cents arithmetic, default totals, transfers, donor limits, Big spending isolation, carryover/reset, month closing, and backup integrity. DOM-stub smoke tests cover view and dialog rendering. Full device/browser visual QA was not available during creation.
