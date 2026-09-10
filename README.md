# sumantacs.github.io

Personal site for **Sumanta Das Bairagya** — Co-Founder & Head of Global Community at
[krako.xyz](https://krako.xyz). Live at **<https://sumantacs.github.io>**.

A deliberately dependency-free static site: no framework, no build step, no package
manager. The whole page is one hand-written HTML file with inline CSS, which keeps it
to a single request and means it cannot rot between deploys.

## Structure

| Path | Purpose |
| --- | --- |
| `index.html` | The entire site — markup, inline CSS, and a small progressive-enhancement script |
| `404.html` | Branded not-found page served by GitHub Pages |
| `portrait.jpg` | Hero portrait (400×400) |
| `og-card.png` | Social preview card (1200×630) for links shared on LinkedIn, X and Slack |
| `favicon.svg` | Monogram favicon |
| `apple-touch-icon.png` | Home-screen icon (180×180) |
| `robots.txt`, `sitemap.xml` | Crawler directives |

## Local preview

No install required — serve the directory with anything that speaks HTTP:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening `index.html` directly via `file://` also works, but the root-relative paths in
`404.html` will not resolve, so prefer the server.

## Deploying

GitHub Pages builds from the `main` branch. Pushing to `main` publishes; there is no
build step and no staging environment, so changes go live within about a minute.

## Conventions

- **CSS lives in `index.html`.** Design tokens are CSS custom properties on `:root`
  (`--navy`, `--steel`, `--paper`, `--rule`, …). Use the tokens rather than hard-coding
  hex values so the palette stays changeable in one place.
- **Type scale uses `clamp()`** so headings shrink fluidly instead of stepping at
  breakpoints. Breakpoints exist at 900px and 520px.
- **JavaScript is progressive enhancement only.** The Calendly booking links are real
  anchors that work with JS disabled; the popup widget is fetched on hover or first
  click rather than on page load.
- **Accessibility:** keep the skip link, the `:focus-visible` outlines, and the
  `prefers-reduced-motion` block intact when editing.

## Editing the social card

`og-card.png` is generated from the site's own palette and fonts, not hand-designed.
If the headline or role changes, regenerate the card at 1200×630 and keep the filename
so existing shared links keep resolving. Note that LinkedIn and X cache previews
aggressively — use their post inspector tools to force a refresh after a change.

## Licence

Code is MIT (see [`LICENSE`](LICENSE)). The portrait, the social card and the
biographical copy are all rights reserved.
