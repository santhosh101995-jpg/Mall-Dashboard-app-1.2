# M3M Mall Intelligence Dashboard

Vite + React app with embedded brand assets. Deploys to Vercel as a static SPA.

## Project structure

All source files are at the repository root (flat layout) so GitHub's web-based
folder upload won't cause issues:

```
.
├── index.html       — entry HTML; loads /main.jsx
├── main.jsx         — React mount point
├── App.jsx          — full dashboard (data, screens, brand assets embedded as base64)
├── package.json
├── package-lock.json (auto-generated on npm install)
├── vite.config.js
├── vercel.json      — SPA rewrites
├── .gitignore
└── README.md
```

## Local development

```bash
npm install
npm run dev
```

Open http://localhost:5173 .

## Production build

```bash
npm run build      # outputs to ./dist
npm run preview    # preview the production build locally
```

## Deploy to Vercel

### First time

1. Push this folder to a GitHub repo.
2. Go to https://vercel.com/new and import the repo.
3. Framework Preset: **Vite** (auto-detected).
4. Root Directory: `.`
5. Build Command: `npm run build`
6. Output Directory: `dist`
7. Click **Deploy**.

### Updating the dashboard

To replace just `App.jsx` (the most common case for data/UI updates):

1. Open the repo on github.com, click `App.jsx`.
2. Click the pencil icon, paste the new file contents, click **Commit changes**.
3. Vercel auto-redeploys within seconds.

## What's inside the dashboard

- Step 1: Property selection (6 M3M properties, each with its own embedded logo)
- Step 2: Property landing page (KPIs, governance watch, sales trajectory, category breakdown)
  - Includes a "View All Brands" directory entry point
- Step 3: Brand directory (searchable, with category-filter chips when in all-brands mode)
- Step 4: Brand detail (lease & commercial, contacts, performance, monthly chart)

Two navigation paths to brand-level stats:

- **Path A** (directory): Property → "View All Brands" → click brand → stats
- **Path B** (by category): Property → click category → brands in category → click brand → stats

## Embedded brand assets

To keep deployment simple (no `/public` folder, no separate image uploads), all
logos are embedded inside `App.jsx` as base64-encoded PNGs:

- M3M brand mark (in every header/footer)
- M3M Business Transformation logo (top-right of every header)
- 6 property logos (65th Avenue, Atrium 57, Broadway, Corner Walk, IFC, Paragon 57)

The production bundle is ~975 KB raw, ~390 KB gzipped (Vercel serves the
gzipped version). Logos make up roughly 250 KB of that.
