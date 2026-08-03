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
| `versions.html` | Lite / Single-State / Tri-State / Multi-State / Pro / Lien Releaser |
| `downloads.html` | Desktop installers for existing customers |
| `contact.html` | Demo request + contact details + phone hours |
| `privacy.html`, `terms.html` | Placeholders pointing at the policies in force; real text via Termly (#323) |
| `lien-writer-pro/`, `multi-state/`, `tri-state/`, `single-state/`, `lite-version/` | Per-version pages at the **legacy URLs**, one `index.html` each |
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
products). The three-way audit against the legacy site and Oscar's WordPress
build is ticket **#316**; its output lives in Drive at
`02 - Brand & Marketing/Website Redesign 2026/Website Content Audit - Three-Way - July 2026.md`.

Done:

- [x] **Property Research page — added, then removed.** See "Property
      Research: removed, to return" below. Do not re-add it from the audit.
- [x] **Per-version pages at the legacy URLs** — five of eight:
      `/lien-writer-pro/`, `/multi-state/`, `/tri-state/`, `/single-state/`,
      `/lite-version/`, as `<dir>/index.html`. Scope is described in
      desktop/FoxPro-parity terms, as the legacy pages do.
- [x] **Downloads page.** Points at the same `assets.fwmsoftware.com`
      installers the legacy page serves, so nothing breaks when that site
      retires.
- [x] **Privacy + terms URLs exist** as honest placeholders that link to the
      policies actually in force and say the update is coming. No invented
      legal text.
- [x] **Support hours published** site-wide (footer) and on the contact page:
      9–11 am and 2–5 pm PST. *Which hours are real still needs confirming —
      the legacy site says 8–5 (audit D2).*
- [x] **Founding-year claims made consistent** on 1991 ("Since 1991" rather
      than "For 30 years", which was wrong — 1991 to 2026 is 35 years).

Outstanding:

- [ ] **Remaining three legacy product URLs** — `/unit-usage/`,
      `/citrix-server/`, `/lien-releaser/`. Blocked on the retire-or-keep
      decision (audit D6); `/chexwriter/` is in the same bucket.
- [ ] **Real privacy + terms text** — generated and hosted by Termly (decision,
      2026-07-30), reconciled against the WP build's wording. Blocks Stripe
      live verification. Ticket #323, audit D4.
- [ ] **301 redirect map**, old URL → new URL, for everything that moved. The
      audit's page-by-page table is the input. Blocked on D6.
- [ ] **About page** — both other sites have a substantial feature narrative
      (Pettit form compatibility, USPS certified-mail Firm Log, the Tracker,
      Outlook calendar, scalability) that this build has no home for.
- [ ] **News/blog** — the WP build has three posts from Nov–Dec 2025 including
      a web-app announcement and a FoxPro-migration piece. Port or rewrite.
- [ ] **Self-serve scheduling** — the legacy contact page offers a Calendly
      link and a Google Form; this build offers a `mailto:` handoff, which
      fails silently on machines with no mail client configured.
- [ ] **Decide whether the marketing copy may promise mechanics liens and stop
      notices** for the *web app* — it has no mechanics-lien generator today
      (`docs/tier-entitlements.md`) and the live catalog is a CA-only Lite
      product. The per-version pages sidestep this by describing the desktop
      program; the home page feature grid does not. Audit D5.
- [ ] **Canadian coverage number.** Legacy and WP both say "11 Canadian
      Provinces" (not a valid count — Canada has 10 provinces + 3
      territories); this build says 13. Left alone pending the actual form
      inventory. Audit D3.
- [ ] Remove the `robots.txt` disallow and the preview banner; submit a sitemap.
- [ ] Verify fwmsoftware.com in Search Console *before* the DNS switch.
- [ ] Keyword research → copy/title/meta pass (ticket #318).
- [ ] **Get `fwmsoftware.operp.net` de-indexed or taken down.** It is live,
      set to `index, follow`, canonicalised to itself, and its terms ship an
      unfilled `[STATE]` placeholder. Two indexable FWM sites compete.

## Facts worth not re-deriving

- Founded **1991** (the legacy footer says so).
- Folsom, CA · (916) 237-7046 · support@fwmsoftware.com
- Jan Wheelock's testimonial says "over 20 years" — it is older than that now;
  worth asking her for a refreshed quote rather than editing her words.
- The X/Twitter link is a personal handle (`@Fmoore0001`) — confirm before
  promoting it as the company account.

## Property Research: removed, to return

Removed from this build on **2026-08-03** on Franklin's instruction: **FWM does
not currently offer property research reports.**

The #316 audit called its absence a P0 gap and shipped a page with `$12.00`/report
pricing and an order path, reasoning that the service was live revenue being
hidden because it appears on both older sites. That reasoning was wrong. It was
inferred from the legacy and WordPress sites rather than confirmed — audit
question **D1** asked exactly this and shipped unanswered. Treat it as a lesson
about the audit's method, not just a bad page: a page inferred from a competitor
or a predecessor site is not a confirmed offer.

What was removed: `property-research.html`, its main-nav link, its footer link on
every page, the home page's "Not sure who owns the job site?" section, and the
contact page's "Property research" row.

**Still live elsewhere and still orderable** as of 2026-08-03 — both need to come
down separately, neither is in this repo:

- `https://www.fwmsoftware.com/property-research/` (legacy Express app)
- `https://fwmsoftware.operp.net/property-research/` (Oscar's WP build)

### If it comes back

The intended shape is a free tier over public data plus a paid report when
deeper research is needed. Note for whoever builds it:

**The FoxPro program never sourced this data.** Every APN reference in
`lienwriter-foxpro` prints an APN the *user typed into the job record* onto a
notice or lien form — field 19, originally 16 characters, later widened to 64.
The legacy help text tells the user to go find it themselves, and treats it as
optional: "APN… If you have the Street address this number is not needed. But in
some cases such as new developments this is the only number you have." The $12
service was staff doing county assessor lookups by hand.

So there is nothing to port. A free tier means integrating county assessor and
parcel data directly — greenfield work, and its own scoping exercise.

Legacy URL `/property-research/` still needs a 301 destination in the redirect
map; it currently has purchase intent behind it and no page to land on.
