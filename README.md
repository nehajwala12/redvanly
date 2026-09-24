# Redvanly ecommerce diagnostic (CreditSwan preview)

A static, single-page report. No build step and no dependencies: just `index.html`. Fonts load from Google Fonts.

## Files

| File | Purpose |
|---|---|
| `index.html` | The full report, with all CSS and JavaScript inline |
| `favicon.svg`, `favicon.png` | Official CreditSwan swan mark (cream on ink) |
| `vercel.json` | Clean URLs and `noindex` headers so search engines skip the page |
| `robots.txt` | Also asks crawlers to skip the site |

## Preview locally

Open `index.html` in a browser, or run:

```bash
npx serve .
```

## Deploy: GitHub + Vercel

1. Create a new GitHub repository, private is recommended, e.g. `redvanly-diagnostic`.
2. Push this folder:
   ```bash
   git init
   git add .
   git commit -m "Redvanly diagnostic preview"
   git branch -M main
   git remote add origin https://github.com/<your-org>/redvanly-diagnostic.git
   git push -u origin main
   ```
3. In Vercel, choose **Add New → Project**, import the repo, and keep these settings:
   - Framework preset: **Other**
   - Build command: leave empty
   - Output directory: leave empty, which uses the repo root
4. Click **Deploy**. Every later push to `main` redeploys automatically.

Optional: add a custom domain such as `redvanly.creditswan.ai` under **Project → Settings → Domains**.

## Deploy without GitHub

```bash
npm i -g vercel
vercel        # first run links the project
vercel --prod
```

## Note on access

The page is public to anyone with the URL. It is excluded from search engines but is not password-protected. For access control, use Vercel's Deployment Protection (Pro plan) or ask for the encrypted-gate version.

## Editing the numbers

All inputs live in one JSON block near the bottom of `index.html`: `<script id="data" type="application/json">`. It holds the call figures (`company`), the P&L lines (`pnl`), the channel parameters (`channels`), the recommended budget (`plan.budget`) and the chart series.

Change a value there and every dependent figure updates on load: KPI tiles, the narrative numbers, the P&L table, the charts, the channel scorecard and the spend planner. Narrative figures are `<span data-k="...">` elements filled from the model.
