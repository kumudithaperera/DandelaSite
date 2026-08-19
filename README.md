# Dandela Site

Marketing / product landing page for **Dandela · Publish Now**, a one-tap app
that publishes a photo or video to your Facebook Page, Instagram Business, and
TikTok accounts.

A plain static site (HTML + CSS + vanilla JS, no build step). Deploys straight
to GitHub Pages.

## Deploy to GitHub Pages

1. **Create a repo** for this site, e.g. `dandela-site`, or use the
   `gh-pages` branch of an existing repo.

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin git@github.com:<you>/<repo>.git
   git push -u origin main
   ```

2. **Enable Pages.** On GitHub: **Settings → Pages → Source → Deploy from a
   branch** → select `main` and the `/ (root)` folder → **Save**.

3. The site is served at `https://<you>.github.io/<repo>/`.

> If you want the site at `https://<you>.github.io/` (a user/org site), name
> the repo exactly `<you>.github.io`.

## Custom domain (optional)

Add a `CNAME` file containing your domain (e.g. `dandela.dev`) and point a DNS
`CNAME` record at `<you>.github.io`. Or configure it under
**Settings → Pages → Custom domain** (GitHub writes the `CNAME` for you).

## Local preview

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

Or open `index.html` directly in a browser.

## Pages

- `index.html` — landing page
- `privacy.html` — privacy policy
- `terms.html` — terms & conditions

## Brand theme

`theme.css` is the single source of truth for the brand: colors, fonts, shape,
and shadows. `styles.css` consumes those tokens only, so to rebrand the site
just edit `theme.css`.

The theme follows the **Dandela Brand & UI direction**:

- Palette: deep navy (`#172554`), trust blue (`#2563EB`), soft sky (`#DBEAFE`),
  warm white (`#F8FAFC`), white surfaces
- Type: **Inter** for UI, **Plus Jakarta Sans** for display headings
- Style: calm, trustworthy, professional. No gradients, restrained rounding,
  light shadows

## Content

Content is lifted from the app's own README so the page stays accurate:

- Three-step flow: **Pick a file → Stage it → Publish**
- Supported platforms: Facebook Page, Instagram Business, TikTok
- Limits: photos ≤ 20 MB (HEIC converted in-browser), H.264 video ≤ 500 MB
- Security: pgsodium-encrypted tokens at rest, private Supabase Storage bucket
  with signed URLs, staging objects deleted after every attempt

## Stack

No framework, no dependencies, no build step. Inter + Plus Jakarta Sans loaded
from Google Fonts, everything else is hand-rolled CSS custom properties in
`theme.css`.