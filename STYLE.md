# Consult Animation Style — Reusable Prompt

Use this as a styling prompt to build a *new* animation in the same visual/motion
family. Replace the bracketed `[...]` slots with your own content.

---

Build a short, silently-looping animated GIF (~7s, 15fps) that demonstrates
**[YOUR PRODUCT/FLOW]** as a clean, government-services-style dashboard
walkthrough. Match the following design system exactly.

**Concept & tone:** Calm, official, data-forward. A cursor quietly guides the eye
through 3 focus areas — no clicks, no checkboxes toggling, no text typing. Motion
is gentle and purposeful; nothing bounces or flashes.

**Canvas & scale:** Logical 560×390 design space, rendered at scale 1.8 from the
top-center. White cards float on a warm off-white page background.

**Color palette (CSS vars):**
- page background `#f3f2f1`
- cards `#ffffff`
- primary accent (active/links/rings) pink `#c01b7b`
- soft accent fills pale pink `#f7d0e8`
- secondary accent teal `#1d7a6e`
- neutral bars / borders mid-grey `#b1b4b6`
- body text dark-grey `#505a5f`, headings near-black

**Typography:** Small, tight sans-serif. Section labels are 8px bold, uppercase,
letter-spaced, in muted grey. Numbers are tabular. Generous line-height, lots of
breathing room.

**Layout skeleton:** Slim top header (logo dot + wordmark left, ghost nav pills
right) → a prominent query/title bar → a two-column body: a narrow left panel with
multiple scrollable sections, and a wide right column holding a feature card on
top, a tab bar, and a swappable content area (table ⇄ list).

**Motion system (framer-motion):**
- Two easings only: entrances use `EASE_OUT = [0.16, 1, 0.3, 1]`; movement/morphs
  use `EASE_IN_OUT = [0.4, 0, 0.2, 1]`.
- Elements mount with a small fade + 6–16px slide/scale; stagger rows by ~40–50ms.
- Bars grow from 0 width; numbers count up.

**Focus device (signature element):** A single spotlight rectangle that *slides*
between focus areas — a 1.5px pink ring plus a full-screen dark scrim
`box-shadow: 0 0 0 9999px rgba(11,12,12,0.16)`. The focused card gently scales to
1.02 and lifts above the scrim. A small cursor glides smoothly between targets
(no click pulses).

**Scene structure (~7.2s loop):** 3 focus beats + a brief settle.
1. **[Area 1]** — focus the left panel, scroll down through its sections.
2. **[Area 2]** — focus the feature card on top (e.g. a small **doughnut chart**
   that draws in via animated `pathLength`).
3. **[Area 3]** — a tab switch swaps the main content area (e.g. table → list)
   with a cross-fade + horizontal slide.
4. **Hold** — clear the focus, fade the cursor out, settle for the loop.

**Deliverable:** A seamlessly looping silent GIF (the first frame equals the start
of scene 1), exported at 1008×702.
