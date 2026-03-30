# 🥫 PantryTracker

A personal pantry and shopping management tool built as a single HTML file. No login, no backend, no installation — just open the file in your browser and start tracking.

---

## What It Does

PantryTrack helps you keep track of everything in your pantry, know what to buy, and never double-purchase something you already have. It cross-checks recipe ingredients against your current stock and tells you exactly what's missing.

---

## Tabs

### 🗄 Pantry
Your full inventory, grouped by category.

- Each item can have **multiple brand entries** with their own quantity, pack size, price, and expiry date
- The app auto-calculates **price per 100g / 100ml / piece** so you can compare brands at a glance
- Items with zero stock are **greyed out** — they're still in your pantry template but flagged as needing restocking
- Expanding an item shows all brand sub-entries with expiry status color-coding
- Items below their minimum stock threshold are flagged as **Low Stock**

**To add stock:** Tap an item → expand → *Add Brand/Stock*

**To consume something:** Tap the 🥄 icon on a brand entry. The app suggests the oldest stock first (by expiry date).

---

### 🛒 Shopping List
One unified list for all your grocery and household needs.

Items on the list have a **source tag** showing where they came from:
- `Manual` — you added it yourself
- `Low Stock` — auto-suggested because quantity hit the minimum threshold
- `Expiring` — auto-suggested because an item is nearing or past its expiry warning
- `Recipe` — added from the Recipe Checker, grouped under the dish name

**Checking off items:**
Tap the checkbox next to each item you've bought. Once you have checked items, a **Done Shopping** bar appears at the bottom. Tap it to log what you bought — enter brand, pack size, quantity, price, and expiry per item. The app then smart-merges everything into your pantry automatically.

**Auto-suggestions:**
Tap *Check for Low Stock & Expiring* to scan your pantry and add anything that needs restocking.

---

### 🍳 Recipe Checker
Cross-check any dish's ingredients against your pantry.

**How it works:**
1. Type the dish name and any notes (e.g. *"spicy, for 4 people"*)
2. Tap **Copy Prompt to Clipboard**
3. Paste the prompt into [Claude.ai](https://claude.ai) and copy the ingredient list it gives you
4. Paste the ingredient list back into the app
5. The app shows you:
   - ✅ **Have It** — in your pantry with sufficient stock
   - ⚠️ **Low Stock** — in your pantry but running low
   - ❌ **Need to Buy** — not in your pantry at all

Each low or missing item has an **Add** button to send it directly to your shopping list, grouped under the recipe name. You can also tap *Add All Missing* to add everything at once.

**Save recipes** you cook regularly using the 💾 Save Recipe button — they'll appear in your Saved Recipes list for quick reuse.

---

### 📋 History
A full in/out log of your pantry activity.

- **Purchases** — logged automatically when you complete a shopping session
- **Consumption** — logged whenever you consume something from the pantry
- Filter by type (All / Purchases / Consumed) or search by item or brand name
- Tap **Clear All History** to wipe the log (useful when clearing test data)

---

### ⚙️ Settings

**Categories** — Add, rename, or delete pantry categories. Categories with items cannot be deleted until items are moved or removed.

**Units** — Manage the unit dropdown used throughout the app (pcs, bottles, g, kg, ml, L, etc.). Add custom units as needed.

**Data Backup:**
- **Export JSON** — downloads a full backup of all your data as a `.json` file
- **Import JSON** — restores from a backup file (replaces all current data)

**Danger Zone:**
- **Clear All Data** — wipes everything and resets to default pantry template

---

## Backup & Restore

PantryTrack stores all data in your browser's `localStorage`. This means data is tied to the browser you use — clearing browser data or accidentally refreshing won't delete it on its own, but switching browsers or devices will show an empty pantry.

**Best practice:** Export a JSON backup after every shopping trip.

A **backup reminder banner** appears at the top of the app after 5 unsaved changes. You can dismiss it or tap *Export Now* directly from the banner.

**To restore after data loss:**
1. Open the app
2. Go to **Settings → Import JSON Backup**
3. Select your most recent `.json` backup file
4. All data is fully restored

---

## Price Comparison

When adding a brand entry, you provide:
- **Pack size** (e.g. `53`) + **Unit** (e.g. `g`)
- **Price per pack** (e.g. `₱45`)

The app calculates the normalized price automatically:
- Weight items → **₱ per 100g**
- Volume items → **₱ per 100ml**
- Countable items → **₱ per piece**

This lets you compare brands of different pack sizes fairly (e.g. 53g vs 100g vs 200g).

---

## Default Pantry Items

On first load, the app pre-loads a pantry template with common Filipino household staples (all greyed out — no stock yet):

Chicken, Eggs, Pork, Garlic, Onion, Rice, Cooking Oil, Soy Sauce, Vinegar, Fish Sauce (Patis)

You can edit, delete, or add to these freely from the Pantry tab.

---

## Hosting

The app is a single `.html` file with no dependencies or build step.

**To deploy on Vercel:**
1. Create a new project and upload `pantrytrack.html` as your only file
2. Rename it to `index.html` or set it as the entry point
3. Deploy — it works immediately

**To use locally:** Just open `pantrytrack.html` in any browser on your phone or desktop.

---

## Technical Notes

- All data is stored in `localStorage` under keys prefixed with `pt_`
- No API keys or external services are used inside the app
- The Recipe Checker uses a clipboard-to-Claude.ai flow — no AI API calls are embedded
- Designed for iPhone (mobile-first, light mode only)
- Single HTML file, no framework, no build tools required

---

*Built for personal use. PHP (₱) currency. Light mode only.*
