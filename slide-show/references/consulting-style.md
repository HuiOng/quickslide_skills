# Consulting-Style Decks (MBB / Executive)

Read this when the user wants a professional, executive, strategy, board, investor, or "consulting-firm" style deck (the McKinsey / BCG / Bain standard). It is about **structure and discipline**, not visual flash. Pair it with a restrained theme (e.g. "Corporate confident" or "Editorial mono" from `themes-and-color.md`); save the boldest palettes for less formal audiences.

The whole philosophy is **be selective, not exhaustive** — say the one thing that matters per slide and cut the rest.

## The five rules that matter most

1. **Answer first (Pyramid Principle).** Lead with the recommendation/conclusion, then the grouped supporting arguments, then the evidence. The first ~3 slides should carry the entire recommendation — if the decision-maker leaves after five minutes, they still know what to do.
2. **Action titles, not topic labels.** Every slide's title is a full-sentence takeaway in active voice, specific and quantified, ≤ ~15 words / 2 lines. The title states the *so what*; the body just proves it.
   - Topic (weak): "Q3 Financial Results"
   - Action (strong): "Q3 revenue beat forecast by 12%, driven by enterprise"
3. **Narrative spine (horizontal logic).** Reading only the slide titles, top to bottom, should read like a short persuasive argument. Write all the titles *first* (the "ghost deck") before designing anything.
4. **One message per slide (vertical logic).** Each slide proves exactly one claim. If the title contains "and," it is probably two slides. Use 2–4 supporting points. Apply the "so what?" test to every element — if it doesn't support the title, delete it.
5. **MECE grouping.** When you break something into parts, the parts shouldn't overlap and together should cover the whole. Keep groups to ~3–4 buckets.

## Slide anatomy

A consulting body slide has a fixed, predictable structure:

- **Action title** — top, the full-sentence takeaway.
- **Body** — one primary proof object (chart, table, simple diagram, or 2–4 points) that earns the title. Not a wall of bullets.
- **Callout (optional)** — a short attached note highlighting the key insight or a caveat ("not yet including X").
- **Source / footnote** — small line crediting data ("Source: company reports 2024; analysis"). Every data point gets attribution.
- **Page number** — on every slide.

## Visual discipline

- ≤ 2 typefaces; consistent sizes for the same element type across slides.
- 3–4 colors used **semantically** (category, status, emphasis) — not decoration. One accent for the one thing that matters per slide.
- Generous whitespace. When a slide feels crowded, remove content rather than shrink it.
- Titles and footers sit in the same position on every slide (don't let them drift).
- No clip art, stock photos, 3D effects, or gratuitous animation.
- **60-second rule:** each slide should be explainable in under a minute. If you'd have to read it aloud word-for-word, there's too much text.

## How this maps to a fullscreen HTML deck

- Put the **action title** in the slide's `h2` (or `h1` on the cover); keep it one or two lines.
- Use the layout components in `fullscreen-html-deck.md`, but bias toward the **data hero**, **two-column**, and **simple table/list** layouts; one proof object per slide.
- Add a small fixed **source line** at the bottom of data slides and keep the slide counter as the page number.
- Open with a 1-slide executive summary that states the recommendation; the rest of the deck defends it.
- Keep the theme restrained and let the structure do the persuading.
