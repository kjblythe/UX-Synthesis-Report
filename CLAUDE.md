# CLAUDE.md — HTML Presentation Builder

## RULES (read first, follow always)

1. **PLAN BEFORE YOU BUILD.** Never write presentation code without first creating a `todo.md` with your plan — what slides you’re building, what layout/background/visualization each will use, and what content goes where. Share the plan and get explicit approval before building. If anything is ambiguous, ask. Do not guess.
1. **Content must fit the viewport.** No overflow, no scrolling, no clipping. If it doesn’t fit, restructure or split.
1. **No AI-slop.** No cards with left colored borders. No three identical cards in a grid. No purple gradients. No Inter/Roboto/Arial. If you catch yourself reaching for a generic pattern, STOP and find a distinctive approach.
1. **One focal point per slide.** If you can’t identify the primary message in 2 seconds, simplify.
1. **No two consecutive slides share the same layout or background.** Vary dark/light/accent backgrounds. Vary composition. Monotony = failure.
1. **Phone frames must look real.** Emphasized bezels, hardware button hints, correct device proportions, Dynamic Island. No flat rectangles.
1. **Slide navigator must work.** Collapsible left panel with thumbnails, visible by default.
1. **PDF export must work.** Test it. If it breaks, fix it before moving on.
1. **State your principles at session start.** Before coding, state: the color palette, font pairing, anti-patterns you’re avoiding, and these rules. Re-read this file and `lessons-learned.md` at the start of every session.
1. **Checkpoint every 5 slides.** Re-read these rules. Audit the last 5 slides against each one. Compare quality to the first 5 slides. If quality has drifted, fix it before proceeding.

These rules are non-negotiable. They are never relaxed for speed, convenience, or “just this once.”

-----

## Purpose

This project builds production-grade HTML presentations that are visually indistinguishable from work produced by a professional design team. The output is a self-contained HTML file that anyone can open in a browser to present, and that exports cleanly to PDF.

## Skills to Read Before Writing Code

Before writing ANY code, read these skills in order:

1. `/mnt/skills/public/frontend-design/SKILL.md` — design tokens, aesthetic principles, anti-AI-slop patterns. This is the primary design authority.
1. `/mnt/skills/examples/web-artifacts-builder/SKILL.md` — if using React architecture, follow this for bundling to single HTML.
1. `/mnt/skills/examples/theme-factory/SKILL.md` — theming patterns and color/font pairing principles.
1. `/mnt/skills/examples/canvas-design/SKILL.md` — read the craftsmanship principles. The quality bar described there (“meticulously crafted, the product of deep expertise, painstaking attention, master-level execution”) is the quality bar for this presentation.

## Architecture

### Framework Options (choose one based on project needs)

- **Reveal.js** — for simpler presentations. Single HTML file, CDN-loaded, keyboard navigation, speaker notes, print-to-PDF. Good for < 25 slides.
- **React (via web-artifacts-builder)** — for complex presentations with reusable components, state management, and interactive data visualizations. Better for 25+ slides because components enforce design consistency. Bundles to single HTML via Parcel.

### Required Features (every presentation must include these)

**Slide Navigator Panel**

- Collapsible panel on the LEFT side of the viewport
- Shows slide thumbnails with section headers
- Visible and expanded by default on load
- Current slide highlighted
- Click any thumbnail to jump to that slide
- Collapse/expand toggle button
- Panel must not overlap slide content when expanded — slides resize/shift to accommodate
- Panel hidden in print/PDF mode

**Navigation Controls**

- Back/Next arrow buttons positioned OUTSIDE the slide content area, at the bottom
- Keyboard navigation (arrow keys, spacebar)
- Progress bar showing overall position in the deck

**PDF Export**

- Accessible via URL parameter (e.g., `?print-pdf`) or a visible “Export PDF” button
- Print stylesheet that renders each slide as a clean, self-contained page
- Animations resolve to their final/static state in print mode
- Navigator panel hidden in print mode
- Background colors and images must render in PDF (use `-webkit-print-color-adjust: exact` and `print-color-adjust: exact`)
- Charts render as static images or SVG in print mode
- Test PDF export before considering the presentation complete — if it doesn’t export cleanly, fix it

**Self-Contained Output**

