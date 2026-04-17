# Lessons Learned

Session log of misses, root causes, and fixes. Read at the start of every session.

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



