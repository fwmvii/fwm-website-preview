# fwmsoftware.com — the 2026 marketing site

The new FWM Software marketing site: a small, dependency-free static build
(hand-written HTML + one stylesheet) in the Harbor & Coral design system.

**Lien Writer is a web application.** The desktop program is no longer sold
(Franklin, 2026-08-03). This site markets the hosted product only; the version
names (Lite / Single-State / Tri-State / Multi-State / Pro) are web
subscription tiers, enforced server-side — see `docs/tier-entitlements.md` in
the app repo. `downloads.html` survives purely as a reinstall archive for
existing desktop licence holders and retires with the legacy site.

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
| `privacy.html`, `cookies.html`, `terms.html` | Termly-hosted legal documents, embedded (see "Legal documents" below) |
| `lien-writer-pro/`, `multi-state/`, `tri-state/`, `single-state/`, `lite-version/` | Per-version pages at the **legacy URLs**, one `index.html` each |
| `styles.css` | The whole design system: tokens, type scale, components |
| `robots.txt` | Blocks indexing **while this is a preview** — remove at launch |
| `_redirects` | Cloudflare Pages 301 map, legacy URL → new URL (Pages only; GitHub Pages ignores it) |
| `_headers` | Cloudflare Pages response headers — CSP, nosniff, frame-ancestors, asset caching |

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
- [x] **Privacy, cookie, and terms pages are real** — the three Termly
      documents, embedded on our own URLs. See "Legal documents" below.
- [x] **Support hours published** site-wide (footer) and on the contact page:
      9–11 am and 2–5 pm PST. *Which hours are real still needs confirming —
      the legacy site says 8–5 (audit D2).*
- [x] **Founding-year claims made consistent** on 1991 ("Since 1991" rather
      than "For 30 years", which was wrong — 1991 to 2026 is 35 years).

Outstanding:

- [ ] **Remaining three legacy product URLs** — `/unit-usage/`,
      `/citrix-server/`, `/lien-releaser/`. Blocked on the retire-or-keep
      decision (audit D6); `/chexwriter/` is in the same bucket.
- [ ] **Attorney read of two clauses** before these documents are relied on:
      the industry-specific compliance clause (the not-a-law-firm / no-warranty
      -that-a-document-perfects-a-lien language) and the custom
      customer-data/export/migration clauses. Danielle. Ticket #323, audit D4.
- [x] **301 redirect map** — `_redirects`. Every legacy URL in audit §1 resolves
      to a live target; the five per-version paths need no redirect because this
      build serves them unchanged. `/property-research/` points at home as a
      placeholder — **still needs a real destination decision**.
- [ ] **About page** — both other sites have a substantial feature narrative
      (Pettit form compatibility, USPS certified-mail Firm Log, the Tracker,
      Outlook calendar, scalability) that this build has no home for.
- [ ] **News/blog** — the WP build has three posts from Nov–Dec 2025 including
      a web-app announcement and a FoxPro-migration piece. Port or rewrite.
- [ ] **Self-serve scheduling** — the legacy contact page offers a Calendly
      link and a Google Form; this build offers a `mailto:` handoff, which
      fails silently on machines with no mail client configured.
- [x] **Mechanics-lien claim scoped honestly (audit D5).** The home page feature
      grid now carries "Mechanics liens — Rolling out" rather than presenting a
      generator that does not exist, and stop notices (which *do* generate) got
      their own tile. The per-version pages no longer defer to the desktop
      program. **Open:** `docs/tier-entitlements.md` says the full Stripe
      catalog "isn't built yet" and current subscribers are all on one
      CA-only Lite product — the site now markets five tiers, so Long needs to
      set `metadata.tier` on the catalog products before launch or the pages
      describe something unpurchasable.
- [x] **Canadian coverage number removed rather than guessed (audit D3).** The
      compliance block's "13" tile is now "35 years of maintained forms"; prose
      says "the Canadian provinces and territories" with no count. The real
      number still needs the form inventory before any count is published.
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

## Web-only: what changed 2026-08-03

Decision (Franklin): **only the web application is offered.** The desktop
program is not sold; `downloads.html` is a reinstall archive that retires with
the legacy site. Full catalog on the new site — all five tiers.

Rewritten accordingly:

- **Home page rebuilt**, 586 → 1,172 words. It was the thinnest page on the
  site; the five per-version pages carried 2,246 words between them, so the
  positioning document weighed less than a tier detail page. Added the tier
  catalog and a "why it belongs in the browser" section (no install, forms never
  stale, real backups, multi-user, migration path, same people answering).
- **"Desktop and web" callout removed from all five version pages.** Five
  identical apologetic caveats explaining that version names described *desktop*
  licensing was the clearest symptom of the old framing.
- **Mechanics liens tagged "Rolling out"** instead of claimed outright, and stop
  notices split into their own tile — they generate, mechanics liens do not.
- **Hero and compliance copy** now lead with the browser: nothing to install,
  statutory changes reach customers the day we ship.

Still desktop-framed on purpose: `downloads.html`, and the home page's
"Moving from the desktop program?" tile — both are migration surface, not
product marketing.

## Cloudflare Pages

Deploy method: **Pages + Git integration** (Franklin, 2026-08-03). Connect
`FWM-Software/website` in the Cloudflare dashboard — no build command, output
directory `/`, production branch `main`. `_redirects` and `_headers` are picked
up automatically.

**Do not point fwmsoftware.com DNS at it yet.** `fwmsoftware.operp.net` is
still indexable, so `robots.txt` and the per-page `noindex` stay until that is
resolved — the first Pages deploy is safe to make public at its `*.pages.dev`
address without competing with the live site.

## Legal documents

`privacy.html`, `cookies.html` and `terms.html` are thin wrappers around
documents that live with **Termly**, embedded via Termly's `embed-policy.min.js`
snippet with the policy UUID in `data-id`:

| Page | Termly policy UUID |
| --- | --- |
| `privacy.html` | `a763f257-50fe-4db6-9d3b-6227de47f232` |
| `cookies.html` | `5aa3544d-4f5d-4b71-b18f-a898c1949ab6` |
| `terms.html` | `67f2991c-abfc-4042-8968-21e446254c15` |

Two rules follow from that, and breaking either causes the failure this design
exists to prevent:

1. **Never paste the policy text into these files.** Edits made in Termly
   propagate to the embed automatically; a pasted copy silently becomes a
   second, differently-worded version of the same document.
2. **The embed is the only third-party script on the site**, which is why
   `_headers` allows `app.termly.io` in `script-src`, `frame-src` and
   `connect-src`. If the embed ever goes away, take those allowances back out.

Each page also carries a direct link to Termly's hosted viewer, for anyone
whose browser blocks the frame, and a `<noscript>` version of the same.

Content written by us rather than Termly: the trademark notice at the bottom of
`terms.html` (carried over from the legacy site's mis-titled "Terms of Use"
page, which was really a trademark statement of use) and the short callouts on
the privacy and cookie pages.

Not yet in place: **a cookie consent banner.** Termly sells one, and it is a
separate script. The site currently sets no advertising or analytics cookies —
the only third-party request is Google Fonts — so a banner is not yet doing any
work. It becomes required the moment analytics or ad pixels are added, which
is likely as soon as SEO work starts (#318).
