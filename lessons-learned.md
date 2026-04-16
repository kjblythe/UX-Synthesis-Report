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

## Standing rules (re-read before every session)

1. Plan first (todo.md, approved before code).
2. Content must fit the viewport; no overflow ever. Author against a content budget.
3. No AI-slop card patterns. No left-border-card grids. No three-identical-cards.
4. One focal point per slide. If the message takes >2 sec to grasp, simplify.
5. No two consecutive slides share background or layout.
6. Navigator must collapse and expand from both states with visible controls.
7. PDF export must be a button (no reliance on browser print).
8. Phone frames must look real (Dynamic Island, bezels, hardware buttons, squircle).
9. Every data viz must reward interaction (hover/click/expand).
10. Citation chips for every quantitative claim with a per-participant story.
11. Verify at four viewports before declaring done: 1920, 1440, 1024, 390.
12. Translate blueprint into slide-tight copy; don't transcribe paragraphs.