- The final HTML file must work when opened locally with zero dependencies
- External libraries loaded from CDN with integrity hashes
- Images can be: (a) base64-encoded inline for true single-file portability, (b) referenced as relative paths if distributed alongside the HTML in a folder, or (c) hosted at a URL
- Fonts loaded from Google Fonts CDN (acceptable external dependency)

## Visual Design Standards

### The Quality Bar

The presentation must look like it was designed by a skilled human designer who spent days on it. It must prompt the reaction: “How did you make this?” If it looks like an AI generated it, it has failed. If it looks like a PowerPoint template, it has failed. If it looks like a default Reveal.js theme with custom colors, it has failed.

### Color & Background Variety

- **Not every slide should have the same background.** Alternate between dark backgrounds, light backgrounds, and accent treatments. Create visual rhythm across the deck.
- Section starter slides should feel distinctly different from content slides
- Use the defined color palette but vary how it’s applied — a dark slide followed by a light slide followed by an accent slide creates energy
- Backgrounds should have depth — subtle gradients, noise textures, or mesh effects. Never flat solid colors unless intentionally minimal.

### Typography

- Choose distinctive fonts. NEVER use Inter, Roboto, Arial, or system defaults. Load from Google Fonts.
- Header and body fonts should be a deliberate pairing with clear contrast
- Establish a strict type scale and use it consistently (display → h1 → h2 → body → caption)
- Numbers and metrics should feel precise — consider tabular/monospace figures for data

### Layout Principles

- **Content must fit within the slide viewport.** No overflow, no scrolling, no clipping, no unintentional overlap. If content doesn’t fit, restructure the content or split the slide. This is non-negotiable.
- **Every slide needs ONE clear focal point.** If multiple elements compete for attention and the viewer can’t immediately understand the hierarchy, simplify.
- **Vary layouts across slides.** Never repeat the same layout on consecutive slides. Alternate between: full-bleed imagery, split layouts, centered hero content, asymmetric compositions, data-forward layouts.
- Leave generous whitespace. Cramped slides are unreadable and unprofessional.
- Maintain consistent margins from slide edges (minimum 5% of viewport)

### What NOT to Do (AI-Slop Patterns)

These are the most common failure modes. Avoid them at all costs:

- **Cards with left-hand colored borders** — the #1 AI-generated aesthetic. Three cards in a row with colored left borders = instant “AI made this” signal. Find a different approach.
- **Uniform card grids** — three identical cards side by side for every grouped content slide
- **Purple/blue gradients** on white backgrounds
- **Excessive centered layouts** — centering everything is lazy. Use intentional alignment.
- **Generic icon + header + description rows** — this is the Material Design default and reads as template content
- **Every slide looking identical** except for the text content — this is monotonous and signals auto-generation

### Animation & Interactivity

The benefit of HTML over PowerPoint is interactivity. Use it purposefully:

**High-Impact Animations (use these)**

- Animated chart reveals — bars growing, lines drawing, numbers counting up on slide entry
- Hover states on data points that reveal additional context
- Smooth, intentional slide transitions with depth (not just fade)
- Staggered content reveals on slide entry (elements appearing in sequence, not all at once)
- Subtle background animations (slow gradient shifts, gentle particle effects) that add life without distraction

**Low-Value Animations (avoid these)**

- Fade-in on every text block — this is the default and adds nothing
- Bouncing or spinning elements — this is never professional
- Animations that delay access to content — if someone has to wait for animation to finish reading, it’s too slow
- Gratuitous parallax — a little adds depth, too much causes motion sickness

**Interactive Elements**

- Charts with hover tooltips showing detail
- Clickable elements that reveal additional context (expandable quotes, detail panels)
- Interactive comparison views (before/after, toggle between views)

### Quote Styling

Participant quotes are the emotional core of research presentations. Style them distinctively:

- Do NOT use cards with left colored borders for quotes
- Options: oversized quotation marks as decorative element, typographic contrast (serif quote text vs. sans body), generous whitespace isolation, subtle background treatment, asymmetric pull-quote positioning
- Always include participant ID and context (age, medication, duration) in a subdued caption style
- Dovetail video clip placeholders should look like embedded video players, not text boxes — include a play button icon, a thumbnail area, and the participant/timestamp metadata

### Phone/Device Frames

