# vasmikstudio.com

Landing page for Vasmik Studio. A one-page static site built with
[Hugo](https://gohugo.io/) (Apache-2.0). No theme, no JavaScript, no web fonts,
no trackers — just one HTML page with inlined CSS.

## Layout

```
hugo.toml             site config; optional contact email in [params]
content/_index.md     the page text
layouts/baseof.html   HTML shell (head, footer)
layouts/home.html     home page
layouts/404.html      not-found page
assets/css/main.css   styles, minified and inlined into each page
static/favicon.svg    favicon
```

## Contact line

The home page shows a contact line only when `params.email` is set in
`hugo.toml` (currently unset).

## Develop

Requires Hugo 0.158 or newer (uses the `locale` config key). On Windows:
`winget install Hugo.Hugo`.

```
hugo server            # http://localhost:1313, live reload
```

## Build

```
hugo --gc --minify --panicOnWarning
```

The site is written to `public/`. `--panicOnWarning` makes any warning
(e.g. a deprecated config key) fail the build.

## Deploy

Hosted on GitHub Pages from the `vasmikstudio/vasmikstudio.github.io` repository.
Every push to `master` runs `.github/workflows/pages.yml`, which builds the site
with a pinned Hugo version and publishes `public/`. Bump `HUGO_VERSION` there
when upgrading Hugo locally.

Custom domain `vasmikstudio.com` is set in the repository's Pages settings
(not via a CNAME file — not needed for Actions-based deploys).

DNS at GoDaddy:

| Type  | Name | Value                     |
|-------|------|---------------------------|
| A     | @    | 185.199.108.153           |
| A     | @    | 185.199.109.153           |
| A     | @    | 185.199.110.153           |
| A     | @    | 185.199.111.153           |
| AAAA  | @    | 2606:50c0:8000::153       |
| AAAA  | @    | 2606:50c0:8001::153       |
| AAAA  | @    | 2606:50c0:8002::153       |
| AAAA  | @    | 2606:50c0:8003::153       |
| CNAME | www  | vasmikstudio.github.io    |
