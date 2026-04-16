# Session 1 Plan — Style System + 6-Slide Proof of Concept

**Goal:** Lock the visual identity, the core component patterns, and a working 6-slide POC that proves the system scales to the full 39-slide deck.

---

## PRINCIPLES (stated at session start, per CLAUDE.md)

**Color palette (finalized below):** dark muted forest green (`#0A3B35`) as anchor, muted teal (`#14B8A6`) as primary accent, reserved mint (`#34EEA7`) for one "wow" moment per slide (count-ups, hero stat), warm off-white (`#F7F1E5`) for light slides, gold (`#F59E0B`) and coral (`#EF4444`) used sparingly.

**Font pairing:** **Sora** (Google, geometric sans with tabular figures — display + body + data) paired with **Fraunces** italic (Google, variable serif with optical sizing — quotes only). Sora carries 90% of the deck; Fraunces italic is the editorial voice for participant quotes. No Inter. No Roboto. No Arial.

**Anti-patterns I am actively avoiding:**
- Cards with colored left borders (the #1 AI-slop tell)
- Three identical cards in a row
- Purple/blue gradients, neon blue, bright saturated blue
- Generic icon-header-description rows
- Every slide sharing the same background
- Default Reveal.js themes
- Centered-everything layouts

**The rules (CLAUDE.md top-of-file):** plan first → viewport-fit content → no AI-slop → one focal point → no consecutive layout repetition → real phone frames → navigator works → PDF export works → state principles → checkpoint every 5 slides.

---

## REFERENCE DERIVATION (what I pulled from the A/B Testing readout PDF)

- Anchor background color: deep forest green, approximately `#0A3B35` (matches section-title slide bg)
- Accent 1: a luminous mint green used for big numerals (`#2BE9A5` in reference — I'm pulling this back toward `#34EEA7` → `#14B8A6` so it doesn't read neon)
- Accent 2: softer teal/aqua for body headlines on dark (`~#5FC8D2`) — I'm using `#5EEAD4`
- Footer pattern: BI X logo lower-left, page number lower-right, thin hairline divider above
- Section starter: huge numeral top-left (mint), section title lower-left (teal), deep forest bg
- Title slide: dark bg + large line-art overlapping "X" shapes as a watermark, teal stroke
- Content slide footer: hairline rule + BI X mark + page number
- Typography in reference: workhorse humanist sans (looks like Source Sans / BI corporate) — I'm replacing with Sora for more personality

---

## STYLE SYSTEM (design tokens)

### Color

```
--forest-deep:   #062823   /* deepest — for gradient extremes only */
--forest-base:   #0A3B35   /* PRIMARY DARK BACKGROUND */
--forest-mid:    #0F4A42   /* subtle depth, card surfaces on dark */
--forest-rim:    #1A5A50   /* hairline borders on dark */

--teal-500:      #14B8A6   /* primary accent — links, highlights, data */
--teal-400:      #2DD4BF   /* hover lift */
--teal-300:      #5EEAD4   /* soft headlines on dark */
--mint-accent:   #34EEA7   /* reserved — one "wow" moment per slide */

--gold:          #F59E0B   /* callouts, warnings (sparingly) */
--coral:         #EF4444   /* negative findings (sparingly) */
--success:       #10B981

--paper:         #F7F1E5   /* WARM off-white for light slides — editorial feel */
--paper-deep:    #EBE3D1   /* light slide depth */
--ink:           #0A1A1C   /* near-black on light */
--ink-mute:      #4A5558

--text-on-dark:  #F5F2EA
--text-dim-dark: #94A3B8   /* brief's specified muted sage/blue-gray */

--surface-glass: rgba(255,255,255,0.06)  /* semi-transparent cards */
--surface-glass-2: rgba(255,255,255,0.09)
```

### Typography

- **Display** — Sora 700, tight tracking (-0.02em), 72–96px on title/section-starters, 40–52px on content headlines
- **H2** — Sora 600, 28–32px, tracking -0.01em
- **Body** — Sora 400, 18–20px, line-height 1.55
- **Eyebrow/label** — Sora 500 uppercase, 12px, letter-spacing 0.16em
- **Metrics** — Sora 700 with `font-variant-numeric: tabular-nums`, 96–160px for hero numbers
- **Quote** — Fraunces italic (opsz variable), 32–44px, line-height 1.25
- **Caption / attribution** — Sora 500, 13px, uppercase letter-spacing 0.08em

### Spatial / scale

- Slide canvas: **1920 × 1080** (16:9), scaled via CSS transform to fit viewport
- Edge margin: 96px (≈5% of 1920)
- 12-col grid, 64px gutter
- Corner radius: 16px (cards), 28px (device), 8px (buttons/chips)

### Treatments (background library, to vary across deck)

- **Dark-Forest** (default content, dark): `#0A3B35` base with a low-opacity radial gradient centered off-slide for subtle depth + 4% noise overlay
- **Dark-X-Watermark** (title + section starters): forest base + large line-art overlapping "X" shapes SVG in `--forest-mid` stroke at 30% opacity
- **Paper-Editorial** (light): `#F7F1E5` base with 3% warm noise, thin forest hairline top divider
- **Paper-Tinted** (light with accent): paper base + large `--teal-300` shape at 12% opacity as pull-quote background
- **Data-Stage** (hero viz): dark forest with a soft mint-to-teal radial glow behind the primary chart

### Components (reusable)

- `SlideFrame` — handles background treatment, margins, footer (BIX mark + page # + "ONLY FOR INTERNAL USE")
- `Eyebrow` — uppercase label above headlines
- `Headline` — H1 treatment
- `StatNumber` — animated count-up with tabular figures
- `Quote` — Fraunces italic, oversized opening mark as decorative element (not a card, not a left border)
- `DovetailClipCard` — video-player-styled placeholder with play icon, participant ID, timestamp, quote
- `PhoneFrame` — iPhone Air CSS-only frame (Dynamic Island, squircle corners, bezel sheen, side hardware button hints, floating shadow)
- `SEQScaleChart` — horizontal bar w/ benchmark zone shaded, Chart.js
- `CitationChip` — small interactive pill ("P07", "6/7") with hover popover

### Animation philosophy

- Slide-enter: content staggers 80ms per element, fade + 12px rise
- Chart reveal: bars grow left-to-right over 900ms with ease-out-cubic
- Stat count-up: 1200ms ease-out, tabular figures
- Hover lift on interactive elements only: 1px translate-y + teal glow
- Slide transitions: horizontal slide + fade over 400ms
- NOT doing: parallax-per-slide, fade-on-every-text-block, spin/bounce, delay-content-behind-animation

---

## ARCHITECTURE

- **Framework:** single-file vanilla HTML + CSS + JS, Chart.js via CDN with integrity hash, Google Fonts via `<link>`. No build step for the POC. Slides are `<section class="slide">` elements toggled via JS. Keyboard nav + URL hash routing + `?print-pdf` → print stylesheet.
- **Why not Reveal.js for POC:** I want zero default-theme gravity; custom shell takes ~120 lines of JS and lets the visuals breathe.
- **Revisit for full 39-slide deck:** if component reuse gets unwieldy, port to React via web-artifacts-builder. Decide after POC review.
- **All assets base64-inlined** in the final HTML for single-file portability. Logo SVG inlined directly.
- **Slide navigator:** collapsible left panel (default open, ~240px), thumbnail-per-slide with section headers, current slide highlighted, click-to-jump, hidden in `@media print`.
- **Progress bar:** 2px hairline at top of slide canvas.
- **Nav controls:** back/next arrows outside the slide canvas, bottom-right.
- **PDF export:** print stylesheet renders each `.slide` as a page, `-webkit-print-color-adjust: exact`, animations resolve to final state, navigator and chrome hidden.

---

## THE 6 POC SLIDES

Layout/background rotation enforces no-consecutive-repetition (CLAUDE.md rule 5):

| # | Slide | Background | Layout | Focal |
|---|---|---|---|---|
| 1 | Title | Dark-X-Watermark | Full-bleed, headline bottom-left, BIX top-left, subtitle + footer | Headline + atmosphere |
| 2 | Executive Summary | Paper-Editorial (light) | Asymmetric: context ⅓ left, 3 findings as numbered typographic stack ⅔ right — **NOT cards** | Three findings as typography |
| 3 | Anchor Quote (P07) | Dark-Forest | Centered oversized serif pull quote, Fraunces italic, giant teal opening mark as decoration, Dovetail clip card offset bottom-right | The quote |
| 4 | SEQ Explainer (Hero Data Viz) | Data-Stage | Chart stage ⅔ right, explainer text ⅓ left, benchmark zone shaded, "6.4" count-up animated | The 6.4 |
| 5 | Photo Meal Logging | Paper-Tinted (light w/ teal wash) | Phone frame left-of-center, "6/7" hero stat upper-right, 2 quotes lower-right, Dovetail clip below frame | Phone + 6/7 stat |
| 6 | Finding 1 — Visual Differentiation | Dark-Forest | Phone frame left with radial callouts (thin line + dot + offset label), remediation typography right | Annotated phone |

**Rotation check:** Dark → Light → Dark → Dark(different treatment: Data-Stage with glow) → Light → Dark. No consecutive repeats. Slide 3 and 4 are both dark but visually distinct (quote vs. chart stage).

**Placeholder strategy for Session 1:** since real app screenshots aren't delivered yet, I'll use a CSS-drawn stylized mock of the home screen / calorie view in the phone frame for slides 5 and 6. The frame itself is the real deliverable — the "screen content" swaps to base64-inlined PNGs once uploaded.

---

## QUESTIONS BEFORE I BUILD

1. **Typography — confirm Sora + Fraunces italic.** Alternative on the table: Instrument Serif (display) + Sora (body) for a bolder editorial voice. My recommendation is **Sora + Fraunces italic quotes** — more restrained, lets the data carry distinctiveness. OK?

2. **Accent saturation.** The reference uses a vibrant mint (`~#2BE9A5`) prominently. The brief wants muted teal (`#0D9488`–`#14B8A6`) as primary. My plan: `#14B8A6` is the workhorse accent, `#34EEA7` mint reserved for one "wow" moment per slide (big numerals, hero count-up). OK, or do you want to pull mint back further?

3. **Warm paper white vs. cool white.** For light slides I'm proposing `#F7F1E5` (warm, editorial-journal feel) rather than pure `#FFFFFF`. Gives the deck an annual-report tone. Confirm?

4. **Phone frame — iPhone Air placeholder content.** Real screenshots not delivered yet. For the POC, slides 5 and 6 will render the phone frame with stylized CSS mockups of the screens (good enough to demonstrate frame fidelity and annotation positioning). We swap in real screenshots in the next session. OK?

5. **"X" watermark.** I'm building an SVG line-art overlapping-X pattern mirroring the reference title slide, in `--forest-mid` stroke. Do you have a specific BI X watermark SVG you'd prefer me to inline instead?

6. **Framework commitment.** Single-file vanilla HTML for POC, revisit React for full deck after your review. Agree?

7. **Slide 6 — annotation style.** I'm planning thin hairline connector lines from callout labels to problem areas on the screenshot (red-dot for ❌, teal-dot for ✅), labels offset outside the phone frame. Alternative: inline badges on the phone. Which do you prefer?

8. **Dovetail clip placeholders.** Styled as embedded video players with a faux thumbnail (dark forest with a waveform-like graphic), participant ID, timestamp, quote excerpt, circular play button. Sound right?

---

## ACCEPTANCE CRITERIA FOR SESSION 1

- [ ] Single HTML file opens locally with zero dependencies (fonts via Google CDN are acceptable)
- [ ] 6 slides render with no overflow, no overlap, no clipping
- [ ] Slide navigator present, collapsible, click-to-jump works
- [ ] Keyboard nav (← → space) works
- [ ] Progress bar reflects position
- [ ] SEQ chart animates on slide 4 entry
- [ ] "6.4" count-up animates on slide 4 entry
- [ ] Phone frame on slides 5–6 passes the "looks real" test
- [ ] `?print-pdf` renders cleanly, one slide per page, backgrounds preserved, navigator hidden, animations resolved to final state
- [ ] No consecutive slides share a background or layout
- [ ] None of the anti-patterns present
