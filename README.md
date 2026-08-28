# MDV WIP Builder — Menswear

Single-file web app that builds per-supplier Work-In-Progress Excel charts from the
Menswear Critical Path + live Airtable PO Lines data.

## Deploy (GitHub → Vercel)
1. Put `index.html` at the **root** of this repository (this is the file Vercel serves).
2. Commit to the branch Vercel deploys from (usually `main`).
3. Vercel auto-builds; when it shows **Ready**, the live URL is updated.
4. Hard-refresh the app in your browser (Cmd+Shift+R / Ctrl+Shift+R) to clear cache.

No build step or dependencies — it's a static file.

## What this version pulls
- **Airtable:** Gender = **Men's** or **Unisex** (exact match on the Gender field).
- **Critical Path:** every style with a supplier + SKU (no TP-date requirement).

## New columns in this format
- **TIERED PRICING** (col H) — supplier-filled, carried over week to week.
- **PRODUCT TIER** (col AN) — pulled from the CP column "Product Tier".

## Notes
- This is the Menswear build. The Womenswear build is identical except it pulls
  Gender = Women's + Unisex. Keep them as two separate repos/projects.
