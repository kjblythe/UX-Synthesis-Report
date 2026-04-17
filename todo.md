# Session 6 Plan — Build Slides 16–30

**Goal:** Continue the build from the 15-slide base shipped in session 5. This session covers the rest of Section 4 (What Resonated), all of Section 5 (Task-by-Task Results), and the first seven slides of Section 6 (Design Findings). Two deferred POC slides reinsert at their blueprint positions during this range.

---

## CHUNK 1 — PRINCIPLES (re-stated from CLAUDE.md + lessons-learned)

**Palette (locked from sessions 1–5):**
- `--forest-base: #0A3B35` · `--forest-deep: #062823` · `--forest-mid: #0F4A42`
- `--teal-500: #14B8A6` · `--teal-300: #5EEAD4`
- `--mint-accent: #34EEA7` (reserved "wow" moment per slide)
- `--paper: #F7F1E5` · `--paper-deep: #EBE3D1`
- `--gold: #F59E0B` · `--coral: #EF4444` (sparingly)
- `--ink: #0A1A1C` · `--ink-mute: #4A5558`

**Type:** Sora (display + body + data, tabular nums) / Fraunces italic (quotes only). No Inter, Roboto, Arial.

**Anti-patterns explicitly avoided:**
- Cards with left colored borders
- Three identical cards in a grid
- Purple gradients, neon blue, BI-X bright blue
- Generic icon-header-description rows
- Consecutive slides sharing bg family AND layout family
- Jargon on slide surfaces ("CSS fix," etc.)
- Static stat pills masquerading as chip triggers
- Popovers extending beyond `#canvas.getBoundingClientRect()`
- Pitch-deck headlines ("the breakout," "the north star," "universal approval as headline")
- Flex `gap`, `object-fit: cover` on `<img>`, `inset: 0` shorthand, CSS border triangles (all html2canvas footguns)

**Voice:** a principal investigator presenting evidence to a funding committee that already knows the team, the program, and the product. Internal readout, not pitch deck. Declarative. Evidence-first.

**Structural invariants (DO NOT violate):**
1. Slide base positioning is `position: absolute; inset: 0`. Never override on a `.slide-*` variant.
2. CSS scoped selectors must follow class-token renames. Grep before renaming.
3. No same-specificity collisions on `.screen` / `.phone-screen` / `.phone`.
4. Phone-frame standard is 380px wide, 8px bezel (JS hardcodes this).
5. Canvas is sacred — popovers clamp against `#canvas.getBoundingClientRect()`.

---

## CHUNK 2 — SCOPE: SLIDES 16–30

**15 slide positions. 13 new builds. 2 deferred reinserts (Slide 21 SEQ, Slide 25 F1).**

| # | Slide (blueprint) | Build action |
|---|---|---|
| 16 | AI Coach — Contextual Intelligence | NEW |
| 17 | Learning Content — Behavioral Science That Lands | NEW |
| 18 | Competitive Advantage — "Better Than What I Use Now" | NEW |
| 19 | The Value Proposition — In Their Words | NEW |
| 20 | Section Starter — Detailed Results | NEW |
| 21 | What We Measured — Understanding SEQ | **REINSERT `.s-deferred-seq` → `.s21`** |
| 22 | Post-Session Satisfaction | NEW |
| 23 | Prototype Context | NEW |
| 24 | Section Starter — Design Findings & Opportunities | NEW |
| 25 | Finding 1 — Visual Differentiation & Affordance Clarity | **REINSERT `.s-deferred-f1` → `.s25`** |
| 26 | Finding 1 — Architecture Validation (P07 Paradox) | NEW |
| 27 | Finding 1 — Recommended Remediations | NEW |
| 28 | Finding 2 — AI Coach Discoverability & Positioning | NEW |
| 29 | Finding 2 — Design Principle & Recommendations | NEW |
| 30 | Finding 3 — Meds Screen as Primary Logging Entry Point | NEW |

**Note on the user's instruction:** User explicitly flagged "reinsert `.s-deferred-seq` as Slide 21 per the protocol." Per the lessons-learned protocol table, `.s-deferred-f1` also belongs in this range at Slide 25. I am assuming BOTH reinserts happen this session. **If this is wrong — e.g. you want the f1 reinsert held for a later session and Slide 25 rebuilt fresh — flag it in the open questions below and I will adjust.**

**Reinsertion steps per slide (applies to both):**
1. Re-read the blueprint entry to confirm content alignment with the shipped deferred slide.
2. Move the section from its current `.slide-deferred` position to its correct sequential position in the HTML.
3. Change class: `.slide-deferred` → `.slide`. Rename scoped class (`s-deferred-seq` → `s21`, `s-deferred-f1` → `s25`).
4. **Grep CSS for `\.s-deferred-seq\b` and `\.s-deferred-f1\b`; rename every occurrence in the same commit.**
5. Add entry to `SLIDES` array in order; verify `paintThumb` has a branch for the slide's `thumb` key.
6. Update `.foot-page` numeral.
7. Verify popover `data-cite` references, chip behavior, and `data-on-enter="animateSEQ"` still fire.
8. Verify navigator thumbnail renders and click-to-jump works.

---

