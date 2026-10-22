# NMAO — Staging Design Pass (for review)

**Everything here is STAGING ONLY.** The live app (app.nmao.us) is untouched. This repo has no CNAME and is never wired to the live domain. Every change is a single reversible `<style id="nmao-design-pass">` block appended at the end of each file — delete that block to return to baseline.

## A/B compare (log in with demo-staff@nmao.us / NmaoDemo!2027, Evergreen)

| Surface | New design | Original (baseline) |
|---|---|---|
| Owner dashboard | /dashboard.html | /dashboard-baseline.html |
| Member portal | /portal.html | /portal-baseline.html |
| Kiosk | /kiosk.html | /kiosk-baseline.html |

Base URL: `https://nmao1.github.io/NMAO-Membership-Staging/`

## What changed — Dashboard
1. **Type system (biggest change):** everyday UI text now uses a clean modern sans (**Inter**); the **brand/headline font (your Settings → font choice) is reserved for headlines** — logo, page titles, panel titles, big dollar numbers. This fixes the "serif everywhere = dated" feel and matches how the member portal already worked. Numbers use tabular figures so columns align like a ledger.
2. **Elevation:** cards/panels/modals get softer borders + subtle depth (instead of hard 1px lines). Stat cards lift on hover.
3. **Nav:** rounded hover pills, calmer section labels.
4. **Buttons:** consistent shape, subtle lift on hover, keyboard focus rings.
5. **Inputs:** softer idle borders + a gold focus ring.
6. **Tables:** more row height, hover rows, quieter gridlines, uppercase column headers.
7. **Badges/chips:** unified pill shape.
8. **Premium thin scrollbars** + smoother transitions.

## What changed — Portal + Kiosk
Lighter polish only (they already use a sans body): elevation on cards, gold focus rings, button lift, thin scrollbars.

## How it respects your brand settings
- The **school's font** (Settings → font) now drives **headlines**; everyday text is the fixed clean sans. (We'd relabel that setting "Brand / headline font".)
- The **school's accent color** still drives all gold accents, focus rings, hovers.
- **Green (#5A9A6A) left untouched** — it's your "success" color (checkmarks, active, paid). Used correctly; not changed.

## Open discussion (not changed — your call)
- **Green vs gold balance:** green nav icons compete a little with the gold brand. I left it alone because green = success is correct. If you want ONE accent identity, we can nudge structural greens toward neutral/gold and keep green strictly for success.

## To revert any surface
Delete its `<style id="nmao-design-pass">` block (or just use the `-baseline.html` file). Nothing here can reach production.
