# MDV WIP Builder — Menswear (Airtable-only)

Single-file web app that builds per-supplier WIP Excel charts **live from Airtable** —
the Critical Path upload has been retired.

## Deploy (GitHub → Vercel)
1. Put `index.html` at the **root** of the repo (Vercel serves it).
2. Commit to the deploy branch (usually `main`); Vercel auto-builds.
3. Hard-refresh (Cmd/Ctrl+Shift+R) after it shows **Ready**.

## What it pulls
- **Colourways** where **Sampling Division ≠ Womenswear** (division read from the Colourway's Sampling Division; Men's, Unisex and untagged all appear — anomalies surface, never silently drop).
- **PO lines** that are **live** — no booking (Shipment) reference (this alone drops shipped/booked lines), and status is not **Cancelled, Delivered or Arrived**. All other statuses (Draft, PO Sent, Confirmed, Awaiting Shipment, On Hold, Shipped, Part-Shipped, etc.) are kept — the booking reference decides those.

## What appears / is excluded
- **New Release** = a colourway with no PO yet (Product Status not Approved/Cancelled),
  or a live **✨Newness** PO. **Restock** = live **🔁Repeat** PO. **Mix** = **🤩Mix** PO.
- Excluded: Approved-with-no-PO; Cancelled-with-no-PO; any PO with a booking reference;
  Cancelled PO/line status; Sampling Division = Womenswear.
- A **Cancelled colourway that still has a live PO** keeps showing the PO (surfaces the clash).

## Notes
- Supplier name comes from the Colourway's Airtable value, so New Releases and restocks
  for one factory share a name and land in one file.
- No API key is stored server-side; it lives in your browser only.
