# Session 5 Plan — Build Slides 1–15

**Goal:** Expand the 6-slide POC into the first 15 blueprint slides, holding the quality bar set in sessions 1–4.

Writing this plan in chunks to stay under the timeout ceiling. Chunk 1 below; chunks 2–4 follow in subsequent edits.

---

## CHUNK 1 — PRINCIPLES (restated per CLAUDE.md)

**Palette (locked from sessions 1–4):**
- `--forest-base: #0A3B35` (primary dark), `--forest-deep: #062823`, `--forest-mid: #0F4A42`
- `--teal-500: #14B8A6` (workhorse accent), `--teal-300: #5EEAD4` (soft headlines)
- `--mint-accent: #34EEA7` (reserved "wow" moment per slide)
- `--paper: #F7F1E5` (warm editorial), `--paper-deep: #EBE3D1`
- `--gold: #F59E0B`, `--coral: #EF4444` (sparingly)
- `--ink: #0A1A1C`, `--ink-mute: #4A5558`

**Type:** Sora (display + body + data, tabular nums) / Fraunces italic (quotes only). No Inter, Roboto, Arial.

**Anti-patterns I am explicitly avoiding:**
- Cards with left colored borders (the #1 AI-slop tell)
- Three identical cards in a row
- Purple gradients, neon blue, BI-X bright blue
- Generic icon-header-description rows
- Consecutive slides sharing background or layout
- Jargon on slide surfaces ("CSS fix," etc.) — business-stakeholder vocabulary only
- Static stat pills that look clickable but aren't — every pill is a chip trigger
- Popovers extending beyond `#canvas.getBoundingClientRect()`

**Standing rules brought forward (sessions 1–4):**
1. Content fits the viewport; restructure or split if it doesn't.
2. One focal point per slide.
3. No two consecutive slides share layout OR background.
4. Phone frames look real (bezels, Dynamic Island, hardware hints).
5. Navigator collapsible, visible by default, works.
6. PDF export works and is tested.
7. Type calibrated for rendered size — ≥14px labels, 17–19px body at 1920 native.
8. Every visible pill/badge = chip trigger; popovers deliver NEW info from `spine.md`, never repeat slide content.
9. Headlines pass the "would a principal investigator say this?" test.
10. Composite viz: sketch vertical bands before placing pieces; no shared strips.
11. Slide canvas is sacred; popovers clamp inside canvas bounds.
12. Interactive expansions reserve space — no layout jump.
13. Distribution = `index.html` + `assets/videos/` only. Images base64-inlined. Videos loaded via relative `<video src>` with graceful fallback to styled placeholder.
14. Checkpoint every 5 slides against all rules.

---

## CHUNK 2 — SLIDE MAPPING (POC → blueprint 1–15)

The POC had 6 slides. Four map cleanly into slides 1–15; two (SEQ, Finding 1) belong to slides 21 and 25 — OUT of this session's range.

| POC | Blueprint | Status for this session |
|---|---|---|
| s1 Title | **Slide 1** Title | KEEP, minor footer tweak to "01 / 15" during build, full page-of-N when deck is complete |
| s2 Executive Summary | **Slide 6** | KEEP, renumber footer to 06 |
| s3 Anchor Quote P07 | **Slide 7** | KEEP, renumber footer to 07 |
| s4 SEQ hero viz | Slide 21 | **DEFER** — move to end of file, swap class to `.slide-deferred` so it's excluded from the deck this session. Re-inserts at position 21 in session 6. |
| s5 Photo Meal Logging | **Slide 14** | KEEP, renumber footer to 14 |
| s6 Finding 1 Visual Diff | Slide 25 | **DEFER** — same treatment as s4 |

**New slides to build this session (11):** 2, 3, 4, 5, 8, 9, 10, 11, 12, 13, 15.

**Final slide order in the file after this session:**
1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9 → 10 → 11 → 12 → 13 → 14 → 15 → [deferred: old-s4, old-s6]

**SLIDES array (nav metadata) gets rewritten with 15 entries, grouped into 4 sections:**
- Front Matter (1–4)
- Executive Summary (5–7)
- Study Design & Participant Profile (8–11)
- What Resonated with Users (12–15) — continues into session 6 (slides 16–19)

Navigator will NOT show the deferred slides. They live in the DOM under `.slide-deferred` so their CSS survives for session 6.

---

## CHUNK 3a — PER-SLIDE PLAN (slides 1–8)

**Background/layout rotation is enforced — no consecutive repeats.**

### Slide 1 · Title (KEEP from POC)
- **Bg:** Dark-X-Watermark. **Layout:** full-bleed, BIX top-left, headline mid-left, meta bottom.
- **No changes** other than page footer "01 / 15".

### Slide 2 · Meet the Team (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** horizontal team row, not cards.
- **Focal:** 4–5 team members as circular headshot placeholders with role/name, connected by a thin hairline rule. Kyle center-emphasized (lead researcher). Above the row: eyebrow "The Team" + one-line mission. Below: a sparse, editorial credit caption.
- **Placeholder strategy:** CSS gradient circles w/ monogram initials until real headshots land in `/assets/team/`. Each circle has `data-headshot="kyle"` etc. so swapping is a one-line change.
- **Chips:** none (this slide is introductory; no citations needed).
- **Variety:** light bg, horizontal composition, editorial — contrasts with dark title slide before and dark Agenda after.

### Slide 3 · Agenda (NEW)
- **Bg:** Dark-Forest (not watermark). **Layout:** oversized numerals 01–06 stacked vertical-left, section titles in Sora 600 right-aligned to the numerals on a strict baseline grid — NOT a bulleted list.
- **Focal:** the typographic hierarchy of the six sections.
- **Detail:** each line has eyebrow section label in muted teal + section title in white. Section 3 ("What Resonated") gets a subtle mint underline — the one "wow" moment per slide, foreshadowing the persuasion core.
- **Chips:** none.
- **Variety:** dark, typographic-grid composition — different from s1 (watermark-led) and s4 (data-led) coming next.

### Slide 4 · What Is This App? (NEW)
- **Bg:** Dark-Forest + subtle mint glow offset right. **Layout:** asymmetric — left ⅗ is a prose description + 4 value-prop callouts as typographic lines (NOT icon+card+description rows); right ⅖ is an iPhone Air frame showing the Home/Wellness Score screen (placeholder CSS mock, real screenshot to swap).
- **Focal:** the phone + the one-sentence product thesis above it.
- **Value props as editorial typography:** each is a big numeral (01–04) + short noun phrase + one-line amplification, stacked vertical, NOT boxed. E.g. `01 / Medication tracking · body-map injection log with rotation history`.
- **Chips:** `[live AI]` → popover explaining PWA + live AI vs Figma click-through.
- **Variety:** dark asymmetric-with-device — different from the typographic agenda and the section-starter that follows.

### Slide 5 · Section Starter — Executive Summary (NEW)
- **Bg:** Dark-X-Watermark (reused from title, INTENTIONAL recurrence for section starters per BI reference). **Layout:** matches BI reference — giant mint numeral "01" top-left, section title bottom-left in teal, forest base with low-opacity X pattern.
- **Focal:** the "01" numeral.
- **Content:** Eyebrow `Section 01`. Title `Executive Summary`. Subtitle one-liner: `Seven patients. Six tasks. A clear verdict.`
- **Variety:** this is a hero punctuation slide; contrasts with the dense content slides bracketing it.

### Slide 6 · Executive Summary (KEEP from POC, renumber)
- Unchanged other than footer "06 / 15" and shifting the eyebrow from "01 · Executive Summary" to match new numbering.

### Slide 7 · Anchor Quote P07 (KEEP from POC, renumber)
- Unchanged other than footer "07 / 15" and eyebrow label.

### Slide 8 · Section Starter — Study Design & Participant Profile (NEW)
- **Bg:** Dark-X-Watermark — **mirrored** X pattern vs. slide 5 so they feel related but not identical, plus a different numeral treatment.
- **Content:** `02` numeral, `Study Design & Participant Profile` title, subtitle `Seven GLP-1 patients. One day in the life of the app.`
- **Variety:** consistent section-starter cadence but mirrored composition ≠ s5.

---

## CHUNK 3b — PER-SLIDE PLAN (slides 9–15)

### Slide 9 · Study Design Overview (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** two-band composition — top ⅔ is a labelled lab-setup photo frame (placeholder: styled browser-frame-style card with "Dovetail overhead camera · Session in progress" caption); bottom ⅓ is a 2-column editorial spec sheet (Methodology | Prototype) rendered as a numbered typographic list, NOT cards.
- **Focal:** the photo placeholder.
- **Detail:** Methodology list items (moderated testing · lab facility · 60-min sessions · think-aloud · SEQ · post-session questionnaire · Rainbow Grid observation · Dovetail recording). Prototype list items (Lovable-built PWA iOS · live AI · "Jennifer" simulated patient · fully interactive, not clickthrough).
- **Chips:** `[SEQ]` → popover "Single Ease Question, 7-pt scale; industry mean 5.5 across 10k+ users." `[Rainbow Grid]` → brief explanation of the 50+ observable schema.
- **Placeholder:** lab-setup photo → CSS treatment with "Dovetail" chrome, video-player styling, swap to real screenshot later. `data-asset="lab-overhead"`.
- **Variety:** light, photo-forward — contrasts dark section starter before, dense table after.

### Slide 10 · Participant Profile (NEW)
- **Bg:** Dark-Forest. **Layout:** 7-row participant table left ⅔ (ID · Age · Gender · Medication · Duration · Tech Comfort), sidebar right ⅓ with stacked callouts.
- **Focal:** the table. Each row gets a mini-avatar (gradient circle with monogram), and each P-ID is a chip trigger → popover with spine-sourced profile (current app, tech moment, quote).
- **Table styling:** no borders — hairline dividers only; tabular-nums for numeric cols; "Tech Comfort" column rendered as a 7-dot bar (filled dots = self-rating) so P07's 5/7 is visually distinct from 7/7's immediately. No left colored borders — rows are pure typography + the dot viz.
- **Sidebar callouts (typographic, stacked):**
  - `6 F · 1 M` — target demographic
  - `Age 36 – 61` (median ~49)
  - `GLP-1 duration: 2 mo – 1 yr`
  - `All had prior health-app experience`
  - `Target segment represented by` [P05] [P07] — chips
- **Variety:** dark data-forward — contrasts paper before, data viz after.

### Slide 11 · Task Flow (NEW — hero viz for this section)
- **Bg:** Data-Stage (dark forest + soft mint radial glow behind the arc). **Layout:** full-width horizontal day-arc from ☀️ → 🌙 with 6 task nodes spaced along it; each node has task #, label, SEQ score badge. Benchmark zone shaded as a horizontal band the arc crosses over.
- **Focal:** the arc. Each node reveals on slide entry (80ms stagger). T4 node (AI Coach, 5.4) visually flagged in gold (not red — it still clears benchmark).
- **Detail:** above arc — eyebrow `One simulated day · Six tasks`. Below arc — single-line caption `All six tasks above industry benchmark (5.5). T4 reflects discoverability, not interaction quality.`
- **Chips:** each task node is clickable → popover with task full name, completion rate (full/partial/fail), and one representative quote from spine.
- **Variety:** data-stage dark with glow — distinct from dark-forest table before and paper exec summary after.

### Slide 12 · Section Starter — What Resonated with Users (NEW)
- **Bg:** Dark-X-Watermark, third rotation — different numeral color (teal-300 instead of mint) to vary from s5 and s8 while keeping the family language.
- **Content:** `03` numeral, `What Resonated with Users` title, subtitle `The persuasion core. Validated wins, in participants' own words.`

### Slide 13 · Feature Validation Overview (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** feature × participant heat-matrix. 6 feature rows × 7 participant cols. Cells: ✅ (teal-500 fill), ⚠️ (gold fill), ❌ (coral fill), — (dim gray). Column headers are P-ID chip triggers (reuse s10 popovers).
- **Focal:** the matrix. Cells are clickable → popover with the participant-feature moment from spine (e.g. `P01 · Evening Reflections · "I hate this."` followed by "... I actually like the app though.").
- **Detail:** below matrix, single typographic callout `Core features validated across all participants. Variation in Reflections is by design — it's a segment feature.`
- **Styling:** NO left colored borders. Rows are typography + hairline dividers + colored glyphs. Interactive cells have subtle hover lift.
- **Variety:** light interactive matrix — contrasts dark section starter and breakout-feature slide after.

### Slide 14 · Photo Meal Logging (KEEP from POC, renumber)
- Unchanged other than footer "14 / 15" and eyebrow.

### Slide 15 · Body Map Injection Tracker (NEW)
- **Bg:** Dark-Forest (NOT paper — rotation rule; s14 was paper-tinted). **Layout:** phone frame left-of-center showing the Body Map screen (placeholder CSS anatomical mock: torso silhouette with a 7-zone grid, the "today" zone highlighted teal, "recent" zones marked, "suggested" zone ringed in mint); right side has the hero stat + two quotes + insight.
- **Focal:** the body map inside the phone frame.
- **Hero stat:** `7/7 · positive` large, tabular; secondary `6.7 / 7 mean usefulness`; tertiary `No competitor offers this combination`.
- **Quotes:** P02 "This is a lot better because the app that I use only tracks my infusions." · P05 "I like that it tells you where your last one was because in [my app] I actually have to go back and look."
- **Dovetail clip card:** P02 @ 15:46 (placeholder, swap to real video later).
- **Chips:** `[P02]` `[P05]` → profile popovers. `[7/7]` → per-participant breakdown.
- **Variety:** dark phone-left, stat-right — different composition from s14 (also phone-left but paper-tinted and different right-side layout).

---

## CHUNK 4 — BACKGROUND/LAYOUT ROTATION CHECK

| # | Slide | Bg family | Layout family |
|---|---|---|---|
| 1 | Title | Dark-X-Watermark | Full-bleed title |
| 2 | Meet the Team | Paper-Editorial | Horizontal team row |
| 3 | Agenda | Dark-Forest | Typographic numeral grid |
| 4 | What Is This App? | Dark + mint glow | Asymmetric text + phone |
| 5 | Section Starter · Exec Summary | Dark-X-Watermark | Section starter (hero numeral) |
| 6 | Executive Summary | Paper-Editorial | Asymmetric 3-finding stack |
| 7 | Anchor Quote | Dark-Forest | Centered pull quote |
| 8 | Section Starter · Study Design | Dark-X-Watermark (mirrored) | Section starter |
| 9 | Study Design Overview | Paper-Editorial | Photo top · spec-sheet bottom |
| 10 | Participant Profile | Dark-Forest | Table left + sidebar right |
| 11 | Task Flow | Data-Stage (dark + glow) | Horizontal arc |
| 12 | Section Starter · What Resonated | Dark-X-Watermark (3rd) | Section starter |
| 13 | Feature Validation Overview | Paper-Editorial | Interactive heat matrix |
| 14 | Photo Meal Logging | Paper-Tinted | Phone-left · stat+quotes-right |
| 15 | Body Map Tracker | Dark-Forest | Phone-left · stat+quotes-right |

**No consecutive repeats of bg family OR layout family.** Section starters (5, 8, 12) repeat bg family intentionally — the reference presentation does this — but they're never consecutive and each has a mirrored/varied numeral + color treatment.

Slides 14 and 15 both use a phone-left layout. They're adjacent. I flag this as the ONE near-miss — mitigated by different backgrounds (paper-tinted vs dark-forest) and distinctly different right-side content (stat + 2 quotes + Dovetail vs stat + 2 quotes + insight). If you want harder separation, I can flip s15 to a different composition (e.g. the body map as the full focal without a phone frame around it). **Flagging for your call.**

---

## CHUNK 5 — OPEN QUESTIONS (please answer before I build)

1. **Slide 14/15 phone-left repeat.** Keep as-planned (differentiated by bg + right-side content) or redesign s15 to a bigger-body-map-no-phone-frame treatment?
2. **Slide 2 team composition.** How many team members should appear? Names/roles you want listed? I'll draft with `[Kyle, Lead Researcher]`, `[Designer]`, `[Product]`, `[Clinical]`, `[Engineering]` placeholders unless you specify.
3. **Slide 9 lab photo.** Do you have a preferred still from the Dovetail overhead camera? If not, I'll use a styled Dovetail-chrome placeholder card, `data-asset="s9-lab-overhead"`.
4. **Slide 15 body map.** Real screenshot available, or do I build the stylized CSS anatomical mock as a placeholder (matching slide 14's approach)?
5. **Dovetail clips.** Slide 15 references a P02 @ 15:46 clip. I'll render the styled placeholder and set up the `<video>`-fallback pattern per rule 13 — OK?
6. **Section Starter numeral variation.** I plan three slightly different numeral treatments (5: mint `01`; 8: teal-300 `02` mirrored; 12: teal-500 with a subtle underline `03`). Acceptable, or do you want them identical for rhythm?
7. **Deferred POC slides.** Confirm OK to move `s4` (SEQ) and `s6` (Finding 1) to the bottom of the file under `.slide-deferred` class, hidden from navigator, preserved for session 6.

---

## CHUNK 6 — BUILD ORDER + CHECKPOINTS

I will build in **three batches** to respect the 5-slide checkpoint rule:

- **Batch A (slides 1–5):** repoint s1, build s2, s3, s4, s5. Checkpoint: audit against 14 standing rules.
- **Batch B (slides 6–10):** repoint s6, s7, build s8, s9, s10. Checkpoint.
- **Batch C (slides 11–15):** build s11, s12, s13, repoint s14, build s15. Final checkpoint + PDF export test + nav/keyboard/touch test + viewport sweep at 1920, 1440, 1024, 390.

Between each batch I'll verify: no overflow, no consecutive layout/bg repeats, every pill is a chip, popovers clamp to canvas, numbers in footer/nav match, deferred slides excluded from SLIDES array.

---

## CHUNK 7 — ACCEPTANCE CRITERIA

- [ ] 15 slides render in order, no overflow, no overlap, no clipping.
- [ ] Navigator shows 15 slides in 4 sections, thumbnails painted, current highlighted, click-to-jump works.
- [ ] Keyboard (← → space), edge arrows, bottom-center prev/next, touch swipe all work.
- [ ] Fullscreen button + `F` shortcut work.
- [ ] PDF export downloads a 15-page PDF; deferred slides not included; navigator hidden; animations resolved.
- [ ] Every visible pill is a chip trigger; popovers clamp inside canvas bounds; each popover delivers NEW info from spine.
- [ ] No consecutive slides share bg family OR layout family (except the intentional section-starter bg-family reuse at 5/8/12, which are never consecutive).
- [ ] No left colored borders. No three-identical-card grids. No Inter/Roboto/Arial. No purple gradients. No "CSS fix" business-unfriendly jargon.
- [ ] All placeholder assets use stable `data-asset="..."` hooks for easy swap-in.
- [ ] Deferred s4 (SEQ) and s6 (Finding 1) preserved in the DOM under `.slide-deferred`, ready for session 6.

---

**Awaiting approval of this plan before I start on Batch A.**