When displaying app screenshots in device frames:

- **Ask the user what device the screenshots are from** before building the frame. The frame dimensions, corner radius, bezel proportions, and hardware details change significantly between devices (e.g., iPhone Air vs. iPhone 16 Pro vs. iPhone SE). Get the specific model so the frame is accurate.
- Use CSS-only device frames with correct proportions for the specified device
- **Emphasize the bezels** — the bezel is what makes a device frame look real vs. a flat rectangle. Thin but visible bezels with subtle color differentiation from the screen area. The bezel should have a slight sheen or material quality (subtle gradient or shadow) that suggests glass and metal.
- **Show hardware button hints** on the outside of the device frame — the volume buttons and power/action button on the side edges, rendered as subtle raised elements. This small detail dramatically increases realism. Don’t overdo it — they should be hints, not focal points.
- Include a **Dynamic Island** (for modern iPhones) or appropriate sensor housing for the specified device
- Proper corner radius matching the real device (iPhones have very specific corner curves — they’re not simple border-radius circles)
- The screenshot must fill the screen area without cropping or stretching
- Frame should cast a subtle shadow for depth and feel like it’s floating slightly above the slide surface
- Never use low-fidelity wireframe boxes or flat rectangles as device frames
- Consider a subtle reflection or gloss effect on the screen area for additional realism

### Data Visualization

- Use Chart.js, D3.js, or equivalent for charts — never static images of charts
- Charts should animate on slide entry (bars growing, lines drawing)
- Use the presentation’s color palette for chart colors
- Add hover interactions that reveal data point details
- Include clear labels, but don’t overcrowd — let the visual tell the story
- Benchmark/reference lines should be visually distinct (dashed, different color) from data
- Consider unconventional data displays where appropriate — not everything needs to be a bar chart

### Citation Chips & Interactive Data Expansion

This is a signature feature of HTML presentations that PowerPoint cannot replicate. Research presentations always have a deeper data spine behind them — participant-level observations, quotes, behavioral notes. Surface that depth through interactive expansion without cluttering the slide.

**How it works:**

- When a slide shows tabular data (task completion, feature validation matrix, comparison tables), individual data cells can be **clickable/tappable**
- Clicking a data point (e.g., a ❌ failure or ⚠️ partial completion) reveals a **popover or expansion panel** with richer context: what happened for that participant on that task, a relevant quote, the behavioral observation
- The popover should be styled as a clean, floating card with: the participant ID, the contextual detail, and optionally a quote with attribution
- Popovers dismiss on click-outside or an explicit close button
- **This does not compromise visual clarity** — the slide surface remains clean and scannable. The depth is there for anyone who wants to drill in, but it never clutters the default view.

**Citation chips** can also appear inline within narrative text:

- A small, styled chip (e.g., a pill-shaped badge with “P07” or “3/7”) that, on hover or click, reveals the supporting evidence
- Think of them like footnotes, but interactive and contextual rather than relegated to the bottom of the page
- Chip styling should be subtle — understated color, small type — so they don’t compete with the primary content

**Use cases:**

- Task completion table: click a “Partial” cell → popover shows what happened (“P04 went to meds section first, self-corrected after 30 seconds. SEQ: 6.”)
- Feature validation matrix: hover over a ⚠️ → shows the participant’s reaction (“P01 refused to engage: ‘I hate this.’ But immediately followed with ‘I actually like the app though.’”)
- Quote slides: a small citation chip next to a quote links to the full exchange context from the transcript
- Metric callouts: clicking “6.4/7” reveals the per-participant breakdown

**Data source:** The research spine (spine.md) contains all participant-level detail. The blueprint (blueprint.md) specifies which data points appear on each slide. Cross-reference both to populate the expansion content.

**Critical constraint:** Interactive expansions must degrade gracefully for PDF export — the popover content should either be hidden entirely in print mode or rendered as footnotes/appendix content.

## Quality Assurance Process

### Before Declaring Any Slide Complete

1. **Viewport check:** Does ALL content fit within the visible slide area without overflow or scrolling?
1. **Overlap check:** Do any elements unintentionally overlap? Text over images? Labels over chart elements?
1. **Hierarchy check:** Can you identify the slide’s primary message within 2 seconds? Is the reading order clear?
1. **Variety check:** Does this slide look different from the previous and next slides?
1. **Print check:** Does this slide render correctly in PDF export mode?

