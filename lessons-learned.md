# Lessons Learned

Session log of misses, root causes, and fixes. Read at the start of every session.

---

## ⚠️ IMPORTANT — read before building more slides

Slides 1–30 are shipped. Sessions 7+ will build 31–38. Before you touch `index.html`, internalise the conventions below so you don't fight them.

### ⚠️ ALSO READ — "Session 6 addendum — tone recalibration + layout adjacency" at the bottom of this file

That block logs the single most-drifted-from rule across sessions 5 and 6: **we are NOT doing pithy marketing-y content. Let the content speak for itself.** The addendum has a concrete before/after table from the Session 6 rework pass — read it and match the "After" voice. It also covers the phone-slide adjacency rule (don't put phones on the same side in consecutive slides, even across bg-family changes).

### Deferred slides — both reinserted in Session 6

Both POC slides previously under `.slide-deferred` have been reinserted at their blueprint positions:

| Token (former) | Now | Section |
|---|---|---|
| `.s-deferred-seq` | **Slide 21** — What We Measured · Understanding SEQ | Detailed Results |
| `.s-deferred-f1`  | **Slide 25** — Finding 1 · Visual Differentiation | Design Findings & Opportunities |

No more deferred slides remain. CSS selectors fully renamed to `.s21` / `.s25`. If you ever defer a slide again, use `.slide-deferred` + a unique scoped class and grep both CSS and JS for the token before/after every rename (Session 6 caught a stale `.s4` reference in `bindSEQ()` because the Session 5 rename only covered CSS).

### The structural invariants — DO NOT override these

1. **Slide base positioning is `position: absolute; inset: 0; opacity: 0 → 1 on .active`.** Never set `position: relative` on a `.slide-*` variant. Causes a 0-height slide; absolute children with `bottom:` land above the canvas. (Session 5, Bug 1.)
2. **CSS scoped selectors must match the HTML class token.** When a slide's class changes (e.g. `.s2` → `.s6`), `grep -c '\.s2\b'` BEFORE changing the HTML, update every selector in the same commit, replace both `".s2 "` and `".s2."` forms. (Session 5.)
3. **Same-specificity collisions matter.** Introducing `[data-x] { position: relative }` or similar utility at the same specificity as base rules on positioned containers (`.screen`, `.phone-screen`) wins in the cascade and breaks layout. Always scope with `:not()` or raise specificity deliberately. (Session 5, Bug 2.)
4. **Phone-frame standard is 380 px wide, 8 px bezel.** The `loadDataAssets` JS hardcodes these for the aspect-ratio math (`phoneW=380; bezel=8`). If you ever change the CSS width, change the JS too.
5. **Slide canvas is sacred.** Every popover clamps against `#canvas.getBoundingClientRect()`, not the window. Don't break this.

### Chip / popover contract

- Any `<button data-cite="key">` OR `.chip` / `.chip-trigger` opens a popover with `CITATIONS[key]`. The handler is global (document-level click) — don't rebind per-slide.
- **A popover must deliver new information** the slide surface does not show (participant profile detail, cohort breakdown, behavioural moment, "why"). If it just restates slide content, cut it.
- The `CITATIONS` content bank already covers 30+ keys. Reuse. Namespace new keys by feature (`feat-*`, `task-*`, `team-*`, `p01`–`p07`, `meal-*`, `learn-*`, `refl-*`, `body-*`).
- Chips must be self-explanatory **before** click — the slide stands alone, the chip deepens.

### PDF-export safety (html2canvas)

The "Export PDF" button uses html2canvas inline. Known footguns — avoid all three:

- **Don't use `object-fit: cover` on `<img>`.** html2canvas renders it distorted. Use `background-image: url(...)` + `background-size: cover` on the container instead. (That's why Session 5 switched team headshots from `<img>` child to bg-image on `.team-avatar`.)
- **Don't use `inset: 0` shorthand on positioned overlays.** Use explicit `top / right / bottom / left`. html2canvas support for shorthand is inconsistent across versions.
- **Don't use flex `gap`.** Use `margin` on children. Pre-2023 html2canvas versions flatten `gap` to zero, causing overlap.
- **Don't use CSS-border triangles** (`border-left: 9px solid X; border-top: 6px solid transparent`). Use inline SVG data-URIs instead. Border-triangles render as rectangles or vanish in some html2canvas passes.
- **Test PDF export whenever you touch a phone, clip card, table, or overlay.** Playwright `await page.evaluate(() => document.getElementById('btn-pdf').click())` and inspect the resulting render.

### Asset hooks — naming and folders

| Content | Folder | Filename pattern | Hook attribute |
|---|---|---|---|
| Headshots | `/assets/team/` | `{firstname-lastname}.jpg` | `data-headshot="firstname-lastname"` |
| Screenshots (phone) | `/assets/screenshots/` | `{screen-name}.png` | `data-asset="slug" data-asset-folder="screenshots" data-asset-ext="png"` |
| Other photos | `/assets/photos/` | `{subject}.jpg` | `data-asset="slug"` (folder default = photos) |
| Dovetail videos | `/assets/videos/` | `p{NN}-{topic}-{mmss}.mp4` | `data-video="slug"` on the `.clip-card` or `.bm-clip` wrapper |

All four pipelines have graceful fallbacks (monogram / CSS mock / placeholder card). Missing files don't break the deck.

**Sanity-check file sizes when an asset "doesn't load."** Session 5 lost an hour to a 2-byte `lab-overhead.jpg` that was actually just `\r\n` — a broken upload. Real JPEGs are tens-to-hundreds of KB, PNGs are hundreds of KB to low MB.

### Tone discipline — applies to every new slide

Voice = a principal investigator presenting evidence to a funding committee that already knows the team and the program. Internal readout, not pitch deck.

