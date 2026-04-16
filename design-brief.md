# DESIGN BRIEF: HTML Research Presentation

## What This Is

An HTML presentation for an internal research readout at Boehringer Ingelheim. This is a usability testing report for a GLP-1 medication support app. The audience is business stakeholders who need to be convinced this app is worth building. The tone is professional research — but the medium is HTML, so we should take full advantage of what HTML can do that PowerPoint can’t.

## Why HTML Instead of PowerPoint

I chose HTML specifically because I want something that goes beyond static slides. I want dynamic elements, rich interactivity, and production-grade visual polish. If this looks like “PowerPoint but in a browser,” we’ve failed. The benefit of HTML is mouseover interactions, animated data visualizations, dynamic background elements, smooth transitions, and a level of typographic and spatial control that .pptx can’t achieve.

## Framework Choice

Consider whether **Reveal.js** or **React (via web-artifacts-builder skill)** is the better fit for this project. React gives you reusable components (SlideFrame, QuoteCard, ChartSlide, PhoneFrame, SectionStarter) that enforce design consistency across 40 slides. The web-artifacts-builder skill has bundling scripts that produce a self-contained HTML file. Either framework is acceptable — the output must be a single HTML file that works when opened locally with zero server dependencies.

## Design Direction

### Skills to Reference

Before writing any code, read these skills:

1. `frontend-design` — primary design authority for aesthetic direction, anti-AI-slop patterns, typography, color, motion, spatial composition
1. `web-artifacts-builder` — if building with React, use this for bundling to single HTML
1. `theme-factory` — theming patterns and color/font pairing principles
1. `canvas-design` — read the craftsmanship principles for the quality bar (“meticulously crafted, painstaking attention, master-level execution”)

### Tone: Editorial / Refined Research

Think: a beautifully designed annual report meets a research journal meets a premium SaaS marketing site. Not playful, not brutalist, not startup-y. This is pharma — it needs to feel trustworthy, precise, and sophisticated. But NOT boring. NOT corporate template. The design should feel like it was made by a design team that cares, not auto-generated.

### CRITICAL DESIGN PRINCIPLES (read these before writing any code)

**1. Background variety is essential.** Not every slide should be dark green. Some slides should be dark green, some should be white/light, some could use other treatments. The agent is allowed and encouraged to make bold choices to create variety and visual interest across the deck. A presentation where every slide has the same background color is monotonous and lazy. Alternate between dark and light, use the palette range.

**2. Do NOT resort to AI-slop card styling.** The most common failure mode for AI-generated presentations is cards with left-hand colored borders arranged in a grid. This looks generic and immediately signals “AI made this.” Avoid it. Find more creative, distinctive ways to present grouped content — asymmetric layouts, typographic hierarchy, pull quotes with spatial composition, data as the visual element itself, full-bleed imagery, overlapping elements with intention.

**3. Content must ACTUALLY fit within the slide.** Before finalizing any slide, verify that the content fits within the viewport without overflow, clipping, or overlap. If there’s too much content for a slide, the layout and content structure needs to change — either reduce the content, split into multiple slides, or restructure the layout. Elements must not overlap unintentionally. Text must not be truncated. This is non-negotiable.

**4. Visual clarity above all else.** The meaning of each slide must be immediately intuitive. If multiple elements compete for attention and the viewer can’t immediately understand the hierarchy (what to read first, what the key takeaway is, where the supporting detail lives), the slide is a failure. Every slide needs a clear focal point. Every slide needs a clear reading order. When in doubt, simplify.

**5. PDF export and slide navigator are required features.** The presentation must include Reveal.js print-pdf support (via `?print-pdf` URL parameter for Chrome print-to-PDF). It must also include a collapsible slide navigator panel with slide thumbnails that is present by default. The navigator should show section structure and allow jumping to any slide.

### Color Palette (from our existing BI X presentation template)

The prior BI X readout uses a dark muted forest green on section title slides — that’s the anchor color I want to carry forward. It establishes the brand connection without the neon blue from BI X branding (which I hate — do NOT use it).

