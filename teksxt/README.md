# Teksxt — public website

Static site for Teksxt, hosted free on GitHub Pages.

**Live URL (after deploy):** https://teksxt.github.io/

**Contact email:** teksxt71@gmail.com

## Structure

```
.
├── index.html               ← homepage
├── privacy.html             ← ONE privacy policy, covers all apps
├── terms.html               ← ONE terms of service, covers all apps
├── contact.html             ← contact / support
├── app-ads.txt              ← AdMob verification (edit with your publisher ID)
├── styles.css               ← shared stylesheet
└── apps/
    ├── flip-coin/index.html ← app landing page (links to master privacy/terms)
    ├── 2048/index.html
    └── sudoku/index.html
```

**Why one privacy policy?** All current Teksxt apps share the same data
practices: no direct data collection, AdMob ads, Play Services, local
storage only. Google Play allows a single shared privacy URL as long as it
accurately covers every app. This is what most small indie studios do.

**When to split into per-app policies?** Only if a future app has
meaningfully different practices — for example an app that collects user
accounts, uses camera/location, or targets children specifically. When that
happens, you can add `apps/<slug>/privacy.html` just for that app and link
it from the master policy.

## Before you push — one thing to customize

**`app-ads.txt`** — replace `pub-XXXXXXXXXXXXXXXX` with your real AdMob
publisher ID (find it in AdMob → Account → Account Information).

Everything else is already wired up with `teksxt71@gmail.com`.

## Deploying to `teksxt.github.io`

1. Create a GitHub Organization called **`teksxt`** (free):
   https://github.com/organizations/plan → pick "Free" plan.
2. Inside that org, create a public repo named exactly **`teksxt.github.io`**.
3. Upload every file in this folder to the repo's `main` branch.
   Easiest way: on the new repo page, click "uploading an existing file",
   drag everything in, commit.
4. Go to repo **Settings → Pages** → confirm source is `main` branch, `/` (root).
5. Wait ~1 minute. Visit **https://teksxt.github.io/** — it should be live.

## URLs to use in Play Console

All apps use the **same** URLs:

| Field | URL |
|---|---|
| Privacy policy (all apps) | `https://teksxt.github.io/privacy.html` |
| Developer website | `https://teksxt.github.io` |
| `app-ads.txt` location | `https://teksxt.github.io/app-ads.txt` |

Paste the privacy URL into every app's Play Console listing. You can also
link the per-app pages from your listing descriptions if you want deep
links, e.g. `https://teksxt.github.io/apps/2048/`.

## Adding a new app later

1. Copy one of the existing app folders (e.g. `apps/2048/`), rename it.
2. Edit the single `index.html` inside — title, tagline, feature list.
3. Add a new `.app-card` block in the root `index.html`.
4. If the new app shares the same data practices, no privacy changes needed.
5. If the new app has different data practices (collects accounts, uses
   camera, etc.), create `apps/<slug>/privacy.html` and link it from the
   master `privacy.html` under a new "app-specific policies" section.

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
