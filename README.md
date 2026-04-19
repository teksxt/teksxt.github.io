# Teksxt — public website

Static site for Teksxt, hosted free on GitHub Pages.

**Live URL (after deploy):** https://teksxt.github.io/

## Structure

```
.
├── index.html               ← homepage
├── privacy.html             ← master privacy policy
├── terms.html               ← master terms of service
├── contact.html             ← contact / support
├── app-ads.txt              ← AdMob verification (edit with your publisher ID)
├── styles.css               ← shared stylesheet
└── apps/
    ├── flip-coin/
    │   ├── index.html
    │   ├── privacy.html     ← use this URL in Play Console for this app
    │   └── terms.html
    ├── 2048/
    │   ├── index.html
    │   ├── privacy.html
    │   └── terms.html
    └── sudoku/
        ├── index.html
        ├── privacy.html
        └── terms.html
```

## Before you push — customize these

1. **Email address** — replace `teksxt.apps@gmail.com` everywhere in `contact.html`
   with the email you actually want public.
2. **`app-ads.txt`** — replace `pub-XXXXXXXXXXXXXXXX` with your real AdMob
   publisher ID (find it in AdMob → Account → Account Information).
3. **Play Store developer link** — already set to your current link across all pages.
   Verify once that it's still correct:
   `https://play.google.com/store/apps/dev?id=7001677909210847797`
4. **App feature lists** — per-app `index.html` pages have generic feature lists.
   Edit them to match what each app actually does.

## Deploying to `teksxt.github.io`

1. Create a GitHub Organization called **`teksxt`** (free):
   https://github.com/organizations/plan → pick "Free" plan.
2. Inside that org, create a public repo named exactly **`teksxt.github.io`**.
3. Push every file in this folder to the repo's `main` branch.
4. Go to repo **Settings → Pages** → confirm source is `main` branch, `/` (root).
5. Wait ~1 minute. Visit **https://teksxt.github.io/** — it should be live.

## URLs to use in Play Console

After deploy, each app's Play Console listing should use:

| App | Privacy URL |
|---|---|
| Flip Coin & Dice | `https://teksxt.github.io/apps/flip-coin/privacy.html` |
| 2048 | `https://teksxt.github.io/apps/2048/privacy.html` |
| Sudoku | `https://teksxt.github.io/apps/sudoku/privacy.html` |

**Developer website field** (Play Console → Developer Account → Profile):
`https://teksxt.github.io`

**AdMob `app-ads.txt` location after deploy:**
`https://teksxt.github.io/app-ads.txt`

## Adding a new app later

Copy one of the existing app folders, rename it, edit the three files inside.
Then add a new `.app-card` block in `index.html` and a list item in both
`privacy.html` and `terms.html` under the "App-specific policies" section.

## Upgrading to a paid custom domain later

When you want to move to `teksxt.in` or `teksxt.app`:

1. Buy the domain at Cloudflare Registrar (cheapest, no upsells).
2. Add a `CNAME` file at the repo root containing just `teksxt.in`.
3. In repo Settings → Pages, set the custom domain to `teksxt.in` and enable "Enforce HTTPS".
4. At Cloudflare DNS, add four A records pointing to GitHub's IPs:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   and a CNAME for `www` pointing to `teksxt.github.io`.
5. Update Play Console + AdMob with the new domain. Re-verify `app-ads.txt`.

No code changes needed — all internal links are relative.
