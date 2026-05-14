---
name: slide-storyteller
description: Create polished, editable presentation decks for work updates, resumes, portfolio stories, leadership narratives, casual weekly updates, and visual storytelling. Use when the user asks Codex to make slides, improve a deck, turn notes into a presentation, create a cute or illustrated slide style, generate clip art for slides, or package a story into PowerPoint/PPTX for business or personal use.
---

# Slide Storyteller

## Operating Standard

Create slides that feel intentional, useful, and human. Optimize for a clear story, credible evidence, and a tasteful visual system before decoration.

For final PPTX generation, use the installed `Presentations` skill and its artifact-tool workflow when available. This skill supplies the storytelling, deck-type routing, art direction, and critique standard that should guide that build.

Default to delivering an actual `.pptx` file when the user asks for slides, a deck, PowerPoint, or something to share at work. Do not stop at an outline, HTML mockup, slide modules, or instructions for conversion unless the user explicitly asks for those instead.

Use image generation for original cute art, spot illustrations, friendly icons, stickers, characters, scene backgrounds, or metaphor visuals when they improve the deck. Do not invent or redraw official logos, mascots, screenshots, product marks, or brand identity assets; use verified or user-provided assets for those.

## Intake

Ask only for missing facts that would materially change the deck. If the user gives a broad request, proceed with reasonable assumptions and state them briefly.

Capture:

- audience and decision-maker
- deck purpose: inform, persuade, update, apply, sell, teach, or celebrate
- desired format: PPTX, PDF, images, or outline
- tone: executive, warm, playful, editorial, analytical, cute, bold, calm
- source material: notes, metrics, resume, screenshots, links, previous decks
- constraints: brand, length, deadline, confidentiality, must-include items

## Workflow

1. Route the deck using `references/deck-patterns.md`.
2. Write a one-sentence promise for the deck: what the audience should believe, understand, or do after viewing it.
3. Build a claim spine: one sharp claim per slide, not topic labels.
4. Choose a design system: typography mood, color palette, layout rhythm, chart grammar, illustration style, and visual density.
5. Create a slide plan with title, claim, proof object, visual treatment, and speaker intent for each slide.
6. Generate or gather assets. For cute art, follow `references/art-direction.md`.
7. Build editable slides, render previews, and critique the deck at thumbnail size and full size.
8. Export the deck to a real `.pptx` file.
9. Verify the `.pptx` exists, is non-empty, and contains the expected number of slides.
10. Iterate weak slides before final delivery.

## PPTX Delivery Rules

For beginner-friendly delivery, Codex must do the conversion/export work itself.

- Produce a final PowerPoint file with a useful filename, such as `ai-coding-for-beginners.pptx`.
- Put the final file in an obvious `output/` folder or the user-requested folder.
- Verify the file with local checks before responding:
  - file exists and size is greater than zero
  - file type is Microsoft PowerPoint or a valid zip-based PPTX
  - `ppt/slides/slide*.xml` count matches the expected slide count when possible
- In the final response, give the exact `.pptx` path first.
- Mention preview images or HTML only as optional extras, not as the main deliverable.
- Never tell the user to run `.mjs` files, export manually, or convert the deck themselves unless they explicitly asked to learn the build process.

## Quality Bar

Every slide should have:

- a headline that says the point
- one primary proof object: chart, table, diagram, image, timeline, quote, artifact, or before/after
- clear visual hierarchy
- enough whitespace to make the point legible
- no filler icons, generic card grids, or decorative charts

The deck should pass three checks:

- thumbnail check: the deck has variety and a coherent visual rhythm
- boss check: the point is obvious in ten seconds
- editability check: text, shapes, charts, and layout remain practical to revise

## Deck Archetypes

Use `references/deck-patterns.md` when choosing structure. Common starting points:

- weekly update: progress, evidence, blockers, decisions, next week
- work story: context, tension, insight, recommendation, plan
- resume or portfolio: positioning, proof, selected wins, working style, next role
- executive narrative: market shift, strategic bet, operating model, milestones, asks
- playful explainer: hook, analogy, steps, example, takeaway

## Art Direction

Use cute art when it adds warmth, memorability, or emotional clarity. Keep work decks professional by making illustration a supporting system rather than the whole message.

Good uses:

- section dividers
- small spot illustrations
- friendly process diagrams
- recurring character or mascot that is clearly original
- metaphor scenes for abstract concepts

Avoid:

- childlike art for high-stakes executive material unless requested
- cluttered decorative borders
- fake brand assets
- clip art that repeats without purpose
- images that compete with the slide's claim

## Final Response

When delivering a deck, include:

- final `.pptx` file path first
- what type of deck was created
- verification performed, especially file type and slide count
- key assumptions made, only if important

Keep the response short and useful.