**Banned phrases** (observed in Sessions 1–5 and corrected):
- "The North Star" · "One direction" · "the breakout feature" · "Universal approval" (as a headline)
- "drove the strongest engagement" · "daily-adoption driver" · "the most requested X path"
- "generated genuine delight" · "resonated with users" (OK in section title, not as a verb in body)
- "cleared the bar" · "adoption curve" · "retrofitting"
- "A day in the life of the app" · "natural rhythm of a day"
- Any sentence shaped "Most X are Y. This does Z." (pitch-deck pattern)

Read every new headline out loud as if you were a PI. If it would make a VP of R&D wince, cut it.

### Visual system invariants

- **Backgrounds rotate.** No two consecutive slides share bg family AND layout family. Section starters (5, 8, 12, and future 20, 24, 34) intentionally reuse the watermarked starter style — but they're never adjacent.
- **All section starters use `.starter-a`** (mint numeral, upper-right X watermark, no rotation). Consistency was the user's explicit call (session 5).
- **Agenda items are placeholder click-to-jump targets.** Once sections 4–6 are built, wire agenda `<div class="agenda-item">` → `goTo(sectionStarterIdx)`.
- **Benchmark story is tiered** — Slide 6 hero headline + `?` chip mini-explainer on the `6.4` KPI pill → Slide 11 visual band + `+0.9` delta badge → Slide 21 full SEQ deep-dive with per-participant distribution. Preserve this three-tier flow when building Slide 21.
- **Type scale baseline at 1920 native:** eyebrow 13 / label 12 / body 17–19 / lead 20 / h3 34 / h2 46 / h1 50–54 / section-starter numeral 320. Presentation-legibility calibrated (session 5).
- **Phone magnifier** is universal on any `.phone .screen.has-asset`. Zoom 2.2×, loupe 400 px. Works on S4, S14, S15 today; any future phone-screenshot slide inherits it automatically.

### Framework handoff

- Single `index.html`, vanilla JS + CSS, Chart.js loaded only where needed, html2canvas + jsPDF inlined for the PDF button.
- `SLIDES` array drives the navigator. Add entries in order when building new slides. The `paintThumb` function needs a matching `key` branch per slide type — section starters, light slides, dark slides, and hero-viz slides each have stylised mini-previews.
- `.slide.active` flip, `.reveal.dN` delayed opacity/transform entrance, `@media print` override — all wired and working. Don't rebuild.

---


## Session 1 — 2026-04-16 — Style system + 6-slide POC

### Miss: Navigator was not collapsible from its expanded state
- **What:** I added a `#nav-toggle` button, but its CSS only revealed it (`display: flex`) when `#app.nav-collapsed` was already true. From the expanded state, no visible control existed to collapse the panel — only the keyboard `n` shortcut, which is undiscoverable.
- **Root cause:** I conflated "the floating reveal button" (visible only when collapsed) with "the close affordance" (must always be visible when expanded). Two distinct UI states require two distinct controls or one persistent control.
- **Fix:** Persistent collapse/expand affordance. When expanded, an `×`-style chevron sits inside the panel header. When collapsed, a chevron-right re-opens it from the left edge.
- **Rule going forward:** every interactive panel needs a visible close in its expanded state. Discoverability > minimalism for navigation chrome.

### Miss: Nav arrows present but underweighted; not discoverable
- **What:** Back/next arrow buttons were placed at the bottom-center, small, low-contrast.
- **Root cause:** I treated them as secondary to the navigator panel. CLAUDE.md is explicit that arrows must work standalone.
- **Fix:** Larger edge-anchored chevron buttons (left and right of the slide canvas) plus the bottom-center group. Arrows must be obvious from any device.

### Miss: PDF "export" relied on the user's Cmd+P print dialog
- **What:** The `?print-pdf` URL parameter triggered `window.print()`, dumping the user into the browser's native print UX.
- **Root cause:** I read CLAUDE.md too literally — it accepts URL-parameter PDF — and missed that the user wants a download-PDF button as a first-class deliverable.
- **Fix:** Add `jsPDF` + `html2canvas` (CDN) and a visible "Export PDF" button. One click → 6-page PDF downloads. Uses the existing `@media print` styles internally so the output matches what the browser would print, but no user dialog required.

### Miss: Slide 2 content overflowed at production viewport
- **What:** The asymmetric 3-finding layout looked fine in my smoke screenshots at 1920×1080, but visually overflowed at the user's viewport.
- **Root cause:** I measured at full canvas size where the content fit by ~155px of headroom. But headroom depends on font loading order, line-wrap, and the noise overlay — fragile margin. I did not enforce a content budget.
- **Rule going forward:** every slide must be authored against a strict content budget, NOT "let's see if it fits." For a 3-section content slide on 1920×1080: header band 56px, section gap 56px, body grid ≤ 720px, footer band 56px. If copy exceeds the budget, cut copy first, restructure second, split the slide third — not vice versa.
- **Fix:** trim slide 2 finding copy to 1 declarative sentence + 1 KPI line each. Detail moves to interactive expand on click.

### Miss: Slide 4 (SEQ) had no interactivity
- **What:** The SEQ scale animated on entry but had no hover or click states. CLAUDE.md is unambiguous that HTML's primary justification over PowerPoint is interactivity.
- **Root cause:** I prioritized "looks beautiful" over "uses the medium." The chart was a static-looking image that happened to animate once.
- **Fix:** Click on the 6.4 marker (or "see the breakdown" CTA) expands the scale to overlay all 6 task SEQ scores. Hover any task pill shows the full task name, completion rate, and a representative quote.
- **Rule going forward:** every data viz slide must answer "what does the viewer learn by interacting?" If the answer is nothing, the slide is failing the medium.

### Miss: No citation chips
- **What:** CLAUDE.md specifies citation chips as a signature feature. I shipped zero.
- **Root cause:** Scope creep risk — felt deferrable. It is not.
- **Fix:** introduce the `<button class="chip">` component with hover/click popover this session. Apply to highest-traffic citations (P-IDs, n/7 ratios) on at least slides 2, 5, 6.

