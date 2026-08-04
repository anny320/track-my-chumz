# Track my Chumz 💰

A budget accountability tool built for how Kenyans actually manage money. Paste your budget in plain text, track income and expenses, catch hidden costs, lock M-Pesa savings, and see exactly where your money goes — all from a single HTML file with zero backend.

**Live:** [anny320.github.io/track-my-chumz](https://anny320.github.io/track-my-chumz)

---

## What it does

Track my Chumz takes the messy way people actually write budgets — in notes apps, WhatsApp messages, or scribbled lists — and turns it into a structured, trackable financial picture.

Paste something like:

```
Balance in account 45000
Income - 120,000

Rent - 35000
Groceries - 15000
SACCO - 10,000 paid
Airtime - 1500 pd
Gym - 3k?
```

The parser handles mixed formats, "paid"/"pd" markers, "k" shorthand, question marks for uncertain expenses, and messy punctuation. It extracts income, balance, and line items with their statuses automatically.

---

## Features

### Budget Management
- **Natural language parser** — paste your budget however you'd write it, the app figures out the structure
- **Editable amounts** — tap any figure in the overview to change it inline
- **Partial payments** — mark bills as partially paid with a progress bar showing how much is left
- **Income deductions** — star (★) expenses that come off the top (SACCO, PAYE, loans) to see a visual drawdown from income received to net available
- **Custom categories** — add or remove expense items anytime

### Income Tracking
- **Multiple income sources** — salary, freelance, side income, each tracked separately
- **Received / Partial / Pending** — mark income as received, partially received, or still expected
- **Drawdown waterfall** — see your received income reduce step by step as deductions hit, showing what's actually available

### Investments & Savings
- **Track investments** — shares, stocks, ETFs, SACCO, money market funds, T-Bills, chama, crypto, pension, property
- **Grouped by type** — see all your share purchases together, all SACCO contributions together
- **Savings rate** — automatic calculation of your investment rate as a percentage of income
- **Notes and dates** — record details like "50 shares @ KES 42" with purchase dates

### Analysis Engine
- **Rule-based budget analysis** — no AI API costs, all calculations run locally
- **Spending velocity** — flags if you're burning faster than the month is moving
- **Daily spending limits** — calculates how much you can spend per day for the rest of the month
- **Partial payment tracking** — flags outstanding partial balances
- **Savings accountability** — checks if your savings target is on track
- **Hidden cost integration** — factors in your identified phantom expenses

### Hidden Expense Check-Up
- **8 preset categories** — daily coffee, ride-hailing, airtime, snacks, M-Pesa fees, bank charges, streaming, data bundles
- **Custom expenses** — add your own with flexible frequency (daily, weekly, monthly, quarterly, yearly)
- **Self-assessment framing** — asks "do you spend on this?" rather than asserting costs exist
- **Monthly/yearly projections** — shows cumulative impact of small recurring costs

### M-Pesa Lock Savings Guide
- Step-by-step Lock Savings setup
- Standing order automation
- Fuliza limit reduction (`*234#`)
- The 24-hour impulse rule

### Security
- **Optional 4-digit PIN** — protects access to the app
- **AES-256-GCM encryption** — all localStorage data encrypted with a key derived from your PIN via PBKDF2 (310,000 iterations)
- **Zero-knowledge** — PIN hash and encrypted data stay on your device; no server ever sees them
- **PIN reset** — forgot your PIN? Data is unrecoverable by design (two-step confirmation to wipe and start over)

### Export & Sync
- **CSV download** — structured export with income sources, expenses (including partial payments), investments, and summary
- **Clipboard copy** — TSV format, paste directly into Google Sheets
- **Google Calendar reminders** — one-click links for locking savings, mid-month reviews, weekly expense checks, month-end close, and Fuliza reduction

### History & Year-in-Review
- **Automatic monthly archive** — previous months are saved when a new month begins (up to 12 months)
- **Year-in-review** — total income, expenses, investments, savings rate, monthly trend chart, best/worst months, recurring expense detection
- **Month-over-month comparison** — tracks whether expenses grew or shrank
- **Reuse structure** — load a previous month's items and income sources into the current month with one tap

### Personalisation
- **Name and greeting** — time-of-day greeting with your name
- **Payday tracking** — shows your payday date in the header
- **Currency selection** — KES, NGN, GBP, USD, EUR, UGX, TZS, RWF, ZAR, GHS, ETB
- **Savings goal** — name, target amount, and target date with progress bar across months

---

## Tech Stack

- **Single HTML file** — no build step, no framework, no dependencies
- **Vanilla JavaScript** — ~2,400 lines, no libraries
- **localStorage** — all data stays on the user's device
- **Web Crypto API** — AES-256-GCM encryption + PBKDF2 key derivation (browser-native, no external crypto libraries)
- **Google Fonts** — DM Sans + DM Mono
- **GA4** — anonymous usage analytics (page views, feature usage; no financial data tracked)

---

## Deployment

### GitHub Pages

1. Clone this repo or download `index.html`
2. Push to a GitHub repository
3. Go to **Settings → Pages → Source: Deploy from branch → main → / (root) → Save**
4. Your app is live at `https://yourusername.github.io/your-repo-name`

### Google Analytics (optional)

Replace the two instances of `G-XXXXXXXXXX` near the top of `index.html` with your GA4 Measurement ID. Get one from [Google Analytics](https://analytics.google.com) → Admin → Data Streams → Web.

Events tracked: `tab_view`, `budget_parsed`, `status_changed`, `item_added`, `item_deleted`, `export_csv`, `export_clipboard`, `budget_reused`, `settings_saved`, `investment_added`, `income_added`, `deduction_toggled`, `hidden_costs_saved`, `pin_created`, `pin_changed`.

### Google Calendar Reminders

No API setup needed — reminders use direct Google Calendar URL links that open in a new tab. The user confirms each reminder individually.

---

## Privacy & Data

- All budget data is stored in the browser's localStorage. Nothing is sent to any server.
- The developer cannot see, access, or recover user data.
- Clearing browser data or switching devices removes all budget data.
- If PIN protection is enabled, all data is encrypted with AES-256-GCM. Without the PIN, data is unreadable — including to the developer.
- GA4 analytics (if enabled) tracks only feature usage events. No financial amounts, item names, income figures, or personal details are ever included in analytics data.
- A first-visit disclaimer and privacy notice are shown to all new users.

---

## File Structure

```
/
├── index.html    ← The entire app (single file)
└── README.md     ← This file
```

---

## Updates

Pushing a new version of `index.html` does not affect existing users' data. localStorage is browser-side and completely independent of the hosted files. Users keep all their budgets, history, settings, and investments across updates.

---

## Built by

[Wakara Technologies](https://wakaratech.com) · Nairobi, Kenya

---

## License

MIT
