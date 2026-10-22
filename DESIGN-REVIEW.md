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

---

## Update — v2 (2026-10-22)

**Key finding:** the green you saw is **Evergreen's own brand accent** (`#2E9E6B`, with a green-tinted bg) — not a design bug. Your school **TAOSD is gold** (`#c9a84c`). 567 of the accent usages already follow each school's color via `var(--gold)`; the real gap was interactive **tints** (hovers/focus glows) hardcoded to gold.

Changes in v2:
1. **Billing-type labels fixed** — the Memberships "Type" column no longer shows raw `ONE_TIME` / `RECURRING`. Now "One-Time", "Recurring", "Annual", etc. (plus a catch-all that title-cases any future value, so a raw enum can never leak again).
2. **Accent now fully brand-consistent** — added `--accent-rgb` (set from the school's color in `applyBrandColors`). Hovers, focus rings, input glows, scrollbar hovers now use the **school's accent**, not gold. So Evergreen = all green, TAOSD = all gold — one coherent accent per school.
3. **Card lift (depth)** — cards/panels now sit raised off the page with a subtle top highlight + layered shadow; stat cards lift further on hover.

Still open / deeper follow-up: ~45 hardcoded `#C9A84C` + ~74 gold-tint spots in the base CSS could be migrated to the accent var for 100% consistency (bigger pass); and portal/kiosk can get the same `--accent-rgb` tint treatment.
