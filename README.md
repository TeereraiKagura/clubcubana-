# 🍾 Club Cubana — Management System

> A zero-dependency, mobile-first nightclub management app that replaces the notebook. Real-time Net Profit, stock tracking, expense logging, and month-over-month history — all in a single HTML file.

---

## ✦ Overview

Club Cubana Track was built to solve one problem: **knowing your real profit at any point in the night**, without manual notebook math. It implements the exact accounting formula used in real club operations:

```
COGS         = Opening Stock + Purchases − Closing Stock
Gross Profit = Sales Revenue − COGS
Net Profit   = Gross Profit − Total Expenses
```

Everything updates live. Every number on the dashboard reflects the current state of your stock, sales, and expenses at all times.

---

## 📸 Features

### Dashboard
- Live **Net Profit** display — green when profitable, red when not
- Four key metrics: Gross Profit, Expenses, Revenue, COGS
- **Sales trend bar chart** (last 7 entries)
- **Burn rate bar** comparing total expenses to gross profit
- **Stock alerts** with pulse animation for low-stock items
- Full **P&L summary** breakdown
- One-tap quick actions: Night Closing, Stock-In, Record Sale, Log Expense, Add Product

### Stock-In
- Select product → enter cases → app multiplies by case size automatically
- e.g. `5 cases × 24 = 120 units`
- Live cost preview before confirming
- Full purchase history with delete

### Closing Count (2AM Tool)
- Enter units remaining per product
- COGS calculated automatically in real-time
- Accessible from the **Night Closing** quick-action on the dashboard (slide-up modal — no tab switching required at 2AM)

### Sales
- Log revenue per product
- Units sold automatically deducted from stock
- Full sales history with delete

### Expenses
- **Fixed costs** (Rent, Starlink, DSTV, DJ) pre-loaded and auto-applied every month
- **Variable costs** with one-tap category chips: Ice, Water, Fuel, Free Drinks, Security, Cleaning, Décor
- Full expense table with running total

### Inventory — Self-Managed
- **Floating ＋ button** always visible on every screen
- **Add Product sheet** with:
  - Category icon tiles (🍺 Beer · 🥃 Spirits · 🍷 Wine · 🍾 Champagne · 🍏 Cider · 🥤 Soft · 📦 Other)
  - 3-step progress indicator
  - Live product card preview as you type
  - Set case size, cost, opening stock, and low-stock alert threshold
- Products flash on entry into the inventory list
- Remove any product at any time

### History
- Gold line chart of Net Profit trend across all months
- Tap any month card to review it
- Side-by-side comparison table (Revenue · Expenses · Net Profit)

### Month Management
- **New Month** carries closing stock forward as opening stock automatically
- Month selector in the header to switch between any recorded month
- **Export CSV** — full P&L report, purchases, sales, and expenses in one file for Excel

---

## 🚀 Getting Started

No installation. No build step. No dependencies.

```bash
# Clone the repo
git clone https://github.com/yourusername/club-cubana.git

# Open the app
open clubcubana.html
```

Or simply open `clubcubana.html` in any modern browser on any device.

---

## 📁 Project Structure

```
club-cubana/
│
├── clubcubana.html       # The entire application (single file)
└── README.md             # This file
```

The entire app — HTML, CSS, and JavaScript — lives in one self-contained file. No frameworks, no bundler, no server required.

---

## 💾 Data Storage

Data is currently stored in **browser `localStorage`**.

| Scenario | Data Status |
|---|---|
| Close tab and reopen | ✅ Data persists |
| Same browser, same device | ✅ Data persists |
| Different browser | ❌ Starts fresh |
| Different device | ❌ Starts fresh |
| Clear browser cache/data | ❌ Data lost |
| Incognito / Private mode | ❌ Lost on close |

**Best practice:** Use **Export CSV** at the end of every trading night as a backup. The CSV is also your Excel-ready report.

### Planned: Google Sheets Integration
A future version will connect to the Google Sheets API as a free cloud database, enabling:
- Access from any device
- Automatic cloud backup
- Native Excel/Sheets export

---

## 🧮 The Math

```
Opening Stock Value  = Σ (opening_units × unit_cost)  per product
Purchases Value      = Σ (cases × cost_per_case)       per purchase
Closing Stock Value  = Σ (closing_units × unit_cost)   per product

COGS                 = Opening Stock + Purchases − Closing Stock
Gross Profit         = Total Sales Revenue − COGS
Net Profit           = Gross Profit − Total Expenses
```

---

## 🗓️ Monthly Workflow

```
1. START OF MONTH
   └── Tap "New Month"
       └── Closing stock from last month → carried forward as opening stock

2. THROUGHOUT THE MONTH
   ├── Deliveries arrive?  → Stock-In tab
   ├── Sales made?         → Sales tab
   └── Expense incurred?   → Expenses tab

3. END OF EVERY NIGHT
   └── Night Closing button → enter remaining units → COGS auto-calculated

4. END OF MONTH
   └── Export CSV → archive in Excel
```

---

## ⚙️ Default Inventory

The app ships with five pre-loaded products. All can be edited or removed.

| Product | Category | Case Size | Cost/Case | Alert Threshold |
|---|---|---|---|---|
| Castle Lite | Beer | 24 units | $250.10 | 24 units |
| Hennessy | Spirits | 1 unit | $450.00 | 3 units |
| Tequila | Spirits | 1 unit | $320.00 | 2 units |
| Savanna | Beer | 24 units | $220.00 | 12 units |
| Moët | Champagne | 1 unit | $650.00 | 2 units |

---

## 💰 Default Fixed Expenses

| Expense | Monthly Cost |
|---|---|
| Rent | $500 |
| Starlink | $60 |
| DSTV | $35 |
| DJ | $110 |
| **Total** | **$705** |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML · CSS · JavaScript |
| Charts | Chart.js 4.4 (CDN) |
| Fonts | Cormorant Garamond · Rajdhani · DM Mono (Google Fonts) |
| Database | Browser localStorage (v1) |
| Hosting | Any static host — Vercel, Netlify, GitHub Pages |
| Build | None required |

---

## 🌐 Deployment

### GitHub Pages
```bash
# In your repo settings → Pages → Deploy from branch → main → / (root)
# App will be live at: https://yourusername.github.io/club-cubana/
```

### Vercel
```bash
npm install -g vercel
vercel --prod
```

### Netlify
Drag and drop `clubcubana.html` into [netlify.com/drop](https://netlify.com/drop).

---

## 🗺️ Roadmap

- [x] Real-time Net Profit dashboard
- [x] Stock-In with case multiplier
- [x] 2AM closing count tool
- [x] Fixed + variable expense tracker
- [x] Self-managed inventory catalog
- [x] Month history with charts
- [x] CSV export
- [x] Night Closing modal shortcut
- [ ] Google Sheets API integration (cloud database)
- [ ] Progressive Web App (PWA) — install on home screen
- [ ] PIN-protected owner mode
- [ ] Multi-user support (owner vs. staff view)
- [ ] WhatsApp / SMS profit summary at close of night

---

## 📄 License

MIT — free to use, modify, and deploy.

---

<div align="center">
  <strong>Built for Club Cubana</strong><br>
  <em>— Est. Club Cubana —</em>
</div>