## CHUNK 3a — PER-SLIDE PLAN (slides 16–19, remainder of Section 4)

### Slide 16 · AI Coach — Contextual Intelligence (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** asymmetric editorial — hero headline top, a "conversational column" left (styled as a short chat transcript with 2–3 participant turns), a "what this means vs. generic AI" column right stacked as editorial quote pairs.
- **Focal:** the hero stat `7/7 found it useful` rendered in large tabular nums with a one-line lede: `Useful beyond novelty — valued for exploration, questions, coaching feedback.`
- **Chat column (left):** styled as a minimal transcript. Each turn shows the participant as a small P-ID chip + their line, and the "Coach" replies are rendered in muted teal. Two turns:
  - P07 [30:04] → *"It's focused on this app and what I'm going through. I don't have to tell it anything because it already knows."*
  - P05 [38:22] → *"I personally don't have anyone that I'm going through like a weight loss journey with. So it's just me, myself, and I."*
- **Quote pair (right):** two short lines under eyebrow `What this means vs. a generic chatbot`:
  - P01 [33:43] — *"Helpful overall — to ask those questions without having to call your doctor."*
  - P04 [28:48] — *"The screens feel more natural, but I like the idea of talking to the coach because I like the feedback."*
- **Dovetail clip card:** P05 @ 38:22 — positioned under the chat column, compact (same `.clip-card` component as slide 14).
- **Chips:** every P-ID is a chip-trigger → spine-sourced profile popover. `[7/7]` → per-participant usefulness breakdown. `[post-discovery]` inline chip explains the discoverability caveat (previewing Finding 2, without spoiling it).
- **No phone frame on this slide** — the previous slide (15 Body Map) uses a phone. Breaking the pattern here is intentional.
- **Variety:** paper editorial, asymmetric columns — distinct from s15 (dark phone-left) and s17 (coming next).

