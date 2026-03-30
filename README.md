# 🌿 PantryTrack

A personal home inventory and shopping manager — built as a single, self-contained HTML file. No backend, no database, no dependencies to install. Designed for solo living, mobile-first use.

---

## What It Does

PantryTrack combines a weekly shopping checklist, a monthly household run tracker, a pantry inventory with expiry tracking, and a spending summary — all in one file.

**Shop tab** — Weekly grocery checklist pre-loaded with common Filipino household staples (eggs, chicken, pork, monggo, rice, soy sauce, vinegar, etc.). Check off items as you shop, adjust quantities, add notes per item, and flag items as running low so they auto-carry to next week's list.

**Household tab** — Monthly household run for laundry, bath & body, cleaning supplies, and personal care items. Activates with a highlighted banner on the first Friday of each month.

**Pantry tab** — Inventory tracker for items at home. Each entry stores name, brand, size, category, quantity on hand, low-stock threshold, expiry date, date purchased, store, and price paid. Color-coded expiry tags (green / orange / red) give an immediate visual of what needs attention.

**Summary tab** — Monthly spend total, trip count, average per trip, all-time spend, and full trip history. Also contains the Backup & Restore tool.

---

## Key Features

- **Smart auto-add** — On every open, items in your pantry that are expiring within 7 days or below their low-stock threshold are automatically surfaced in the Shop tab with an alert banner.
- **Master list persistence** — "Done Shopping" resets your checklist but preserves all custom items, edits, and deletions you've made. Your list evolves with your actual shopping habits.
- **Low-flag carry-over** — Items flagged as running low remain checked/flagged after a trip reset so you don't forget them next week.
- **Edit everything** — Shop items, household items, and pantry entries all have full edit support via modal forms, not browser prompts.
- **Export & Import** — One-tap JSON export for backup. Re-import on any device or after a browser cache clear to restore all your data.
- **No internet required after load** — All data lives in `localStorage` on your device. The only external dependency is a Google Fonts stylesheet loaded on first open.

---

## Stack

| Layer | What's used |
|---|---|
| UI | Vanilla HTML + CSS + JavaScript (no frameworks) |
| Fonts | Playfair Display + DM Sans via Google Fonts |
| Storage | Browser `localStorage` |
| Hosting | Static file — works on Vercel, GitHub Pages, or opened directly |

---

## Deploying to Vercel

This is a single static HTML file. Vercel treats it as a static site with zero configuration needed.

**Step 1 — Set up the repo**

```
pantrytrack/
├── index.html       ← rename PantryTrack.html to this
└── README.md
```

Rename `PantryTrack.html` to `index.html` so Vercel serves it at the root URL.

**Step 2 — Push to GitHub**

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/pantrytrack.git
git push -u origin main
```

**Step 3 — Deploy on Vercel**

1. Go to [vercel.com](https://vercel.com) and log in.
2. Click **Add New Project** → Import your GitHub repo.
3. Vercel will auto-detect it as a static site. No build settings needed — leave everything as default.
4. Click **Deploy**.

Your app will be live at `https://pantrytrack-YOUR_USERNAME.vercel.app` (or your custom domain if configured).

**Step 4 — Save to your iPhone home screen**

1. Open the Vercel URL in Safari on your iPhone.
2. Tap the Share icon → **Add to Home Screen**.
3. Name it "PantryTrack" and tap Add.

It will appear and behave like a native app icon. All data is stored locally on your phone.

---

## Data & Storage Notes

- All data is stored in your browser's `localStorage` under the key `pantrytrack_v3`.
- Data persists between sessions as long as you use the **same browser** on the **same device**.
- Data is **not synced** across devices. Use the Export → Import flow in the Summary tab to move data between devices or browsers.
- Clearing browser site data will erase your data. Export a backup regularly.

---

## Updating the App

To update PantryTrack after making changes to `index.html`:

```bash
git add index.html
git commit -m "Update: describe your change"
git push
```

Vercel will automatically redeploy on every push to `main`. Your localStorage data on your phone is unaffected by app updates.

---

## Customizing Your Lists

The default grocery and household items are defined at the top of the `<script>` block in `index.html` as `DEFAULT_SHOP` and `DEFAULT_HH` arrays. You can edit these directly to match your actual recurring purchases before your first deploy — changing names, brands, prices, and categories to fit your household.

After your first use, any edits made through the app UI are saved to your master list and will persist across weekly resets without touching the code.

---

## License

Personal use. Built for solo living in Manila. 🇵🇭