### Miss: Slides did not hold 16:9 / scale gracefully across devices
- **What:** Canvas was nominally 1920×1080 with `transform: scale()`, but padding asymmetry, no aspect-ratio enforcement, and no mobile considerations meant the slide could feel cramped or misproportioned on tablets/phones.
- **Root cause:** I designed for a single viewport (desktop laptop) and assumed scaling "would work."
- **Fix:** enforce `aspect-ratio: 16/9` on the canvas wrapper, use `min(scaleX, scaleY)` faithfully, drop padding on small viewports, auto-collapse navigator under 900px width, add touch swipe, ensure controls scale with thumb-friendly hit targets.
- **Rule going forward:** every responsive change is verified at four viewports — 1920×1080, 1440×900, 1024×768 (iPad), 390×844 (iPhone).

### Miss: Title slide had a redundant lower-left X watermark
- **What:** I added a second X graphic in the lower-left at 8% opacity to "balance" the composition. It read as a duplicate / artifact.
- **Root cause:** Decorative overreach. One feature element per slide; the giant X is the watermark, the small X is noise.
- **Fix:** remove the second watermark. The single X carries the composition.
- **Rule going forward:** if I'm adding a second instance of a decorative motif, ask "is this serving the focal point or distracting from it?" Default to the cleaner option.

### Miss: Heavy text density, especially on findings slides
- **What:** Across slides 2, 5, 6, body copy was longer than necessary.
- **Root cause:** I copied the blueprint paragraph-style language verbatim instead of authoring slide-tight copy.
- **Rule going forward:** the blueprint is the source of TRUTH. The slide is the source of CLARITY. Translate, don't transcribe. Each text block on a slide should fit a "read in 4 seconds" budget; deeper detail moves to citation-chip popovers, click-to-expand panels, or speaker notes.

---

## Session 2 — 2026-04-16 — Pass 2 fixes: nav, PDF, SEQ, chips

### Miss: Overcorrected slide 2 — too sparse after trimming
- **What:** Responding to "it overflows" from pass 1, I trimmed slide 2 copy down to one-line headlines + KPI pills. User flagged it swung too far — now nothing explains the findings.
- **Root cause:** I treated "content budget" as a literal word-count minimization rather than a layout-fit constraint. The correct response to overflow is restructure, not amputate.
- **Rule going forward:** content budget = what fits at target type sizes, not the absolute minimum. Split the difference: keep 1 supporting sentence per finding beyond the headline + KPIs. If it overflows, raise the info density via chips/popovers, not by deleting the context.

### Miss: Citation chip content was shallow — mostly quote repetition
- **What:** Chips opened to popovers that often repeated the same quote already on the slide. No new information value.
- **Root cause:** I treated chips as "show the quote in more detail." They are "show the evidence BEHIND the claim." Two different jobs.
- **Rule going forward:** A chip popover must deliver something the slide surface does NOT show: participant profile context (age/med/duration/tech-comfort/current app), the behavioral moment (what they did, where they looked, what they said unprompted), how it compares across the cohort, the WHY behind the inference. If a popover just restates a slide element, it's dead weight.
- **Fix:** rewrite every chip to source from `spine.md`. For P-IDs: profile + current app + key moment. For n/7 ratios: list of WHO + a one-line behavioral note per participant. For findings: observation → inference → implication.

### Miss: Used jargon ("CSS fix", "HTML") in business-stakeholder copy
- **What:** Slide 6 and slide 2 finding 3 used "CSS fix — not a redesign." Technical audiences understand; BI business stakeholders see noise.
- **Root cause:** Implementation vocabulary leaked into communication vocabulary.
- **Rule going forward:** prefer "UI styling fix," "visual refinement," "visual polish" vs "foundational architecture issue," "structural redesign." Audience is business, not engineering.

### Miss: Key claims not self-explanatory before clicking
- **What:** "P07: lowest tech comfort, navigated everything" with a "[paradox]" chip was cryptic. The user has to click to understand why it matters.
- **Root cause:** I front-loaded the chip as the explanation. A chip is supplemental depth — the slide must stand alone.
- **Rule going forward:** every claim reads as a complete thought on the slide surface. The chip deepens; it does not define. Test: if I hide all the chips, does the slide still make sense?

### Miss: SEQ slide data viz too static-looking; type too small; benchmark under-emphasized
- **What:** The scale animates once on entry but still reads as a static image. Benchmark label is a small pill. Tick numbers, zone labels, and task labels are hard to read at production scale. When the breakdown expands, the scale shifts position (layout jump).
- **Root cause:** Designed for 1920×1080 desktop at 1.0 scale, which everyone will only see at fractions. Also treated the benchmark and our-score as equal marks when the whole point is the distance between them.
- **Rule going forward:** type calibration pass at the end of every session — no body label under 14px at native 1920 (renders ~10px at common viewport). The SEQ benchmark should read as "what we beat," not a passing landmark. Visual gap/bracket between the two markers telling the +0.9 story directly.
- **Rule going forward:** any expansion that changes slide geometry should be animated in a reserved space — no "stage shifts up when you click".

### Miss: Shipped without a fullscreen / present-mode affordance
- **What:** No way to go fullscreen and hide browser chrome. Expected for any presentation tool.
- **Fix:** Fullscreen button in the top bar + `F` keyboard shortcut, uses Fullscreen API.

---

## Session-2 additions to standing rules

