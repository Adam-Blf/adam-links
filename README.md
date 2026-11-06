# adam-links

<!-- adam-badges:start -->
[![version](https://img.shields.io/badge/version-1.1.0-163767?style=flat-square)](CHANGELOG.md)
[![commits](https://img.shields.io/github/commit-activity/t/Adam-Blf/adam-links?color=001329&label=commits&style=flat-square)](https://github.com/Adam-Blf/adam-links/commits)
[![visites](https://hits.sh/github.com/Adam-Blf/adam-links.svg?style=flat-square&label=visites&color=001329)](https://hits.sh/github.com/Adam-Blf/adam-links/)
[![last commit](https://img.shields.io/github/last-commit/Adam-Blf/adam-links?color=D4A437&style=flat-square&label=dernier%20push)](https://github.com/Adam-Blf/adam-links/commits)
[![top language](https://img.shields.io/github/languages/top/Adam-Blf/adam-links?style=flat-square)](https://github.com/Adam-Blf/adam-links)
[![license](https://img.shields.io/github/license/Adam-Blf/adam-links?style=flat-square&color=D4A437)](LICENSE)
<!-- adam-badges:end -->

Personal link-in-bio page for the Instagram account `@_adam_blf`, served at
https://links.beloucif.com.

- Single static `index.html`, no build step, no JavaScript, no cookies, no analytics.
- Fonts: Newsreader (display) and Geologica (text), OFL, subset and self-hosted in `fonts/` (no CDN).
- Profile photo in `img/`, Reicon arrow inlined as an SVG symbol.
- Light and dark themes from the system preference.

## Architecture

```mermaid
flowchart LR
  IG["Instagram bio link"] --> DNS["links.beloucif.com<br/>CNAME at OVH"]
  DNS --> V["Vercel static hosting"]
  V --> P["index.html"]
  A[("fonts/ + img/<br/>self-hosted assets")] --> P
  P --> L1["adam.beloucif.com"]
  P --> L2["LinkedIn"]
  P --> L3["GitHub"]
  P --> L4["YouTube"]

  classDef input fill:#2563eb,stroke:#1e3a8a,color:#fff
  classDef process fill:#7c3aed,stroke:#4c1d95,color:#fff
  classDef store fill:#f59e0b,stroke:#92400e,color:#111
  classDef ok fill:#16a34a,stroke:#14532d,color:#fff
  classDef error fill:#dc2626,stroke:#7f1d1d,color:#fff
  class IG input
  class DNS,V,P process
  class A store
  class L1,L2,L3,L4 ok
```

## Legal

Personal, non-professional site: LCEN art. 6 III 2 only requires the host identity,
shown in the footer. No data is collected, so no privacy policy or cookie banner.
Adding a form, analytics or a third-party embed reopens that question.

## Deploy

```bash
vercel deploy --prod
```

Releases are tagged `vX.Y.Z`. The version lives in `VERSION`; pushing a tag runs
`.github/workflows/release.yml`, which checks the tag against `VERSION`, takes the
notes from `CHANGELOG.md` and attaches a zip of the static site.

## Licence

Code (`index.html`) under the MIT licence, see [LICENSE](LICENSE). The profile photo
in `img/` is not covered and stays all rights reserved. Fonts in `fonts/` keep their
own SIL Open Font License.
