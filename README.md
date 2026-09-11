# What's Good Nearby? 🍯

A Winnie-the-Pooh-inspired food discovery directory for spots within 2 km of
Singapore postal code 550425. Pure HTML/CSS/JS, no build step, no backend.

## Deploy on Vercel

1. Push this repo to GitHub.
2. In Vercel: **New Project → Import** this GitHub repo.
3. Framework preset: **Other** (static site). Leave build command empty,
   output directory `.` (root) — `vercel.json` already sets this up.
4. Deploy. `index.html` is served at the root URL.

## Local preview

Just open `index.html` in a browser, or run a tiny static server:

```bash
npx serve .
```

## Connecting a real restaurant/places API

All sample data lives in the `<script id="restaurant-data" type="application/json">`
block inside `index.html`. The app loads it through the `fetchRestaurants()`
function near the top of the main `<script>` block — replace that function's
body with a real `fetch()` call to your API (Google Places, a delivery
platform, your own backend, etc.), keeping the same field names, and the rest
of the app (filtering, sorting, search, distance calculation) keeps working
unchanged.

Never put a secret API key directly in this client-side file — route calls
needing one through your own serverless function / backend instead (e.g. a
Vercel Serverless Function under `/api`).

## Notes

- Distances are calculated client-side with the Haversine formula from the
  550425 postal code centre point on every load — nothing is hardcoded.
- Restaurant data is a labelled **sample data** set sourced from real,
  publicly listed places; ratings are only shown where genuinely available.
