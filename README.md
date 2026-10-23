# Wholethread site

Static website for the Wholethread Chrome extension: landing page, privacy policy, support. Plain HTML and one CSS file. No build step, no JavaScript, no external requests.

## Layout

- `index.html`, `support/index.html`, `privacy/index.html`, `404.html`
- `style.css`, `icons/`, `favicon-16.png`, `favicon-48.png`, `favicon.ico`, `og.png`
- `llms.txt`, `a9d49930f7405a7eb80ac2722f73bdde.txt` (IndexNow key file)
- `robots.txt`, `sitemap.xml`, `.nojekyll`
- `CNAME` (holds `wholethread.org`)

## Canonical domain

The canonical domain is `https://wholethread.org`. It appears in canonical, Open Graph, Twitter and JSON-LD URLs in each page, in `sitemap.xml` and in `robots.txt`. To change it, search and replace `https://wholethread.org` across the site, and update `CNAME` / `CNAME.pending`.

## Publish order

Do not make the repository public before the domain is registered. In this order:

1. Buy `wholethread.org`.
2. Create the public GitHub repository and push this directory to the `main` branch.
3. Repository Settings, Pages: source "Deploy from a branch", branch `main`, folder `/ (root)`.
4. `git mv CNAME.pending CNAME` and push. `CNAME.pending` holds `wholethread.org`; it is deliberately not named `CNAME` until the domain is owned, because a `CNAME` pointing at an unowned domain breaks Pages.
5. Configure DNS: `A` records for the apex to GitHub Pages (185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153) and a `CNAME` record for `www` to `<user>.github.io`. Check GitHub's current documentation for the addresses.
6. In Settings, Pages, enter the custom domain, wait for the certificate, then enable "Enforce HTTPS" and check that `https://wholethread.org/` loads.

The absolute canonical URLs point at `wholethread.org`, so the `github.io` copy should not be submitted to search engines.

## Search engines

1. Google Search Console: add `https://wholethread.org` as a property, verify via DNS TXT, submit `https://wholethread.org/sitemap.xml`.
2. Bing Webmaster Tools: add the site (or import it from Search Console), submit the same sitemap.
3. IndexNow: generate a key, publish `<key>.txt` containing the key at the site root (the key file is `a9d49930f7405a7eb80ac2722f73bdde.txt`), then submit changed URLs to `https://api.indexnow.org/indexnow`. Resubmit after each content change.

## Release checklist

- Copy the extension's `PRIVACY.md` into `privacy/index.html` (keep the "This website" section at the end) and update the "Last updated" date.
- Update `lastmod` in `sitemap.xml` for changed pages.
- Check that every product claim on the site still matches the extension.
- Resubmit changed URLs through IndexNow.

## When features become paid

The site says every feature is free during launch, in two places on the home
page ("Is Wholethread free?" and the FAQ's cost answer), and the JSON-LD
`offers.price` is `0`. All three change the day the locking version is
published, together with the Store listing's "Free during launch" paragraph.