13. No jargon on slide surfaces (CSS/HTML/frontend terms). Translate to audience vocabulary.
14. Chip popovers deliver new information (context, cohort breakdown, behavioral moment) — never repeat slide content.
15. Every slide claim must be self-explanatory without the chip. Chip = deeper dive, not the punchline.
16. Type scale calibrated for rendered size, not 1920 native. Minimum 14px for labels, 17-19px for body, at 1920.
17. Any interactive expansion must reserve its space — no layout jump when opening/closing panels.
18. Fullscreen / present mode is table stakes; add it upfront, not as a polish task.

---

## Session 3 — 2026-04-16 — Depth, chips, distribution model

### Miss: Half the "chips" weren't chips
- **What:** Slide 2 mixed clickable `.chip` buttons with static `.kpi-pill` spans styled identically. The hover/click inconsistency broke the mental model — users tried to click pills that weren't interactive.
- **Root cause:** Style reuse without affordance parity. If two elements look the same, they must behave the same.
- **Rule going forward:** if a pill carries a stat, it is clickable. Every pill opens a popover sourced from the spine. The only exceptions are pure typographic labels (eyebrows, tags, meta captions) — and those should not look like pills.

### Miss: Popover typography had no rhythm
- **What:** label (small uppercase) sat directly against title (bold sans) with no padding and minimal visual distinction. Subtitle read as "slightly smaller body text."
- **Fix:** label is now italic Fraunces on a hairline divider, title is sans-serif bold below, body has explicit margin below the title, meta/lists sit under a second hairline. The popover now has three clear bands (label → title → body) not one cluttered block.
- **Rule going forward:** popovers are mini-layouts. Treat them with the same typographic hierarchy discipline as a slide — label band, title band, body band, meta band. Dividers earn their keep.

### Miss: Marketing voice leaked into research-readout copy
- **What:** Headlines like "The app landed," "the breakout," "the adoption gatekeeper" read as pitch-deck language. Audience is a pharma business stakeholder — they want accurate + punchy, not hype.
- **Rule going forward:** headlines must pass the "would a principal investigator say this?" test. Reach for declarative, evidence-first phrasing: "The experience resonated. All seven participants expressed willingness to use the app daily." is better than "The app landed." Punchy is fine; promotional is not.

### Miss: SEQ data viz had visual collisions
- **What:** "OUR MEAN 6.4 / 7" floated above the track at a horizontal position that overlapped with the "+0.9 Gap" label in the same vertical band. The big numeral occupied a wide visual footprint; the gap badge tried to live in the same strip. Also — expand CTA sat too close to the metric rows below it.
- **Fix:** moved the gap bracket + label BELOW the track in the negative space between the benchmark tag and the score marker column. Added 40+ px of padding above the below-scale panel, another 40 px inside it before the metric grid, and positioned the expand button with generous top-margin on its own row.
- **Rule going forward:** when building a composite data viz, sketch the vertical bands each element will own BEFORE placing pieces. If two elements need the same horizontal strip, one moves vertically; they do not share.

### Distribution model: videos + truly-single-file
- **What the user actually wants to ship:** `index.html` + `assets/videos/` (when clips exist). A zip you can email or drop on a USB. Nothing else.
- **What this implies for the build:**
  1. **Images** → base64-inlined in the HTML (or inline SVG). No separate `assets/images/` distribution folder.
  2. **JS libraries** → inlined directly in `<script>` blocks. The HTML is 600–800 KB with jsPDF + html2canvas inlined; this is fine. No `assets/vendor/` in the distribution.
  3. **Fonts** → Google Fonts CDN link (acceptable external dependency; degrades to system-serif fallback if offline).
  4. **Videos** → `assets/videos/` with relative `<video src>` paths. Too large to base64 (any reasonable clip is tens of megabytes). The Dovetail clip card detects whether the video file is present; if so, renders a real `<video>` element; if not (single-file email share), shows the styled thumbnail placeholder.
- **Rule going forward:** the file tree the user ships is the file tree the build assumes. Default to inline for everything EXCEPT videos. Never rely on an `assets/vendor/` or `assets/reference/` that the user has to remember to include.

---

## Session-3 additions to standing rules

19. Every visible pill/badge is a chip-trigger; no static stat pills.
20. Popover typography = label band / title band / body band / meta band, separated by hairlines with real padding.
21. Headlines pass the "would a principal investigator say this?" test. No marketing-deck vocabulary.
22. Composite data viz: sketch vertical bands per element before placing anything. No two elements share a horizontal strip unintentionally.
23. Distribution = `index.html` (everything inlined) + `assets/videos/` (when present). Nothing else. Images are base64-inline; JS libs are `<script>`-inline.
24. Dovetail clip component degrades: if the video file is present, render an actual `<video>`; if not, show the styled thumbnail placeholder. Both render correctly in the PDF export.

---

## Session 4 — 2026-04-16 — Containment + the /7 overlap

### Miss: Popovers overflowed the slide canvas
- **What:** Chips near the bottom of a slide (e.g. Exec Summary Finding 03, Slide 5 quote chips, Slide 6 summary chip) opened popovers that extended BELOW the visible slide edge into the dark letterbox. The popover was clamped to the window, not the slide canvas. On a 16:9 slide inside a non-16:9 viewport, that meant popovers could render in the scaled-away whitespace — invisible.
- **Root cause:** I positioned the popover in viewport coordinates and clamped to `window.innerWidth` / `window.innerHeight`. But the slide canvas is a 1920×1080 transformed element inside the window; its visual bounds are smaller than the window when the viewport isn't 16:9.
- **Fix:** positioning now reads `#canvas.getBoundingClientRect()` and clamps the popover inside those bounds with 16px padding. Flip-above activates when the natural below-placement would exceed the canvas bottom (not the window bottom). Fallback: if neither above nor below fits cleanly, place in the side with more room.
- **Rule going forward:** **the slide canvas is sacred.** No interactive element — popover, tooltip, modal, drawer — may extend outside the canvas bounds. Always clamp against `#canvas.getBoundingClientRect()`, never against the window.