- **Primary dark/background:** Dark muted forest green (from the section title slides in the reference presentation) — NOT navy/charcoal. This is the dominant color for slide backgrounds and section starters. Think deep, desaturated green-black, not bright green.
- **Primary accent:** Teal/seafoam (`#0D9488` to `#14B8A6` range) — used for data highlights, key metrics, interactive elements, CTAs
- **Secondary accent:** Soft gold/amber (`#F59E0B` or warm yellow) — used sparingly for warnings, callouts
- **Text primary:** White or near-white on dark backgrounds
- **Text secondary:** Muted sage or blue-gray (`#94A3B8`) for supporting text
- **Card/surface:** Semi-transparent cards (`rgba(255,255,255,0.05)` to `0.08`) — NOT opaque white cards
- **Positive/success:** Green (`#10B981`)
- **Negative/caution:** Soft red/coral (`#EF4444`)
- **Quote styling:** Distinguished from body text — find a distinctive treatment that is NOT a card with a left colored border. Consider: oversized quotation marks, a subtle background shift, typographic contrast (serif vs. sans), spatial isolation with generous whitespace, or a combination.
- **DO NOT USE:** Bright/neon blue, BI X light blue branding color, or any saturated blue as a primary element

If you have access to the reference presentation (PDF available at https://coderift.io/Research_Readout_AB_Testing.pdf), use the section title slide backgrounds as your primary dark color reference.

### Typography

- **Display/Headers:** Something with character — NOT Inter, NOT Roboto, NOT Arial. Consider: Outfit, Sora, General Sans, Satoshi, or similar modern geometric sans with personality. Load from Google Fonts.
- **Body:** Clean, highly readable. Can be the same family at lighter weight, or a complementary face.
- **Quotes:** Should feel distinct — either a subtle serif for contrast, or the display font at a different weight/style with clear visual framing.
- **Data/metrics:** Tabular or monospace-influenced for numbers that need to feel precise.

### Visual Identity Elements

- I will upload the **BI X logo** — use it on the title slide and subtly in a footer/corner on content slides
- I will upload the **“X” graphic** — this is a large, stylized “X” that appears as a watermark/background element on some slides in our template. Use it as a subtle, low-opacity background element on section starters or key slides
- **“ONLY FOR INTERNAL USE”** should appear in a subtle footer

### Backgrounds & Atmosphere

- Dark theme throughout (matching our app’s premium feel and our existing presentation style)
- NOT flat solid colors — use subtle gradients, noise textures, or mesh gradients for depth
- Section starter slides should feel distinctly different from content slides (perhaps a more dramatic background treatment)
- Consider subtle animated elements: a slow gradient shift, floating particles, or geometric patterns that move slowly — nothing distracting, just alive

## Interactivity & Dynamic Elements

This is what makes it worth being HTML instead of PowerPoint:

### Must-Have

- **Chart.js animated charts** that draw/reveal on slide entry:
  - SEQ bar chart with benchmark zone (the hero data viz)
  - Satisfaction radar chart
  - Task completion visualization
- **Hover states on data points** — mousing over a bar in the chart shows the detail (participant breakdown, context)
- **Quote cards with subtle hover effects** — lift, glow, or reveal additional context on hover
- **Smooth slide transitions** — not just fade, but something with depth (slide + fade, or a subtle parallax)
- **Animated number reveals** — key metrics (6.4/7, 6.6/7) should count up when the slide enters

### Nice-to-Have

- **Interactive feature validation matrix** — hovering over a cell reveals the participant quote or context
- **Citation chips** — small inline badges (e.g., “P07” or “3/7”) that reveal supporting evidence on hover/click. Think interactive footnotes. See CLAUDE.md for full specification.
- **Clickable data cells** in tables — clicking a task completion result (e.g., ❌ Fail or ⚠️ Partial) opens a popover with what happened for that participant. The spine.md has all participant-level detail to populate these.
- **Animated engagement spectrum** (for the reflections finding) — participants slide into position along a scale
- **Parallax depth** on section starters — background moves at different rate than foreground text
- **Progress indicator** showing where you are in the presentation

### Phone Frame for App Screenshots

I will upload actual screenshots from the app prototype taken on an **iPhone Air**. The device frame should:

- Accommodate iPhone Air screenshot dimensions: **2736 × 1260 pixels, ~19.5:9 aspect ratio**
- **Emphasize the bezels** — visible, with material quality (subtle gradient/sheen suggesting glass and metal)
- **Show hardware button hints** on the outside edges — volume buttons and power button as subtle raised elements
- Include the **Dynamic Island** (not a notch — iPhone Air has Dynamic Island)
- Proper iPhone corner radius (not a simple border-radius — Apple’s corners are squircles)
- Cast a subtle shadow for depth
- The screenshot must fill the screen area without cropping or stretching
- CSS-only construction is fine — no SVG needed — but it must look like a real device, not a wireframe box

## Dovetail Video Clip Placeholders

Several slides reference embedded video clips from our Dovetail research platform. Create styled placeholder cards for these with:

- 🎥 icon
- Participant ID and timestamp
- The quote being referenced
- A “Play Clip” button (non-functional placeholder)
- Styled to feel like an embedded video player, not just a text box

## Slide Navigator (REQUIRED — enabled by default)

- Collapsible side panel showing slide thumbnails and section titles
- Visible by default when the presentation loads (user can collapse it)
- Current slide highlighted in the navigator
- Click any thumbnail to jump to that slide
- Section headers in the navigator for easy section jumping
- Back/Next buttons (in addition to keyboard nav)
- Progress bar showing overall position

## PDF Export (REQUIRED)

The presentation must support clean PDF export. If using Reveal.js, this is via `?print-pdf` URL parameter for Chrome print. If using React, implement a print stylesheet or export button. The design must degrade gracefully for print — animations become static states, hover states show default content, the slide navigator is hidden in print mode. Each slide should render as a clean, self-contained page. Background colors and images must appear in the PDF. **Test PDF export before considering the presentation complete.**

## What to Build for the Proof of Concept (5-6 slides)

Build these slides to establish the look and feel:

1. **Title slide** — “GLP-1 Support App: Pre-Pilot Usability Testing Results” with subtitle, BI X branding placeholder, atmospheric background
1. **Executive Summary** — context paragraph + 3 key findings with the layout and typography established
1. **Anchor Quote** — full-slide quote: “It’s easy to take the medication and lose weight, but you have to change your lifestyle.” — P07, with context line and Dovetail clip placeholder
1. **SEQ Explainer** — the 1-7 scale with color zones, benchmark at 5.5, our score at 6.4 — THIS is the hero data viz. Chart.js animated, with the benchmark zone clearly shaded and our score revealed with a count-up animation
1. **Photo Meal Logging** (from “What Resonated”) — a feature highlight slide with an app screenshot in a phone frame, key data point (6/7 chose photo unprompted), and 2 participant quotes with styling
1. **Finding 1 — Visual Differentiation** — annotated screenshot placeholder in phone frame with callout annotations pointing to problem areas, plus key quotes

These 6 slides should establish: the color system, typography, quote styling, data visualization approach, phone frame treatment, section starter vs. content slide distinction, animation/transition approach, and overall polish level.

## Files I’m Attaching

- `GLP1_Presentation_Blueprint_v2.md` — the full 39-slide blueprint with all content, quotes, and visualization specs
- `GLP1_Usability_Synthesis_Spine.md` — the complete data synthesis (1,500+ lines) for reference if you need deeper context on any finding
- BI X logo (image file)
- App screenshots (multiple image files)
- [Optional] The “X” background graphic

## What I DON’T Want

- **Cards with left-hand colored borders in a grid layout** — this is the #1 AI-slop aesthetic. If your instinct is to put three cards side by side with colored left borders, STOP and find a different approach.
- Generic “AI slop” aesthetics — no purple gradients, no Inter font, no card-heavy Material Design look
- PowerPoint-in-a-browser — if it looks like Google Slides, we’ve failed
- Excessive animation that distracts from content — animations should serve the data, not perform for their own sake
- Low-fidelity phone mockups — if we’re showing app screenshots, the device frame needs to look real
- Cookie-cutter Reveal.js themes — no default themes, everything custom
- **Every slide looking the same** — vary backgrounds (dark/light), vary layouts, vary visual treatments. Monotony = laziness.
- **Content that overflows or overlaps** — if the content doesn’t fit the slide, restructure the content or split the slide. Never let text clip, truncate, or pile up.
- **Competing focal points** — every slide needs ONE clear primary element. If you can’t tell what the slide is about in 2 seconds, simplify.
