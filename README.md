# NAVTEC Expeditions — Landing Pages (navtec-lps)

Standalone PPC landing pages for NAVTEC Expeditions (navtec.com), one per Google
Ads ad group, all deployed together via a single GitHub Pages site + one
subdomain CNAME. Each ad group gets its own folder/path rather than its own
subdomain, so we only manage one DNS record as the repo grows.

## Live structure
- `/` — redirects to `/4x4/` until more ad group pages exist
- `/4x4/` — 4x4 / National Park Tours (Canyonlands & Arches) ad group landing page
- `/rafting/` — (planned) Colorado River Rafting ad group
- `/canyoneering/` — (planned) Canyoneering ad group
- `/combo/` — (planned) Land + River combo ad group

To add a new ad group LP: create a new top-level folder (e.g. `/rafting/index.html`
+ `/rafting/assets/`), following the same pattern as `/4x4/`.

## Local assets needed before launch (per LP)
Drop into that LP's `assets/` folder and confirm the `<img src>` paths match:
- `4x4/assets/`: island-in-the-sky.jpg, arches-4x4.jpg, needles-district.jpg, full-day-combo.jpg

## Deployment
1. Push to `main` branch.
2. In repo Settings → Pages, set source to `main` / root.
3. Add a `CNAME` file at the repo root containing the subdomain (e.g. `lps.navtec.com`).
4. On the client's DNS host, add a CNAME record: `lps` → `<github-username>.github.io`.
5. In GitHub repo Settings → Pages, enter the same custom domain and enable
   "Enforce HTTPS" once DNS propagates.
6. Point each ad group's Google Ads final URL at its own path, e.g.
   `https://lps.navtec.com/4x4/?utm_source=google&utm_medium=cpc&utm_campaign=...`

## Lead form
Each LP's form posts to a Zapier webhook (see `ZAPIER_WEBHOOK_URL` in the
`<script>` tag near the bottom of its index.html) with hidden UTM/click-ID
attribution fields.

