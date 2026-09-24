# Redvanly ecommerce diagnostic (CreditSwan preview)

A static, single-page report. No build step and no dependencies: just `index.html`. Fonts load from Google Fonts.

## Files

| File | Purpose |
|---|---|
| `index.html` | The full report, with all CSS and JavaScript inline |
| `favicon.svg` | CreditSwan swan mark |
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

## Editing

Numbers in the planner live in the `CH` array and the `REV0`, `OTHER_MKT`, `FIXED`, `NEW0`, `EMAIL0` and `AOV` constants near the bottom of `index.html`. Static narrative figures are in the HTML above them.
