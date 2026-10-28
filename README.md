# adam-links

![version](https://img.shields.io/badge/version-1.1.0-8f2d1c) ![status](https://img.shields.io/badge/status-live-e48a6c) ![author](https://img.shields.io/badge/by-Adam--Blf-15160f)

Personal link-in-bio page for the Instagram account `@_adam_blf`, served at
https://links.beloucif.com.

- Single static `index.html`, no build step, no JavaScript, no cookies, no analytics.
- Fonts: Newsreader (display) and Geologica (text), OFL, subset and self-hosted in `fonts/` (no CDN).
- Profile photo in `img/`, Reicon arrow inlined as an SVG symbol.
- Light and dark themes from the system preference.

## Architecture

```mermaid
flowchart LR
  IG[Instagram bio link] --> DNS[links.beloucif.com<br/>CNAME at OVH]
  DNS --> V[Vercel static hosting]
  V --> P[index.html + fonts/ + img/]
  P --> L1[adam.beloucif.com]
  P --> L2[LinkedIn]
  P --> L3[GitHub]
  P --> L4[YouTube]
```

## Legal

Personal, non-professional site: LCEN art. 6 III 2 only requires the host identity,
shown in the footer. No data is collected, so no privacy policy or cookie banner.
Adding a form, analytics or a third-party embed reopens that question.

## Deploy

```bash
vercel deploy --prod
```

Releases are tagged `vX.Y.Z` from `CHANGELOG.md`.