### Miss: SEQ /7 unit still collided with the marker line
- **What:** The "/ 7" subunit sat below the "6.4" numeral in a flex-column; the mint vertical line from the marker dot passed up through the "/ 7" text, visually cutting the glyphs.
- **Fix:** re-parented `/ 7` INSIDE the `.big` span as an absolutely-positioned child, anchored to the baseline of 6.4 and offset 8px to the right. The marker line now passes cleanly through the center of 6.4 alone; the /7 floats off to the right as a small unit label.
- **Rule going forward:** when a callout has a directional line (arrow, connector, axis), treat the primary glyph as the anchor. Units, denominators, and annotations that aren't the number go NEXT to the number, never above or below where the line tracks through.

---

## Session-4 additions to standing rules

25. The slide canvas is sacred. Popovers/tooltips/modals clamp against `#canvas.getBoundingClientRect()` with padding. Never extend beyond the slide visual frame, even if the viewport has room.
26. Flip-above behavior for popovers uses canvas-bottom, not window-bottom. Measure popover height after append (offsetHeight) before final positioning.
27. When a numeric callout has a directional marker line, the line anchors on the primary glyph only. Units and subunits float beside, not above/below.

---

## Session 5 — 2026-04-17 — Build slides 1–15 (in progress)

### ⚠️ IMPORTANT — DEFERRED POC SLIDES TO REINSERT IN SESSION 6+

Two POC slides are held under `.slide-deferred` at the bottom of `index.html`. They are NOT part of the blueprint's slides 1–15 and must be reinserted at their correct blueprint positions when we build the rest of the deck. **Do not lose these.**

| POC class | Blueprint slide | Section | Reinsert during |
|---|---|---|---|
| `.s-deferred-seq` (originally `s4`) | **Slide 21 · SEQ Scores & Task Completion** | Task-by-Task Results | Session 6 (slides 16–23) |
| `.s-deferred-f1` (originally `s6`) | **Slide 25 · Finding 1 — Visual Differentiation & Affordance Clarity** | Design Findings & Opportunities | Session 7 (slides 24–33) |

**Reinsertion protocol:**
1. Re-read the blueprint entry for the target slide position to confirm content still aligns.
2. Move the `.slide-deferred` section back to its correct sequential position in the HTML.
3. Swap the class back from `.slide-deferred` → `.slide`, rename the section class (e.g. `.s-deferred-seq` → `.s21`).
4. Update the `SLIDES` array to include it, renumber `.foot-page`, and verify `data-on-enter="animateSEQ"` still fires.
5. Verify popover `data-cite` references, chip behavior, and navigator thumbnail still match.

Both slides passed QA in sessions 1–4 with full polish (SEQ chart interactions, P07 paradox table, phone-frame annotations). Re-use AS-IS unless the blueprint has evolved.

### Session 5 plan (this session)

Build blueprint slides 1–15 in three batches of 5. Batch A first. See `todo.md` for the full plan.

### ⚠️ IMPORTANT — TONE DISCIPLINE (standing rule; applies to every slide going forward)

**What:** Body and headline copy on slides 2 and 4 (and the title slide subtitle) drifted into pitch-deck marketing voice. Examples that were shipped and must be avoided:
- "A small, cross-functional team built this." (slide 2 headline)
- "One team, one prototype, one week in the field." (slide 2 lede)
- "A GLP-1-specific companion that turns the medication into a lifestyle — in one app." (slide 4 headline)
- "Most patients are stitching together three or four tools…" (slide 4 lede)
- "Seven patients. Six tasks. One day in the life of the app." (title slide)

**Root cause:** I treated audience-facing copy the same way I'd treat website hero copy — punchy, evocative, story-shaped. But this is an **internal research readout to BI business stakeholders who already know the team, the program, and the product**. Self-introduction, mission language, and evocative consolidation narratives are NOT what they need. They need findings and evidence, stated precisely.

**Rule going forward:** the voice of this deck is a **principal investigator presenting evidence to a funding committee they already work with**. That means:
- Declarative, not evocative. "Six core-team members built this prototype." not "A small, cross-functional team built this."
- Factual, not aspirational. "The prototype integrates medication logging, nutrition tracking, an AI coach, behavioral learning, and reflections." not "…turns the medication into a lifestyle."
- Concrete counts and nouns beat adjectives. "Seven patients. Six tasks. Five hours of recorded session." not "One day in the life of the app."
- No "story-shaped" lede patterns ("Most X are Y. This does Z."). Lede should orient, not persuade.
- No self-congratulation. The findings speak for themselves — don't editorialize the work.
- No "in one app," "one team," "this is what X looks like when…" — those are all marketing constructions.

**Test before shipping any copy:** read it out loud as if presenting to a VP of R&D who has been briefed on BI X for years. If any sentence would make them wince, reach for the delete key.

### ⚠️ Session 5 content fix log

