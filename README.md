# ProxyPulse v2

Territory planner loaded from the **client-verified spreadsheet** (M10HH May 6 TTHG) instead of v1's inlined data.

Live: https://dditonto.github.io/proxypulse-v2/

## What's different from v1

- **Data source:** on load the app fetches `proxypulse_v2_data.json` (451 stores from the client xlsx) instead of the inlined `STORES_DATA` constant.
- **Territory model:** v2 stores list real suburb names with per-suburb `lat`/`lng`/`pop` in `suburb_details`. The app synthesizes a v1-compatible suburb map (one small square per suburb centroid, keyed by a unique code) so all existing features keep working: territory rendering, audience totals, Voronoi, sanity check, tier match, CSV export, and the AI agent.
- **Audience:** `calcStoreAudience` sums each store's `suburb_details` populations (households derived at ~2.5 people/household). Per-store totals match the spreadsheet exactly.
- **Buttons:** the primary button **↺ Reset to Client Data** restores the spreadsheet allocation (source of truth); **↻ Re-allocate Voronoi** runs the v1-style nearest-store allocation using suburb centroids.

## Files

- `index.html` — the app (v1 engine, v2 data loader)
- `proxypulse_v2_data.json` — 451 stores from the client spreadsheet