### Before Declaring the Presentation Complete

1. Export to PDF and verify every slide renders correctly
1. Open the HTML file locally (not on a dev server) and verify it works self-contained
1. Test the slide navigator — does it show all slides with correct thumbnails? Does click-to-jump work?
1. Test keyboard navigation — do arrow keys advance slides correctly?
1. Review the full deck for visual rhythm — is there enough variety in backgrounds, layouts, and treatments?
1. Check all charts — do they animate on entry? Do hover states work?

## Project Structure

```
project-root/
├── CLAUDE.md                  (this file)
├── design-brief.md            (project-specific creative direction)
├── blueprint.md               (slide-by-slide content spec)
├── spine.md                   (deep research data — reference only)
├── index.html                 (the presentation — or src/ if using React)
├── assets/
│   ├── logo.svg               (brand logo)
│   ├── screenshots/           (app screenshots for phone frames)
│   └── backgrounds/           (any background images/textures)
└── dist/                      (bundled output if using React)
    └── presentation.html      (self-contained final file)
```

## Workflow

1. **Read the design brief** — understand the project-specific creative direction, color palette, and tone
1. **Read the blueprint** — understand the slide-by-slide content, visualization specs, and quote placements
1. **Establish the design system** — build the CSS custom properties, type scale, color tokens, and reusable component patterns BEFORE building individual slides
1. **Build the proof of concept** — the first 5-6 slides establish the visual language (typically: title slide, executive summary, anchor quote, hero data visualization, feature highlight, finding slide)
1. **Review with stakeholder** — iterate on the design system before building remaining slides
1. **Build remaining slides in batches** — 5-10 slides at a time, maintaining design consistency
1. **QA pass** — viewport checks, overlap checks, PDF export, navigator, keyboard nav
1. **Final polish** — animation timing, micro-interactions, hover states, background treatments

## Session Discipline & Context Integrity

### The Problem

Over long sessions, adherence to design principles degrades. By slide 30, the agent has forgotten the rigor it applied to slide 5. The RULES at the top of this file prevent that. This section provides the operational framework.

### Planning Protocol (MANDATORY)

Before building ANY slides, create a `todo.md` file with:

1. **Which slides** you’re building this session (e.g., “Slides 7-15”)
1. **For each slide:** the layout approach, background treatment (dark/light/accent), primary visualization or visual element, key content summary, and any interactive elements
1. **Ambiguities or questions** — anything unclear from the design brief or blueprint

Share `todo.md` with the user and **wait for explicit approval.** Do not write presentation code until the plan is approved. Update `todo.md` as slides are completed.

### Session Start Protocol

1. **Read CLAUDE.md** — especially the RULES at the top
1. **Read `lessons-learned.md`** if it exists
1. **Read the design brief**
1. **Review the last 3-5 slides built** for visual continuity
1. **State your principles** — colors (hex), fonts, anti-patterns, confirm you’ve read the rules
1. **Create/update `todo.md`** and share for approval

### Mid-Session Checkpoints (every 5 slides)

1. Re-read the RULES at the top of this file
1. Audit the last 5 slides against each rule
1. Check for layout monotony — if 3+ slides look similar, redesign at least one
1. Compare quality against the proof-of-concept slides — if drifted, fix before proceeding

### One Task Per Session

Do not build the entire presentation in one session. Context degrades. Quality degrades. Ship in batches, review, continue.

### Lessons Learned Log

Maintain `lessons-learned.md` in the project root. After each session, append what went wrong, root cause, and fix. Read it at the start of every subsequent session. Create it after the first session if it doesn’t exist.

### When in Doubt

1. Re-read the RULES
1. Re-read the design brief
1. Look at the proof-of-concept slides
1. Choose the MORE distinctive option
1. If still uncertain, **ask the user**

## Key Reminders

- **PLAN FIRST.** No code without an approved `todo.md`. No exceptions.
- The design brief is the creative authority. The blueprint is the content authority. This CLAUDE.md is the quality authority.
- When in doubt, simplify. One clear message per slide beats three competing elements.
- The quality bar: people should ask “how did you make this?”
- The anti-pattern bar: if it looks like AI made it, it failed.
