---
name: slide-show
description: Build a single self-contained HTML file that opens as a real fullscreen presentation — one slide per screen, arrow-key/space/swipe navigation, slide counter, and progress bar, with no internet or dependencies. Use when the user wants presentation-style HTML slides, a deck that plays fullscreen in the browser, a clickable/keyboard-navigable slideshow, an interactive web deck, or an HTML presentation that looks and behaves like PowerPoint/Keynote rather than a scrolling web page. This skill is HTML-only and deliberately picks bold, varied visual themes; it asks for the company's main brand colors up front. For .pptx export or long-form scrolling story/portfolio pages, use slide-storyteller instead.
---

# Slide Show

## What this skill makes

One **self-contained `.html` file** that, when opened in a browser, behaves like a live presentation:

- each slide fills the whole screen (one slide visible at a time, not a long scroll)
- navigation by arrow keys, space/backspace, `Home`/`End`, on-screen arrows, click zones, and touch swipe
- a slide counter and progress bar, plus a `F` key to toggle true browser fullscreen
- everything inlined — CSS, JS, and SVG — so it works offline and is easy to share as one file

This skill is **HTML-only**. If the user asks for PowerPoint or `.pptx`, hand off to the `slide-storyteller` skill. If they want a long scrolling story/portfolio page, that is also `slide-storyteller`.

When the user wants a professional, executive, strategy, board, investor, or consulting-firm (McKinsey/BCG/Bain) style deck, read `references/consulting-style.md` before planning the spine, and bias toward a restrained theme.

## Operating Standard

Make decks that feel like a designer made them on purpose — bold, distinctive, and tailored to the brand. Optimize for a sharp story and a confident visual system, then make it play smoothly fullscreen.

**Be creative and vary the look every time.** Do not fall into one default palette or layout. Never default to a nature/garden/sage-green theme unless the user explicitly asks for it. Each new deck should pick a deliberately different visual direction (see `references/themes-and-color.md`).

## Intake — ask for brand colors first

Before building, ask the user for their **brand basics**, since this drives the whole look. Ask concisely and in one message:

- "What are your ~3 main brand colors (or a vibe/company to match)? If you're not sure, I'll pick a bold theme for you."
- audience and the deck's purpose (inform, persuade, pitch, teach, update, celebrate)
- rough slide count and tone (bold, corporate, playful, editorial, techy, elegant)
- any must-include content, logo, or constraints

Rules for handling the color answer:

- If the user gives colors or a brand, build the palette around them (see the palette-building rules in `references/themes-and-color.md`).
- If the user gives nothing or says "you pick," **choose one bold theme from the theme library** and state which one you picked in one line. Do not stall waiting for an answer, and do not fall back to a generic or nature default.
- Proceed with reasonable assumptions for anything else; state assumptions briefly.

## Workflow

1. Run intake. Lock the palette (brand-driven or a chosen bold theme).
2. Write a one-sentence promise: what the audience should believe, understand, or do after the deck.
3. Build a claim spine — one sharp claim per slide (**subject + verb + object + stake**), not a topic label. Write all the slide titles first; reading just the titles top-to-bottom should tell the whole story. For executive/consulting decks, follow the action-title and pyramid rules in `references/consulting-style.md`.
4. Pick a visual theme and a type pairing from `references/themes-and-color.md`. Commit to one bold direction; do not blend many styles.
5. Plan slide formats with variety. Across the deck, use several distinct layouts (cover, big-statement, data/metric, two-column, image/visual, quote, list/steps, closing). Avoid two adjacent slides sharing the same layout.
6. Build the deck from the scaffold in `references/fullscreen-html-deck.md`. Keep it one self-contained file with the fixed-stage scaling system so slides look identical on any screen.
7. Use inline SVG for shapes, icons, charts, and accents. Do not invent official logos or brand marks; use user-provided assets for those.
8. Verify before responding (see Verification).
9. Run a quick critique pass: name the two weakest slides and fix at least one by switching its layout or strengthening its proof object.

## Build Rules

- **One file.** Output a single `.html` with inline `<style>` and `<script>`. No CDNs, no external fonts unless the user approves a web-font link; prefer strong system-font stacks.
- **Fixed stage, scaled to fit.** Lay out every slide on a fixed stage (default `1280×720`, 16:9) and scale it to the viewport with a transform, centered and letterboxed. This keeps spacing and alignment identical on laptops, monitors, and phones — like a real deck.
- **One slide per screen.** Exactly one slide is visible at a time; advancing replaces it (no scrolling between slides).
- **Navigation must work:** `→`/`Space`/`PageDown` next, `←`/`Backspace`/`PageUp` prev, `Home`/`End` jump, on-screen prev/next buttons, left/right click zones, touch swipe, and `F` for the Fullscreen API. Update the counter and progress bar on every change. Support `?slide=N` deep-linking and remember position with the URL hash.
- **Type and grid.** Use 1–2 typefaces and a clear size scale. Headlines are claims and get the most weight; supporting text is visibly lighter.
- **Color semantics.** Build a small palette (background, ink, 1 primary, 1–2 accents) from the brand colors and apply it as CSS variables. Ensure text/background contrast stays readable (aim WCAG AA).
- **No placeholders.** No `Lorem`, `TODO`, or empty slides in the delivered file.

## Verification

Before responding, check the saved file with local checks:

- file exists and size is greater than zero
- HTML parses without obvious errors and contains exactly one `<section class="slide">` (or equivalent) per intended slide
- the navigation script is present and the slide count in JS matches the markup
- no placeholder copy remains
- spot-check that the stage-scaling math is wired (a resize handler exists)

## Delivery

- Save to an obvious `output/` folder (or the user's requested folder) with a useful filename, e.g. `quarterly-pitch.html`.
- In the final response, give the exact `.html` path first, then: the theme/palette used, slide count, and how to navigate (arrows / space / `F` for fullscreen).
- Keep the response short. Offer one concrete next step (e.g., "want a different theme, or more slides?").

## Quality Bar

Every slide should have:

- a headline that is a claim, not a label
- one primary focal element (a number, chart, image, quote, or diagram) — not a wall of bullets
- generous whitespace and clear hierarchy
- alignment to the stage grid

The deck should pass:

- **fullscreen check**: opening the file shows slide 1 filling the screen; arrows and swipe move between slides; the counter and progress bar update
- **variety check**: several distinct layouts; no two adjacent slides look the same
- **brand check**: the palette reflects the user's colors (or the chosen bold theme), and is applied consistently
- **ten-second check**: each slide's point is obvious at a glance
- **portability check**: the file opens offline with no missing resources

## References

- `references/fullscreen-html-deck.md` — the copy-ready HTML/CSS/JS scaffold for a fixed-stage, keyboard/swipe-navigable fullscreen deck, plus the layout components and responsiveness rules.
- `references/themes-and-color.md` — how to ask for and build a palette from brand colors, and a library of bold, varied themes to avoid defaulting to one look.
- `references/consulting-style.md` — MBB/executive deck discipline: pyramid structure, action titles, narrative spine, one-message-per-slide, slide anatomy, and visual restraint.
