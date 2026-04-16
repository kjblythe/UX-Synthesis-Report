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