- **Tone pass 1** — rewrote slide 1 subtitle, slide 2 headline + lede, slide 4 headline + lede per rule above. Kept the structure and information; changed the voice.
- **Slide 2 restructure** — 6 primary team members in a 2×3 grid (was 1×6 row). Roles moved off the visible surface into chip popovers (surfaced on click) along with email addresses. Aligns with rule 19 (every visible pill/badge is a chip-trigger) and avoids the "CV-style role cards in a grid" anti-pattern.
- **Slide 4 phone** — screenshot was cropped because `object-fit: cover` forced the screen aspect to match the frame. Switched to `object-fit: contain` + dynamic aspect-ratio match (the phone frame now adopts the loaded image's natural dimensions), so the frame wraps the image instead of cropping it.
- **Slide 5 content not rendering** — the `.ss-inner > ss-focus` flex-column with `justify-content: space-between` collapsed content to the bottom edge off-canvas in certain viewport scales. Rebuilt to match slide 1's proven layout pattern (direct children of `.slide-frame`, no extra wrapper, explicit left alignment).
- **Henry crop** — `object-position` moved from 22% → 8% (head was at the very bottom of the source image; needed to shift the crop further toward the top of the frame).

### ⚠️ IMPORTANT — CSS same-specificity rule collisions (standing rule)

In one session I shipped two separate bugs with the same root cause. Both needed Playwright-rendering to catch, because by-eye inspection of the HTML/CSS looked correct.

**Bug 1 — slide 5 empty.** I declared `.slide-section-starter { position: relative }`. Specificity 10. The base `.slide { position: absolute; inset: 0 }` is also specificity 10, declared earlier. Mine won. A relative section without explicit height collapses to 0 when its children are absolute. The `ss-body { bottom: 120px }` then rendered at y = -468px — above the canvas. Content was "gone."

**Bug 2 — slide 4 phone image collapsed.** I declared `[data-asset] { position: relative }` to give asset overlay containers a positioning context for absolutely-positioned child images. Specificity 10. The base `.screen { position: absolute; inset: 0 }` is also specificity 10, declared earlier. Mine won on the `.screen[data-asset]` element. Inset:0 stopped applying, the flex container collapsed to padding height (70px), and the real screenshot rendered at 70px tall — "barely displaying."

**Rule going forward:**

- When introducing a utility rule like `.foo { position: relative }` or `[attr] { display: ... }`, always scope it so it does NOT collide with already-positioned container classes. Use `:not(.screen):not(.phone-screen):not(.phone)` or equivalent exclusions.
- **Never override the base `.slide` positioning** (`position: absolute; inset: 0`) on a slide variant. The entire deck relies on that invariant. If a section needs extra effects, use `::before`/`::after` with `inset: 0` — which work because `.slide` is already positioned.
- Before declaring a new `position`/`inset`/`display` rule, grep the CSS for earlier rules targeting the same elements with the same specificity. If equal-specificity rules exist, either raise specificity intentionally (compound selector) or scope with `:not()`.
- **Validation protocol:** Playwright-render every layout change. `getBoundingClientRect()` tells you whether an element is where you expect it. For any slide that visually "isn't showing content," the diagnosis is almost always position/size collapse — not z-index, not opacity. Check dimensions before blaming anything else.

### ⚠️ IMPORTANT — CSS scoping must follow slide class renames

When the POC slides were renumbered to their blueprint positions (old `s2`→`s6`, old `s3`→`s7`, old `s5`→`s14`, old `s4`/`s6` → deferred), I updated the HTML `class` attributes but left the CSS selectors scoped to the OLD class names (`.s2 .exec-grid`, `.s3 .quote-wrap`, `.s5 .meal-grid`, …). 140+ rules stopped matching. The slides rendered with structure only — no per-slide typography, grid layout, or component styling. Exec Summary and Anchor Quote both shipped "looking wrong" for several sessions before the user flagged it.

**Rule going forward:** **any time a slide's class token changes (e.g. `.s2` → `.s6`), grep the entire CSS for `\.<old-class>\b` and update every selector in the same commit.** The class token is structural — changing it is a rename, not an edit. Treat it like renaming a function: update the declaration AND every call site, or the rename is incomplete.

**Safe rename protocol:**
1. Before changing a slide's class, `grep -c "\.<old-class>\b"` to know how many rules you're about to break.
2. Rename any class that will be claimed by another slide FIRST (e.g. rename old `.s6` → `.s-deferred-f1` before renaming `.s2` → `.s6`). Otherwise the second rename steps on the first.
3. Use `replace_all: true` on `".<old> "` (trailing space — descendant combinator) and `".<old>."` (compound selector). Watch out for dropped trailing space — if the replacement loses the combinator, compound selectors like `.s6 .foo` turn into `.sNew.foo` (matches the same element with both classes, which is never what you want).
4. Verify with Playwright-render immediately.




## Session 6 — 2026-04-17 — Build slides 16–30 + reinsert deferred POCs

Built 13 new slides and reinserted the two deferred POC slides (SEQ at 21, F1 at 25). Deck is now 30 slides, end of Section 6 is in reach (slides 31–38 remain for Session 7).

### Miss: Rename protocol dropped the descendant-combinator space — TWICE

**What:** Renamed `.s-deferred-seq` → `.s21` using `Edit` with `old_string=".s-deferred-seq "` (trailing space) and `new_string=".s21"` (no trailing space). Result: every descendant selector like `.s-deferred-seq .seq-tasks` became `.s21.seq-tasks` — a COMPOUND selector that matches an element with BOTH classes on it, not a descendant. 63 selectors silently broke. Same bug repeated on `.s-deferred-f1` → `.s25` rename (19 selectors).

**Root cause:** The session-5 rule in this file literally warns against this: "Watch out for dropped trailing space — if the replacement loses the combinator, compound selectors like `.s6 .foo` turn into `.sNew.foo` (matches the same element with both classes, which is never what you want)." I read the rule, wrote the code, shipped the bug.

**Fix sequence (applied for both seq and f1):**
1. Edit 1: `.s-deferred-X ` → `.sNEW` (drops space, breaks things — didn't realize)
2. Edit 2: `.s-deferred-X.` → `.sNEW.` (for compound selectors, correct)
3. Edit 3 (the fix): `.sNEW.seq-` → `.sNEW .seq-` globally (restore descendant combinators)
4. Edit 4: `.sNEW.f1-` → `.sNEW .f1-`, `.sNEW.callout` → `.sNEW .callout`, `.sNEW.connectors` → `.sNEW .connectors` (exhaustively fix compound cases)
5. Also: `.s4.active` and `.s4.seq-expanded` (stale session-5 leftovers) had to be renamed to `.s21.active` / `.s21.seq-expanded` with the same care.

**Verification that became essential:** After every rename, run `grep -oh "\.sNEW\.[a-zA-Z0-9_-]\+" index.html | sort -u` to list every compound-selector pattern. If any of the results look like child-element class names (e.g. `.s21.seq-tasks`, `.s25.f1-grid`), they are broken — those classes live on children, not on the slide itself.

**Rule going forward — updated rename protocol:**
- **Never** do `".s-OLD " → ".sNEW"` as a single replace_all. The replacement must preserve the descendant combinator.
- **Do** `".s-OLD " → ".sNEW "` (trailing space preserved) for descendant form.
- **Do** `".s-OLD." → ".sNEW."` for compound form.
- **Better yet**, add a verification step to the protocol: after any slide-token rename, `grep "\.sNEW\.[a-zA-Z0-9_-]\+"` — manually confirm that every result is a legitimate compound (like `.s21.active`, `.s21.seq-expanded`), NOT a child-class pattern. If you see `.s21.seq-tasks`, the space is missing.

### Miss: Stale JS references to old class tokens survived the session-5 rename

**What:** In the session-5 rename of `s4` → `s-deferred-seq`, the CSS got renamed but the JS `document.querySelector('.s4')` in `bindSEQ()` did not. Because the deferred slide was `display:none`, the broken JS never triggered visibly. When I reinserted and renamed to `.s21` this session, I had to find and fix the JS reference too.

**Root cause:** The session-5 rename-bug protocol covers CSS but not JS. Class tokens appear in both.

**Rule going forward:** Before any slide-class rename, grep for the OLD token across the entire file, not just the `<style>` block. That means:
- CSS: `grep "\.s-OLD\b"`
- JS querySelectors: `grep "querySelector.*s-OLD\|querySelectorAll.*s-OLD"`
- JS class manipulation: `grep "classList.*s-OLD\|className.*s-OLD"`
- HTML class attributes: `grep "class=.*s-OLD"`
- Data attributes: `grep "data-.*s-OLD"` (unlikely but cheap to check)

All four places need to be updated in the same commit as the CSS rename.

### Win: Running asset list in `todo.md`

Added a consolidated asset-needed table to `todo.md` with file-path + hook-attribute + status for every screenshot, Dovetail clip, headshot, and photo across the deck. Discovered two gaps the user can fill async (learn-pathway screenshot, meds-popover screenshot) without blocking the build, and documented all five upcoming Dovetail clips needed for Session 6 slides. Graceful degradation was already wired in every case — the deck works end-to-end without any of the missing files, but tracking them explicitly saves time later.

### Win: Content-consolidation judgment call on Slide 21

Blueprint split the SEQ coverage across two slides: 21 (explainer) and 22 (per-task bar chart). The deferred POC slide combined both into one interactive surface (click-to-expand). Kept the consolidation — frees Slide 22 for post-session satisfaction (which needs the room). Flagged the deviation from blueprint in the plan; user approved.

### Win: Lollipop plot over radar chart for Slide 22

Blueprint suggested a radar or grouped bars for post-session satisfaction. I built a lollipop plot + cohort dot-strip instead. Reasoning: radar under-emphasizes meaningful differences at this data's tight range (6.4–6.7) and visually over-emphasizes irrelevant angular artifacts. Lollipop reads honestly at this range. User delegated the viz call.

### Win: Phone-frame layout was preserved, not repeated

Slides 14, 15, 25, 30 all carry phone frames. All four are separated from each other by non-phone slides. Rotation rule held. Slide 16 (AI Coach) explicitly did NOT use a phone frame, breaking a near-miss with slide 15's phone-left layout.

### Win: Every chip delivers new info

Verified by reading each CITATIONS popover against the slide surface. No popover restates slide content. Every pill opens to a participant profile, cohort breakdown, behavioural moment, or "why" detail sourced from the spine.

### Standing-rule additions from Session 6

28. **Always grep for the rename token in BOTH CSS and JS before renaming a slide class.** The rename is not complete until `querySelector`, `classList`, and inline data-attribute references have been updated alongside the CSS.
29. **Verify compound-selector correctness after a descendant-combinator rename.** Run `grep "\.sNEW\.[a-zA-Z0-9_-]\+"` and confirm every hit is a legitimate compound, not a child-class pattern.
30. **Running asset list in `todo.md`** is a first-class artifact. Update it every time a new asset hook is wired in. Helps async file prep.
31. **Blueprint is the content authority, not the strict slide-count authority.** If two blueprint slides merge cleanly into one interactive HTML slide (like SEQ 21+22), make the call deliberately and flag for review.


## Session 6 addendum — tone recalibration + layout adjacency

### ⚠️ IMPORTANT — Tone drift caught by the user on every new content slide in 16–30

After shipping slides 16–30, the user flagged that the content had "made a sales pitch" across the entire range. This is the same miss logged in Session 5 — I caught it there, logged it, and then drifted right back into the pattern when building new slides. Locking this in more forcefully now.

**The rule:** *We are not doing pithy marketing-y content. Let the content speak for itself. Balance punchy with professional research readout; when in doubt, go professional.*

**Specific patterns that are banned** (added to the Session-5 list — these were all present in Batch A/B/C and had to be removed):

- **Headlines that editorialise the finding instead of stating it.** Before: *"Users tried to log from the meds calendar. They were right — the screen just doesn't support it yet."* After: *"Three participants tried to log from the meds calendar. The instinct is correct; the screen does not yet support it."* The editorial move is "They were right." Drop it — the reader sees that themselves.
- **Dramatic italic emphasis in headlines ("None of *them*," "They were *right*," etc.).** Italic is for the rare anchor-word that earns the emphasis, not for dramatising the beat. When an entire headline carries drama, the deck loses authority.
- **Over-punctuated headline rhythms ("X. Y. Z — W.").** Pitch-deck cadence. Prefer a complete declarative sentence, or a stat + explanatory clause.
- **"landed in the excellent band"** / **"cleared the bar"** / **"tells the same story"** / **"nudged scores down"** — narrative verbs substituting for the actual number. State the number. "Every measure scored 6.4 or higher" not "every measure landed in the excellent band."
- **"visual tweak"** / **"easy wins"** / **"no redesign"** / **"just a CSS fix"** — casual product-team vocabulary. Translate for a PI audience: "visual-styling change," "low-effort remediation," "no information-architecture changes."
- **Meta-text that reads as internal deck taglines** (e.g. *"Honest ledger · 4 limitations"*, *"Both paths. Not a choice."*). Prefer descriptive counts / labels: *"4 prototype limitations"*, *"Design principle + 4 recommendations."*
- **"Everything X-specific"** type catch-all feature claims. Always name the specific features instead. *"+ Everything GLP-1-specific"* → *"+ Medication, Nutrition, AI coach, Body map, Learning."*
- **"The ground X doesn't cover"** / **"the things X doesn't do well"** — colloquial clause endings. If the contrast matters, write it as a full clause; if it doesn't, cut it.
- **Emphasised-bold-in-running-prose** (`<strong style="font-weight:600">still said she would…</strong>`). The emphasis editorialises. Let the sentence stand without ornamentation.
- **"It tells the same story" / "It's the same story" rhythm** for connecting evidence rows. Prefer "follows the same pattern" or "the evidence is consistent."
- **"It's just me, myself, and I"-style colloquial framings** in editorial text (fine in participant quotes). Body copy stays plain-English-declarative.

**Calibration procedure** for every new headline / body paragraph:

1. Read the copy out loud as if presenting it to a principal investigator on a funding committee. If any clause makes a clinical VP of R&D wince, it is wrong.
2. Check for each pattern above. If a sentence matches one, rewrite until it doesn't.
3. Check that every claim is a *stateable fact* — a count, a rate, a quote, a behavioural observation — rather than an editorial framing of facts.
4. Italic emphasis is for one anchor phrase per slide maximum, and only when it survives the "would a PI italicise this?" test.
5. Look at the previous slide's content and this slide's content side-by-side. Is the voice consistent? If this slide feels more enthusiastic, trim it.

**Example before/after set** (shipped corrections from the Session 6 rework pass):

| Before (pitch-y) | After (PI voice) |
|---|---|
| "Valued for exploration, questions, and coaching feedback — the things UI screens don't do well." | "Valued for exploration, open questions, and coaching feedback." |
| "The format works. Content resonated across every participant who found it." | "Format understood. Content engaged with by every participant who reached the section." |
| "Five participants named the app they currently use. *None of them* covers the full GLP-1 journey." | "Five participants named the app they currently use. None covers the full GLP-1 journey." |
| "Every measure landed in the *excellent band*. Every participant scored above 5.8." | "Every measure scored 6.4 or higher. Every participant averaged 5.8 or above." |
| "A few prototype constraints nudged specific scores down. *They aren't in the product.*" | "Four prototype constraints affected specific scores. None is present in the production build." |
| "Every remediation below is a *visual tweak*. No structural changes. No new screens. No redesign." | "Every remediation below is a visual-styling change. No information-architecture changes. No new screens." |
| "Chat and UI aren't a choice. *They do different jobs.*" | "Chat and UI are not substitutes. They address different user needs." |
| "Users tried to log from the meds calendar. *They were right* — the screen just doesn't support it yet." | "Three participants tried to log from the meds calendar. The instinct is correct; the screen does not yet support it." |

### Miss: Layout adjacency between phone slides

Built s16 (AI Coach, paper) with phone-RIGHT + content-LEFT, the same spatial composition as s15 (Body Map, dark) which has phone-RIGHT + stat/quotes-LEFT. Different bg families, same phone-side positioning. The user caught the near-miss: even with a bg-family change, a phone slide immediately after another phone slide with the phone on the same side reads as repetitive.

**Fix:** swapped to s16 phone-LEFT + content-RIGHT, s17 phone-RIGHT + content-LEFT. Implementation via CSS `order` on children (DOM preserved for screen-reader logical order).

**Rule going forward — phone slide adjacency:** *when two phone slides are adjacent (even with bg-family change), the phone must be on opposite sides.* Track the phone-side in the rotation audit alongside bg family and layout family.

### Standing-rule additions (32–37)

32. **No editorial framing of facts.** State the number, name the behaviour, quote the participant. Don't tell the reader what the evidence means — they read the slide faster than you can write the interpretation.
33. **Dramatic italic emphasis is for anchor words, not headline drama.** Maximum one italic per slide, and only if the anchor word earns it.
34. **Translate casual product-team vocabulary** (visual tweak, easy win, no redesign, just a CSS fix) into research-neutral equivalents (visual-styling change, low-effort remediation, no information-architecture changes). Business stakeholders are not engineers; don't assume the dev vocabulary.
35. **Meta captions are descriptive, not editorial.** "4 prototype limitations" not "Honest ledger · 4 limitations." "Design principle + 4 recommendations" not "Both paths. Not a choice."
36. **Feature-coverage claims are specific, not catch-all.** "+ Medication, Nutrition, AI coach, Body map, Learning" beats "+ Everything GLP-1-specific" every time.
37. **Phone slides separated by a non-phone slide, OR phone on opposite sides.** Treat phone-side as a rotation axis alongside bg family and layout family.

### Session-start protocol update

Add to the existing Session Start Protocol (Session 1 rules):

- **Read the "tone recalibration" block above (this section) first.** It is the single most-drifted-from rule across sessions 5 and 6.
- **Before writing any new slide copy, read the shipped slides immediately before and after the target position** and note the tone register. Match it. If the surrounding deck reads clean-declarative, do not drift into punchy-editorial.
- **Maintain the phone-side rotation log** alongside bg/layout when auditing new slides.

