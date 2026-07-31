# fwmsoftware.com — the 2026 marketing site

The new FWM Software marketing site: a small, dependency-free static build
(hand-written HTML + one stylesheet) in the Harbor & Coral design system.

**Not live yet.** fwmsoftware.com still serves the legacy site from
[`fwmsoftware-website`](https://github.com/FWM-Software/fwmsoftware-website)
(an Express app, last touched Aug 2024). This repo replaces it at launch.

## Why static

Decided on the 2026-07-23 Franklin/Long call, and reaffirmed after checking:
Google does not care about the platform, so the hosting choice is SEO-neutral.
A static build means nothing to patch, fast loads, hosting anywhere
(Cloudflare was Long's suggestion for the CDN), and edits made by Claude
rather than through a CMS. The tradeoff is that non-developers cannot
self-serve edits — accepted, because the legacy site's content sat untouched
from 2018 to 2026.

## What's here

| File | Purpose |
| --- | --- |
| `index.html` | Home — positioning, product surface, the Tracker, testimonials, compliance |
| `versions.html` | Lite / Single-State / Tri-State / Multi-State / Pro |
| `contact.html` | Demo request + contact details |
| `styles.css` | The whole design system: tokens, type scale, components |
| `robots.txt` | Blocks indexing **while this is a preview** — remove at launch |

No build step, no dependencies, no framework. Open `index.html` in a browser.

## Preview

Served by GitHub Pages from a personal fork, so the org repo needn't be a
Pages source: **https://fwmvii.github.io/fwm-website-preview/**

Every page carries a "Preview build — not our live site yet" banner and
`noindex, nofollow`. Both come off at launch (see the checklist).

To update the preview: push to this repo, then push the same commits to the
`preview` remote (`git push preview main`).

## Design system

Harbor & Coral: Sand `#FAF5EC`, Deep Harbor `#0E3E44`, Harbor Teal `#127C74`,
Coral `#F0654A` (accent only), Outfit for type, 10px radii. No gradients, no
stock photography, no hype. Approved tagline: "The fastest way from pending to
paid." The phrase "we help you get paid" is banned.

Source package: Drive → `02 - Brand & Marketing/Website Redesign 2026/`.

## Launch checklist

Tracked as tickets in `FWM-Software/lienwriter` (one board covers both
products).

- [ ] **Per-version pages at the legacy URLs.** The legacy site had eight
      indexable product pages (`/lien-writer-pro/`, `/multi-state/`,
      `/tri-state/`, `/single-state/`, `/lite-version/`, `/unit-usage/`,
      `/citrix-server/`, `/lien-releaser/`); this build collapses them into a
      single Versions page. Collapsing loses eight keyword-specific landing
      pages, so rebuild them at the same paths.
- [ ] **Privacy + terms pages** — generated and hosted by Termly (decision,
      2026-07-30). Blocks Stripe live verification. Ticket #323.
- [ ] **301 redirect map**, old URL → new URL, for everything that moved.
- [ ] **Downloads page** — legacy installers still live on the old site and
      existing desktop customers depend on them. They need a new home before
      the old site retires.
- [ ] Remove the `robots.txt` disallow and the preview banner; submit a sitemap.
- [ ] Verify fwmsoftware.com in Search Console *before* the DNS switch.
- [ ] Keyword research → copy/title/meta pass (ticket #318).
- [ ] Decide the fate of the ChexWriter / Unit Usage / Citrix Server / Lien
      Releaser content (audit ticket #316).

## Facts worth not re-deriving

- Founded **1991** (the legacy footer says so).
- Folsom, CA · (916) 237-7046 · support@fwmsoftware.com
- Jan Wheelock's testimonial says "over 20 years" — it is older than that now;
  worth asking her for a refreshed quote rather than editing her words.
- The X/Twitter link is a personal handle (`@Fmoore0001`) — confirm before
  promoting it as the company account.