### Slide 17 · Learning Content — Behavioral Science That Lands (NEW)
- **Bg:** Dark-Forest with soft mint glow offset to the left (behind the pathway viz). **Layout:** pathway-forward. Left ⅗ is a stylized "Learn overview" visualization — NOT a full phone frame, but a cropped treatment that shows the CORE pathways stacked as editorial typographic rows with progress dots (echoing the app's Duolingo-like pathway UI without cluttering). Right ⅖ holds the hero stat, two quotes, and the insight callout.
- **Focal:** the pathway visualization. Five CORE paths rendered as titled rows with small progress-dot arrays (completed / locked). One row — "Personalized" — has a subtle mint ring to flag the AI-generated path.
- **Hero stat:** `7/7 engaged with content once found` (tabular). Secondary line: `Grounded in CBT, ACT, behavioral activation — unnoticed as a framework, which is the sign of effective behavioral design.`
- **Quotes (right column):**
  - P02 [38:13] — *"When you bunch a list together, it scrambles your brain. This one separates it so it's individualized."*
  - P07 [39:50] — *"It gives people options if you're not an AI type person."*
- **Insight (small caption):** `Discoverability is the real issue — not content or format. Tied to Finding 1 (bottom-nav visibility).` The `Finding 1` text is an inline chip → pop with the F1 one-line + cue to jump to s25.
- **Chips:** `[P02]` `[P07]` `[7/7]` `[CBT / ACT]` — chip expands to explain the clinical frameworks in one sentence each (from spine F7).
- **Data hook:** `data-asset="learn-pathway"` on the pathway viz container so a real screenshot can drop in later.
- **Variety:** dark, pathway-forward, left-heavy viz — contrasts paper s16 before and paper s18 after.

### Slide 18 · Competitive Advantage — "Better Than What I Use Now" (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** editorial comparison table — 5 rows, one per participant-mentioned app, rendered as typographic rows with hairline dividers. Columns: `Current tool` · `What it does` · `What it doesn't` · this app's coverage dot. No left colored borders. No cell fills.
- **Focal:** the table's final column — a full column of teal ✓ dots visually reads as "this app covers all of it."
- **Rows (from spine K):**
  - MyFitnessPal (P04) · Calorie tracking · No GLP-1, no AI, no photo · ✓
  - Shotzy (P05) · Injection tracking · No site-rotation history · ✓
  - Weight Watchers / Healthi (P03) · Weight, community · No AI, no meds · ✓
  - Microhealth (P02) · Infusion tracking · No nutrition, limited body map · ✓
  - Apple Health (P07) · Step counting · No nutrition, no AI, no meds · ✓
- **Two quotes below the table, offset with typographic contrast:**
  - P03 [52:34] — *"I would definitely consider replacing the one I use with this and use this instead."*
  - P02 [08:00] — *"I tried to add my GLP-1 to [my app], but I couldn't. So I'm interested in this app."*
- **Dovetail clip card:** P03 @ 52:34 — compact, positioned to the right of the quote block.
- **Chips:** every P-ID + every current-tool name (MyFitnessPal, Shotzy, etc.) → popover with the spine detail on why they mentioned it.
- **Variety:** paper, editorial-table — distinct from the dark pathway viz before and the dark quote montage after.

### Slide 19 · The Value Proposition — In Their Words (NEW)
- **Bg:** Dark-Forest, plain, with a subtle low-opacity X motif at ~4% opacity far-right (different position from the section-starter watermark so it doesn't duplicate). **Layout:** three-quote typographic montage, no decorative cards. Each quote is a standalone editorial block: Fraunces italic pull-quote on top, P-ID + context below, separated by generous negative space.
- **Focal:** the three quotes as a cadence — not one dominant, but a rhythm. Page reads top-to-bottom.
- **Quotes (from spine A):**
  - P04 [48:26] — *"It's a nutritional app, it's a fitness app, it's everything wrapped up in one… I would highly recommend it."*
  - P07 [52:52] — *"It would be great if the advertising could be geared towards tracking your journey, because this is not something you're just gonna lose weight on. You have to modify your life."*
  - P05 [10:40] — *"This looks like it kind of combines a lot, like more than one app."*
- **Eyebrow:** `In their words` (top-left). **Capstone caption (bottom-right):** `Section transition — task-level evidence follows.`
- **Chips:** each P-ID chip → full spine-sourced profile + the broader quote context. No other citations; the slide is emotional-capstone-quiet.
- **Variety:** dark, full-slide typographic montage — NOT the centered single-quote treatment of s7. Distinctly different composition.

---

## CHUNK 3b — PER-SLIDE PLAN (slides 20–23, Section 5 Task-by-Task)

### Slide 20 · Section Starter — Detailed Results (NEW)
- **Bg:** Dark-X-Watermark (4th use — section starters at 5, 8, 12, 20 share the family). **Layout:** same `.starter-a` hero-numeral pattern established in session 5.
- **Content:** eyebrow `Section 04`. Title `Detailed Results`. Subtitle: `Task-by-task evidence. SEQ scores, post-session satisfaction, and the prototype context that frames both.`
- **Numeral treatment:** mint `04` (matching session-5 convention that all section starters use `starter-a` with mint numeral — user's explicit call to keep consistent).
- **Variety:** intentional bg-family repeat with s5/s8/s12; never consecutive.

### Slide 21 · What We Measured — Understanding SEQ (REINSERT `.s-deferred-seq`)
- **Source:** the deferred POC SEQ hero slide, already QA'd in sessions 1–4.
- **Action:**
  1. Move `<section class="slide-deferred s-deferred-seq slide-data-stage">` to the correct sequential position (between s20 and s22).
  2. Rename class `slide-deferred` → `slide`; rename `s-deferred-seq` → `s21`.
  3. Grep CSS: `grep -n "\.s-deferred-seq\b" index.html` → rename every occurrence to `.s21`. (Per the lessons-learned rename protocol.)
  4. Update `.foot-page` numeral to `21`.
  5. Add to `SLIDES` array: `{ id: 's21', num: 21, section: 'Detailed Results', title: 'Understanding SEQ', thumb: 'seq' }`.
  6. Verify `paintThumb` handles `seq` key (it already does — built in session 1).
  7. Verify `data-on-enter="animateSEQ"` still fires on slide entry.
- **Content-alignment note vs. blueprint:** blueprint slide 21 title is "What We Measured — Understanding SEQ" and describes a 1–7 scale explainer with our 6.4 mark. The deferred POC slide combines that explainer WITH a per-task breakdown expansion (blueprint slide 22's content) behind a click-to-expand affordance. This is intentionally better than the blueprint — it consolidates two slides into one interactive surface, freeing slide 22 for the post-session satisfaction viz (which needs the room). Per CLAUDE.md the blueprint is the content authority but editorial consolidation is allowed when it improves clarity. **Call this out in the demo.**
- **One copy tweak:** the deferred copy leads with "A 1–7 scale. We hit 6.4." — passes the PI-voice test. Keeping as-is.
- **Eyebrow update only:** the deferred slide's eyebrow says "How we measured ease" — fine, but I'll prefix with `Section 04 · Understanding SEQ` for cohesion with other slides in this section. Small change.

### Slide 22 · Post-Session Satisfaction (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** two-band composition — top band is a horizontal "lollipop" plot of the 6 post-session items (each item as a row with a dot at the mean position on a 1–7 axis, a thin rule connecting to a subdued tick axis). Bottom band is a small stacked-dot "participant cluster" viz showing all 7 participants' overall means plotted on the same scale.
- **Focal:** the lollipop plot. Every item clusters between 6.4–6.7 on the axis, which tells the story visually without needing per-item commentary.
- **Data (from spine §5):** rows rendered top-to-bottom:
  - Features meet my needs — 6.6
  - Easy to use — 6.7
  - Trust with health info — 6.6
  - Fits my daily routine — 6.7
  - AI feels helpful, not gimmicky — 6.6
  - Understands my journey — 6.4
  - **Overall mean highlighted: 6.6/7.**
- **Participant cluster (bottom band):** 7 dots plotted on the same axis — 3 at 7.0 (P01/P02/P04), P05 6.7, P07 6.5, P06 6.2, P03 5.8. Each dot is a chip-trigger → popover with that participant's per-item breakdown.
- **Callout:** `P03 (mean 5.8 — lowest) said she would still replace her current app with this one.` P03 chip deepens the context.
- **Chips:** every item mean (6.6, 6.7, etc.) is a chip → popover with the 7-value breakdown. Every participant dot is a chip. `[Trust 6.6]` → popover notes P07's outlier 5 (only non-7 on that item) and what she said about it.
- **Why not a radar chart:** all items cluster in a tight band (6.4–6.7); radars under-emphasize meaningful differences and visually over-emphasize irrelevant angular artifacts. A lollipop reads honestly.
- **Variety:** paper light, data-forward, horizontal — contrasts dark data-stage SEQ before and dark limitations ledger after.

### Slide 23 · Prototype Context (NEW)
- **Bg:** Dark-Forest, subdued (no glow, minimal decoration — the slide's tone is "honest transparency"). **Layout:** two-column ledger. Left column is a framed intro paragraph setting the posture ("This was a fully interactive PWA with live AI, not a mockup. Participants treated it as a real app. We note the limitations that affected specific findings."). Right column is a 4-row limitation table with hairline dividers, no fills.
- **Focal:** the intro paragraph's first sentence, rendered in Sora 500 one step larger than body.
- **Limitation rows (from spine §VI):**
  - Microphone non-functional → P07's T4 SEQ of 5 explicitly attributed to this; confirms voice-input demand.
  - AI response variability → live AI produced inconsistent responses; may explain some T4 range.
  - Fixed persona data → P01 and P04 tried to customize dose; expected behavior the prototype couldn't support.
  - Catch-up logging not prototyped → feature exists in production but was out of scope.
- **Chips:** `[P07]` `[P01]` `[P04]` → profile popovers. `[T4 range]` → cross-link to SEQ slide's per-task data. `[PL2]` `[PL4]` → spine's prototype-limitations ledger detail.
- **Why this slide matters:** preempts stakeholder skepticism about SEQ scores. Shows we're not hiding anything.
- **Variety:** dark subdued, ledger-style table — distinct from paper post-session before and dark-X-watermark section starter after.

---

## CHUNK 3c — PER-SLIDE PLAN (slides 24–27, Section 6 start + F1)

### Slide 24 · Section Starter — Design Findings & Opportunities (NEW)
- **Bg:** Dark-X-Watermark (5th use). **Layout:** same `.starter-a` hero-numeral pattern.
- **Content:** eyebrow `Section 05`. Title `Design Findings & Opportunities`. Subtitle: `What we learned. How to make it better.`
- **Numeral:** mint `05`.
- **Variety:** same bg family as s5/s8/s12/s20 — not consecutive.

### Slide 25 · Finding 1 — Visual Differentiation & Affordance Clarity (REINSERT `.s-deferred-f1`)
- **Source:** the deferred POC F1 slide, already QA'd in sessions 1–4.
- **Action:**
  1. Move `<section class="slide-deferred s-deferred-f1 slide-dark">` to the correct sequential position (between s24 and s26).
  2. Rename class `slide-deferred` → `slide`; rename `s-deferred-f1` → `s25`.
  3. Grep CSS: `grep -n "\.s-deferred-f1\b" index.html` → rename every occurrence to `.s25`. (Rename protocol.)
  4. Update `.foot-page` numeral to `25`.
  5. Add to `SLIDES` array: `{ id: 's25', num: 25, section: 'Design Findings & Opportunities', title: 'Finding 1 — Visual Differentiation', thumb: 'f1' }`.
  6. Verify `paintThumb` handles `f1` key (it already does — built in session 1).
- **Eyebrow tweak only:** currently says "Finding 01 · Visual differentiation" — keeping. Section label updates are handled by `SLIDES` section attribute, not eyebrow text.
- **Preserved interactions:** all callout chips (`[f1-bottomnav]`, `[f1-fab]`, `[p04]`, `[p07]`, `[p07-paradox]`) already route through the global popover handler. Verified this works in sessions 1–4.

### Slide 26 · Finding 1 — Architecture Validation (The P07 Paradox) (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** named-duel two-column layout — centered headline `The same person. Two stories.` with eyebrow `Finding 01 · Architecture validation`. Below the headline, two columns with a hairline vertical rule between them.
  - Left column: `What P07 said about herself` — 4 self-assessment quotes rendered as editorial blocks with a muted-sage left alignment rule (NOT a colored left border — a hairline, and only on the vertical rule between columns).
  - Right column: `What P07 actually did` — 4 behavioral observations rendered with a mint rule on the same baseline.
  - Below the columns: one caption tying the two sides together, plus the Dovetail clip card.
- **Focal:** the juxtaposition itself. Reading left-to-right on every row produces the paradox.
- **Content (from blueprint slide 26 table):**

| Self-assessment (left) | Actual performance (right) |
|---|---|
| App comfort: 5/7 (lowest in cohort) | Found every feature on first attempt |
| *"There's always some apps that challenge me."* [03:46] | Decoded wellness-score rings unprompted |
| *"I'm the kind of person who X's out of things by mistake."* [50:34] | Found Learn "right here at the bottom" [35:01] |
| Uses Apple Health once a week for step counting | Correctly predicted feature behavior before tapping |

- **Caption below:** `If the least tech-comfortable participant can navigate every feature intuitively, the architecture is sound. Finding 1's problems are styling, not structure.` (Translates "CSS fix" to business vocabulary per session-2 rule.)
- **Dovetail clip card:** P07 [03:46] tech-discomfort clip — compact, bottom-right.
- **Chips:** `[P07]` full profile popover. `[03:46]` `[35:01]` `[50:34]` → each timestamp chip → the transcript context from spine. `[architecture is sound]` inline chip → links to the target-demographic validation in spine §IV.
- **No left colored borders.** The column separator is a single vertical hairline. Typographic hierarchy carries the comparison, not card borders.
- **Variety:** paper, named-duel two-column — contrasts the dark F1-phone slide before and the dark remediation table after.

### Slide 27 · Finding 1 — Recommended Remediations (NEW)
- **Bg:** Dark-Forest. **Layout:** 4-row remediation grid. Each row is a typographic unit: element name (Sora 600) + issue (muted sage one-liner) + recommendation (Sora 500 on-dark color) + complexity tag at far right.
- **Focal:** the complexity tags, all reading `Low` or `Low–Medium` — the visual message is "everything here is tractable."
- **Rows (from blueprint slide 27):**
  - **Bottom navigation** — Semi-transparent on dark reads as decorative → Solid/semi-opaque bg, larger icons, stronger labels. `Low`
  - **Primary action button** — Correct pattern, insufficient visual weight → Color/contrast boost, subtle entrance animation. `Low`
  - **Toast notifications** — Styled like content cards → Restyle as distinct banners (full-width, different color, brief animation). Add persistent "last logged" indicators on home screen. `Low–Medium`
  - **Card CTAs (F11)** — Decorative icon above fold mistaken for button; real CTA below fold → Make icon tappable, or move CTA above fold, or visually de-emphasize decorative icon. `Low`
- **Eyebrow:** `Finding 01 · Recommended remediations`.
- **Caption below the grid:** `Every item is ticketable pre-pilot. No architectural changes required.`
- **Chips:** `[persistent "last logged" indicators]` → P06 [15:35] spine quote. `[F11]` → blueprint F11 detail + P04 [14:03] moment. `[Low–Medium]` → one-line explanation of the complexity axis.
- **Styling discipline:** no left colored borders. Rows separated by hairlines only. The "complexity" tag is a small pill, but it IS a chip trigger (consistent with rule 19).
- **Variety:** dark, typographic remediation list — contrasts paper P07 paradox before and paper AI Coach spectrum after.

---

## CHUNK 3d — PER-SLIDE PLAN (slides 28–30, F2 + F3)

### Slide 28 · Finding 2 — AI Coach Discoverability & Positioning (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** mental-model spectrum — a horizontal scale from "Customer service" (left) to "Focused on my journey" (right), with four participant plot-points along it. Above the spectrum: eyebrow `Finding 02 · AI Coach · Discoverability + labeling` and headline `Coach meant four different things to four participants.` Below the spectrum: a split "The labeling problem" quote + "The post-discovery value" quote pair.
- **Focal:** the spectrum viz. Each plot-point is a vertical hairline with a P-ID chip and a short mental-model tag.
- **Spectrum plot (left → right):**
  - P02 → *"Customer service type thing"* [31:49]
  - P04 → *"Tutorial? Pumping you up?"* [09:44]
  - P05 → *"A buddy"* [36:49]
  - P07 → *"Focused on my journey"* [30:04]
- **Key data pinned above the spectrum:** `7/7 valued it after using it. · 2–3/7 found it independently on the directed task.`
- **Quote split below (two blocks side by side, no cards):**
  - Left — eyebrow `The labeling problem` — P04 [09:44] *"Is it a tutorial? Is it a more descriptive part of the app? Is it something giving you pep?"*
  - Right — eyebrow `The post-discovery value` — P07 [30:04] *"It already knows that I'm looking for that."* + P05 [36:49] *"It's almost like having a buddy."*
- **Chips:** every P-ID → profile popover + the transcript context for that moment. `[2–3/7]` → the spine's T4 discoverability breakdown (who went direct, who detoured, who needed a bridge).
- **Variety:** paper, spectrum composition — distinct from dark remediation grid before and dark two-column recs after.

### Slide 29 · Finding 2 — Design Principle & Recommendations (NEW)
- **Bg:** Dark-Forest. **Layout:** two-column editorial. Left column headlined `What this means` with a design-principle statement. Right column headlined `Recommendations` with a 4-item numbered list. Hairline vertical rule between.
- **Focal:** the design principle at the top of the left column, rendered in Sora 500 one step larger than body:
  > `AI Coach is most valuable for exploration, questions, and coaching feedback. UI screens are most natural for repetitive, structured actions. Both paths should coexist.`
- **Right column recommendations (numbered):**
  - 01 · Increase Coach prominence in the UI (beyond the bottom nav).
  - 02 · Rename or add a descriptive subtitle to clarify what the feature does.
  - 03 · Add contextual prompts from within other features ("Ask Coach about this").
  - 04 · Monitor natural discovery patterns in the diary study — single-session discoverability may resolve with multi-day use.
- **Caption below both columns:** `Strength high (post-discovery). Severity medium (discoverability). Complexity low.` with each tag a chip → popover with the severity/complexity criteria.
- **Chips:** `[P05 temporal model]` inline chip in the principle statement → P05's "chat for onboarding, UI for maintenance" spine quote [42:29], which supports the design principle.
- **Variety:** dark, two-column recs — contrasts paper spectrum before and paper phone+annotation after.

### Slide 30 · Finding 3 — Meds Screen as Primary Logging Entry Point (NEW)
- **Bg:** Paper-Editorial (light). **Layout:** phone-left + annotation + content-right. The phone displays a stylized Meds screen (calendar view with the "today" date ringed in teal as the annotation target). Above the "today" ring, a callout line points to it with a small connector line and a label: `3/7 tapped here expecting to log.` The right column holds the headline, key data, quote, and recommendation.
- **Focal:** the teal ring around "today" on the meds calendar — the users' instinct made visible.
- **Content:**
  - **Eyebrow:** `Finding 03 · Meds screen · A natural primary entry point`
  - **Headline:** `Users tried to log from the meds calendar. They were right — the screen just doesn't support it yet.`
  - **Key data:** `3/7 went to meds section first to log. All three tapped "today."`
  - **Quote (Fraunces italic):** P07 [17:52] *"It literally says meds. So I would have expected that if I went there, that would have been an option."*
  - **Recommendation (small, right-column bottom):** `Make the meds calendar's "today" date tappable to initiate the injection logging flow. Low complexity, high impact.`
- **Chips:** `[P07]` `[P03]` `[P05]` → profile + moment (spine F6). `[3/7]` → the three participant paths spine table. `[learning transfer]` inline chip → P03 "Well I learned not to hit those" [18:03] — the fast-learning-curve note from spine.
- **Placeholder asset hook:** the phone's meds screen is a CSS mock (calendar grid + today ring + mini dose callouts). `data-asset="meds-popover"` — a real screenshot can drop in later via the existing asset loader.
- **Dovetail clip card:** P07 [17:52] — compact, positioned under the recommendation on the right.
- **Variety:** paper, phone+annotation+content — contrasts dark two-column recs before. Phone-left echoes s14/s15/s25 but rotation rule holds since those aren't consecutive and the annotation treatment is distinctly editorial.

---

## CHUNK 4 — BACKGROUND / LAYOUT ROTATION AUDIT

Adjacency check against session-5 slide 15 (Dark-Forest phone-left) on the front, and open-ended on the back.

| # | Slide | Bg family | Layout family |
|---|---|---|---|
| 15 | Body Map (prev session) | Dark-Forest | Phone-left + stat/quotes-right |
| 16 | AI Coach | Paper-Editorial | Chat-transcript column + quote pair |
| 17 | Learning | Dark-Forest + mint glow | Pathway viz left + content right |
| 18 | Competitive Advantage | Paper-Editorial | Editorial comparison table |
| 19 | Value Proposition | Dark-Forest | Three-quote typographic montage |
| 20 | Section Starter · Detailed Results | Dark-X-Watermark | Section starter (hero numeral) |
| 21 | SEQ (reinsert) | Data-Stage (dark + glow) | Composite scale + per-task viz |
| 22 | Post-Session Satisfaction | Paper-Editorial | Lollipop plot + participant dots |
| 23 | Prototype Context | Dark-Forest (subdued) | Two-column honest ledger |
| 24 | Section Starter · Design Findings | Dark-X-Watermark | Section starter |
| 25 | F1 Visual Diff (reinsert) | Dark-Forest | Phone-left + callout stack |
| 26 | F1 P07 Paradox | Paper-Editorial | Named-duel two-column |
| 27 | F1 Remediations | Dark-Forest | 4-row typographic remediation grid |
| 28 | F2 AI Coach spectrum | Paper-Editorial | Horizontal spectrum + quote split |
| 29 | F2 Recommendations | Dark-Forest | Principle + numbered recs two-column |
| 30 | F3 Meds Screen | Paper-Editorial | Phone-left + annotation + content |

**No two consecutive slides share BOTH bg family AND layout family.** Section starters (5/8/12/20/24) intentionally reuse the Dark-X-Watermark family — they're never adjacent.

**Flagged near-misses (mitigated):**
- **s19 → s20 → s21** (three dark). Different layout families (quote montage → hero numeral → data viz). Bg family sub-varies: plain dark → watermark dark → data-stage dark. Precedent: session 5 accepted s7 Dark-Forest → s8 Dark-X-Watermark → s9 Paper. Same pattern here plus one more dark slide with visually distinct treatment. Holds.
- **s23 → s24 → s25** (three dark). Same reasoning: subdued ledger → watermark starter → phone+callout. Layout families all different.
- **Phone-left layouts at s14 (paper), s15 (dark), s25 (dark), s30 (paper).** None adjacent within this session's build. s25 and s30 are separated by s26/27/28/29. Holds.
- **Paper-Editorial used 6× in this range.** Rotation rule is about adjacency, not totals. Every paper slide is separated by at least one non-paper slide. Holds.

---

## CHUNK 5 — OPEN QUESTIONS (please confirm before I start Batch A)

1. **F1 reinsert in this session?** Lessons-learned protocol puts `.s-deferred-f1` at Slide 25 during Session 7 (slides 24–33), but this session's range (16–30) includes slide 25. I've planned to reinsert in this session. **Confirm, or hold for next session?**
2. **SEQ slide content consolidation.** Blueprint slide 21 (SEQ explainer) and blueprint slide 22 (SEQ per-task bars) are functionally combined in the deferred POC slide via click-to-expand. I plan to keep this consolidation (frees slide 22 for post-session satisfaction). **Confirm, or rebuild as two separate slides?** If two separate slides, the numbering below shifts and post-session satisfaction becomes slide 23, prototype context becomes slide 24, pushing the whole later-range by one.
3. **Slide 17 Learning pathway visualization.** I plan a stylized editorial treatment (typographic pathway rows with progress dots, not a full phone frame) since s15 and s25 already carry phone frames nearby. **OK, or do you want a real phone screenshot of the Learn overview?** If the latter, we need the asset (`assets/screenshots/learn-pathway.png`).
4. **Slide 22 viz choice.** Lollipop plot over radar chart (for the reasons argued above — radars under-emphasize meaningful differences at this data's tight range). **OK, or prefer the blueprint's radar option?**
5. **Dovetail clip placements this session.** I'll render styled placeholders with `data-video="..."` for: P05 [38:22] (s16), P03 [52:34] (s18), P07 [53:48] (s19 — optional, may skip since s7 already uses it), P07 [03:46] (s26), P07 [17:52] (s30). Confirm list.
6. **Slide 19 · value prop fourth quote.** Blueprint suggests 3–4 quotes. I planned 3 (P04, P07, P05). **Add P03's "I would definitely consider replacing" as the fourth?** It's a strong persuasion quote but also appears on slide 18, so I'd rather skip to avoid repetition.
7. **Voice/tone spot-checks.** A few planned headlines I want to flag-ahead for the PI-voice test:
   - s17 — *"Behavioral Science That Lands"* — blueprint phrasing. Feels pitch-deck-ish. Proposed swap: `Learning content — validated format, discoverability-bound.` Your call.
   - s19 — *"The Value Proposition — In Their Words"* — I'll use only the `In their words` eyebrow on-slide; "Value Proposition" stays in the navigator metadata. OK?
   - s26 headline *"The same person. Two stories."* — feels right for the paradox, but checking.
8. **Slide 23 tone.** This is the "honest transparency" slide. Blueprint says "not defensive, just honest." I've planned it as a subdued dark ledger. **OK, or prefer a paper treatment to visually reinforce "this is the footnote, not the story"?**

---

## CHUNK 6 — BUILD ORDER + CHECKPOINTS

Three batches to respect the every-5-slides rule.

- **Batch A (slides 16–20):** Build s16 (AI Coach), s17 (Learning), s18 (Competitive), s19 (Value Prop), s20 (Section Starter · Detailed Results). Checkpoint against 14 standing rules + rotation audit.
- **Batch B (slides 21–25):** Reinsert `.s-deferred-seq` as s21 (rename + grep CSS + SLIDES array). Build s22 (Post-Session). Build s23 (Prototype Context). Build s24 (Section Starter · Design Findings). Reinsert `.s-deferred-f1` as s25 (rename + grep CSS). Checkpoint.
- **Batch C (slides 26–30):** Build s26 (P07 Paradox), s27 (Remediations), s28 (AI Coach Spectrum), s29 (F2 Recs), s30 (Meds Screen). Final checkpoint + PDF export test + nav/keyboard/touch test + viewport sweep at 1920, 1440, 1024, 390.

Between each batch I verify:
- No overflow / overlap / clipping at 1920 native.
- No consecutive layout or bg family repeats.
- Every pill is a chip trigger; every popover clamps to canvas bounds; every popover delivers NEW info (not a slide-content repeat).
- `.foot-page` numerals and `SLIDES` array are in sync with section HTML order.
- Deferred classes are fully renamed in both HTML and CSS (no dangling `.s-deferred-*` selectors).
- PDF export still renders (test after Batch B since the reinsert changes matter, test again after Batch C).

---

## CHUNK 7 — ACCEPTANCE CRITERIA

- [ ] 30 slides render in order, no overflow, no overlap, no clipping.
- [ ] Navigator shows all 30 slides in 6 sections (Front Matter 1–4, Executive Summary 5–7, Study Design & Participant Profile 8–11, What Resonated 12–19, Detailed Results 20–23, Design Findings & Opportunities 24–30).
- [ ] Thumbnails paint for every slide including new `seq`, `f1`, and new thumb keys for 16, 17, 18, 19, 20, 22, 23, 24, 26, 27, 28, 29, 30.
- [ ] `.s-deferred-seq` and `.s-deferred-f1` classes no longer exist in HTML or CSS — fully renamed to `.s21` and `.s25`.
- [ ] Every visible pill/badge is a chip trigger. Every popover clamps inside `#canvas.getBoundingClientRect()` with 16px padding. Every popover delivers new information (participant profile, cohort breakdown, behavioural moment, "why").
- [ ] Keyboard (← → space), edge arrows, bottom-center prev/next, touch swipe, fullscreen (`F`) all work across all 30 slides.
- [ ] PDF export downloads a 30-page PDF; deferred slides not included (there are none left); navigator hidden; animations resolved to final state; SEQ per-task expansion rendered expanded in print mode.
- [ ] No consecutive slides share both bg family AND layout family (section-starter bg-family intentional repeats at 5/8/12/20/24 are never consecutive).
- [ ] Anti-pattern scan: no left colored borders, no three-identical-card grids, no Inter/Roboto/Arial, no purple gradients, no "CSS fix" / "HTML" / "frontend" jargon in body or headlines.
- [ ] Tone scan: every headline passes the PI-voice test. No "north star" / "breakout" / "adoption gatekeeper" / "landed" / "cleared the bar" / "adoption curve" / "natural rhythm of a day" / "A day in the life" / "Most X are Y. This does Z." patterns.
- [ ] Placeholder asset hooks (`data-asset`, `data-video`, `data-headshot`) stable and documented for future swap-in.
- [ ] Lessons-learned file updated with any Session-6 miss-and-fix entries once batches complete.

---

**Awaiting approval (or adjustments via the Chunk 5 open questions) before I start on Batch A.**

---

## RUNNING ASSET LIST — drop-in hooks for the deck

Updated as each slide is built. File names/paths use the stable hooks wired into `index.html` — drop the real asset at the path and the loader swaps it in automatically (CSS mock / placeholder card falls back gracefully if missing).

### Screenshots (phone / app UI)
| Slide | Hook attribute | File path | Status |
|---|---|---|---|
| s4 — What Is This App? | `data-asset="home-wellness"` | `assets/screenshots/home-wellness.png` | ✅ present |
| s14 — Photo Meal Logging | `data-asset="meal-logging"` | `assets/screenshots/meal-logging.png` | ✅ present |
| s15 — Body Map | `data-asset="bodymap-injection"` | `assets/screenshots/bodymap-injection.png` | ✅ present |
| s17 — Learning pathways | `data-asset="learn-pathway"` | `assets/screenshots/learn-pathway.png` | ⏳ needed |
| s25 — F1 home screen (deferred) | CSS mock only (home rings, cards, toast, FAB, bottom-nav) | — | CSS fine; real screenshot optional |
| s30 — Meds calendar popover | `data-asset="meds-popover"` | `assets/screenshots/meds-popover.png` | ⏳ needed |

### Dovetail video clips
| Slide | Hook attribute | File path | Clip content | Status |
|---|---|---|---|---|
| s7 — Anchor quote | `data-video="p07-lifestyle-5348"` | `assets/videos/p07-lifestyle-5348.mp4` | P07 @ 53:48 "It's easy to take the medication and lose weight…" | ⏳ needed |
| s14 — Photo meal logging | `data-video="p02-photomeal-2038"` | `assets/videos/p02-photomeal-2038.mp4` | P02 @ 20:38 "I didn't think it was gonna pick up the whole meal…" | ⏳ needed |
| s15 — Body map | `data-video="p02-bodymap-1546"` | `assets/videos/p02-bodymap-1546.mp4` | P02 @ 15:46 "This is a lot better…" | ⏳ needed |
| s16 — AI Coach | `data-video="p05-coach-3822"` | `assets/videos/p05-coach-3822.mp4` | P05 @ 38:22 "I personally don't have anyone…" | ⏳ needed |
| s18 — Competitive Advantage | `data-video="p03-replace-5234"` | `assets/videos/p03-replace-5234.mp4` | P03 @ 52:34 "I would definitely consider replacing…" | ⏳ needed |
| s26 — P07 Paradox (upcoming) | `data-video="p07-techdiscomfort-0346"` | `assets/videos/p07-techdiscomfort-0346.mp4` | P07 @ 03:46 "There's always some apps that challenge me…" | planned |
| s30 — Meds screen (upcoming) | `data-video="p07-meds-1752"` | `assets/videos/p07-meds-1752.mp4` | P07 @ 17:52 "It literally says meds…" | planned |

### Team headshots
| Slot | Hook | File path | Status |
|---|---|---|---|
| Kyle Blythe | `data-headshot="kyle-blythe"` | `assets/team/kyle-blythe.jpg` | ✅ present |
| Vincent Crossley | `data-headshot="vincent-crossley"` | `assets/team/vincent-crossley.jpg` | ✅ present |
| Lisa Michelson | `data-headshot="lisa-michelson"` | `assets/team/lisa-michelson.jpg` | ✅ present |
| Kamal Shaham | `data-headshot="kamal-shaham"` | `assets/team/kamal-shaham.jpg` | ✅ present |
| Henry Levinson | `data-headshot="henry-levinson"` | `assets/team/henry-levinson.jpg` | ✅ present |
| Allen On | `data-headshot="allen-on"` | `assets/team/allen-on.jpg` | ✅ present |

### Other photos
| Slide | Hook | File path | Status |
|---|---|---|---|
| s9 — Lab overhead | `data-asset="lab-overhead"` | `assets/photos/lab-overhead.jpg` | ⏳ needed (was 2-byte corrupted; re-upload) |

**Graceful degradation:** every missing asset falls back to a styled placeholder — CSS mock, waveform clip card with the quote text, or monogram avatar. The deck works end-to-end without any of the ⏳ items.

