# dpp4you — Landing Page

Marketing site for **dpp4you**: beautiful, multilingual Digital Product Passports (DPP)
that turn EU ESPR compliance into a premium brand touchpoint.

Single-file site (`index.html`) — no build step. Open it in a browser or deploy the
folder as-is to any static host (Cloudflare Pages, Netlify, GitHub Pages…).

---

## Redesign rationale (what changed, and why)

This document explains every deliberate decision behind the current version of the page.

### 1. The cryptography section was removed

The previous version dedicated a full section (and one of the three value pillars) to an
interactive "cryptographic signature" sandbox, with hash outputs and tamper demos.
It was removed for marketing reasons:

- **Wrong audience, wrong moment.** A landing page sells the *outcome* (a passport your
  customers love to open). Cryptographic internals are a procurement/technical due-diligence
  topic — they belong in a sales call or a security whitepaper, not above the fold.
- **Claim hygiene.** Advertising "mathematically tamperproof" data invites scrutiny and
  legal/technical objections we don't need on a first-touch page. Understating beats
  overstating.
- **Message focus.** Removing it leaves three crisp pillars: brand portfolio, direct
  customer channel, multilingual coverage. Trust is still communicated — subtly — through
  the "Verified authentic · ESPR aligned" badge in the demos, without making promises we
  have to footnote.

### 2. A multilingual section was added

New dedicated section: **"One passport. Every European language."**

- **It's a real differentiator.** The EU has 24 official languages; a DPP that only speaks
  English is a compliance checkbox, not a customer touchpoint. Competitors rarely lead with
  this, so we do.
- **It's demonstrated, not just claimed.** The section includes a live preview: tapping a
  language chip (EN, IT, FR, DE, ES, PT, NL, PL, SV, DA) instantly re-renders a sample
  passport in that language, with a paper-flip micro-animation. The remaining 14 languages
  are listed as covered on every plan.
- **Zero-effort framing.** Copy stresses automatic device-language detection and editorial
  overrides — the prospect understands "it just works, and I keep control of my brand voice."

### 3. Paper-morphic design system

The visual language was rebuilt around a **paper / card-stock aesthetic**, with cards
modeled on [beyondtag-webapp](https://beyondtag-webapp.pages.dev/) (our sibling product),
so the brand family feels cohesive.

Why paper-morphism:

- **Metaphor fit.** A "passport" is a paper document. Rendering the UI as stacked sheets
  of card stock makes the product concept instantly tangible — the page itself demonstrates
  the product.
- **Brand fit.** Warm, tactile, crafted — it signals sustainability and artisan care, which
  is exactly the audience (premium European brands facing ESPR) responds to. It also stands
  apart from the generic glassmorphism/dark-mode look of every other SaaS compliance tool.
- **Interaction fit.** The signature behavior — a hard offset shadow (like a sheet resting
  on a desk), cards that *lift* on hover and *press flat* on click — gives the whole page a
  physical, satisfying feel.

Core tokens (see `tailwind.config` and the `<style>` block in `index.html`):

| Token | Value | Use |
|---|---|---|
| `paper` | `#f2ece0` | page background (with a faint 24px graph-paper grid) |
| `paper-deep` | `#e7ded0` | recessed areas, phone frames |
| `paper-card` | `#faf8f5` | raised card stock |
| edge | `rgba(139,128,107,.35)` | warm 1.5px card borders |
| hard shadow | `rgba(90,80,60,.15)` | offset "stacked paper" shadow |
| `ink` | `#2d2b27` | primary text |
| `terra` | `#c36237` | primary accent (terracotta) |
| `inde` | `#3273a6` | secondary accent (indigo) |
| `leaf` | `#3c8a5a` | success / eco accent |

Typography: **Outfit** for headings, **Inter** for body — same pairing as BeyondTag.
Recurring motifs: dashed "tear-line" dividers (perforated-paper edge), a gradient ink rule
under section headings, and a slight rotation on featured cards (paper-cutout charm).

### 4. Overall design & functionality upgrades

Beyond the two requested content changes, the page was professionalized end to end:

- **Real navigation.** Sticky blurred-paper header with anchor links (Why us / Live demo /
  Languages / Templates), a primary CTA, and a working mobile hamburger menu (the old page
  had only a logo placeholder and a button).
- **Brand identity.** The `[Logo Placeholder]` box was replaced with a proper wordmark
  (`dpp4you` + QR glyph) used consistently in header and footer.
- **"How it works" section.** Three numbered steps (Connect data → Design → Publish & scan)
  that answer the buyer's first practical question and shorten the path to the contact form.
- **Scroll-reveal animations** via `IntersectionObserver`, with a `prefers-reduced-motion`
  fallback for accessibility.
- **Kept what worked.** The interactive smartphone simulator (compliance vs. portfolio vs.
  customer-loop views) and the template gallery were retained — they're the strongest
  sales tools on the page — and restyled into the paper system. The simulator's footer now
  reads "Verified authentic · ESPR aligned" instead of the removed crypto hash.
- **SEO & polish.** Descriptive `<title>` and meta description, semantic sections with ids,
  a real multi-column footer with contact links, dynamic copyright year, paper-styled
  scrollbar and focus states.
- **Copy tightening.** Headlines now speak outcomes ("pressed on fine paper", "why comply
  when you can captivate?") and every section ends in a clear next step toward `#contact`.

---

## Page structure

1. **Hero** — value proposition + paper phone mockup + trust strip (ESPR ready · 24 languages · bespoke themes)
2. **Why us** — three pillars: Brand Portfolio / Direct-to-Owner / Multilingual
3. **Live demo** — interactive smartphone simulator (3 switchable passport modules)
4. **Languages** — live multilingual preview with 10 tappable languages, all 24 covered
5. **How it works** — 3-step onboarding
6. **Templates** — 3 themes + bespoke studio card
7. **Contact** — consultation pitch + inquiry form (mock submission with success state)
8. **Footer** — brand, explore links, contact

## Tech stack

- **Tailwind CSS** via CDN with an inline custom theme (paper palette)
- **Lucide** icons via CDN
- **Google Fonts**: Outfit + Inter
- Vanilla JS: tab simulator, language switcher, mobile menu, scroll reveal, form mock

No dependencies to install, no bundler — edit `index.html` and refresh.
