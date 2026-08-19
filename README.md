# Dandela Site

Marketing / product landing page for **Dandela**, a personal AI knowledge graph
that captures notes and articles, connects them, and answers your questions with
grounded, cited answers.

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

Content is lifted from the app itself (`Dandela-kg`) so the page stays accurate
rather than generic. The landing page is content-led — there is one call to
action on the whole page (the email link), because email is the only real action
the site supports today.

Sections, in order:

1. **Hero** — positioning, plus a worked example of an ask → grounded answer with
   citations (in place of a second dead-end button)
2. **How it works** — Capture → Connect → Ask, with the real ingestion pipeline
   strip and source status states
3. **Knowledge model** — sources, chunks, entities, relationships, decisions,
   events, projects, mentions; entity and relationship types as chips
4. **Sources** — text notes and URLs today, PDF and images next
5. **Retrieval** — hybrid search (Postgres FTS + pgvector cosine), graph
   expansion, grounded answers, provider-agnostic AI; chunk/embedding specs
6. **Security** — RLS-scoped data, citations, your choice of AI provider
7. **Contact** — a single email address

If the app changes, update these sections rather than adding new CTAs.

## Stack

No framework, no dependencies, no build step. Inter + Plus Jakarta Sans loaded
from Google Fonts, everything else is hand-rolled CSS custom properties in
`theme.css`.