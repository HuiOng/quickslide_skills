---
name: slide-storyteller
description: Create polished story-first HTML portfolios, presentation drafts, and editable slide decks for work updates, resumes, portfolio stories, leadership narratives, casual weekly updates, and visual storytelling. Use when the user asks Codex to make a resume portfolio, visual story, HTML presentation, slides, improve a deck, turn notes into a presentation, create a cute or illustrated style, generate clip art for slides, or package a story into PowerPoint/PPTX for business or personal use.
---

# Slide Storyteller

## Operating Standard

Create story artifacts that feel intentional, useful, and human. Optimize for a clear story, credible evidence, and a tasteful visual system before decoration.

For final PPTX generation, use the installed `Presentations` skill and its artifact-tool workflow when available. This skill supplies the storytelling, deck-type routing, art direction, and critique standard that should guide that build.

Default to delivering a polished HTML artifact first when the user asks for a resume portfolio, visual story, presentation draft, or broad storytelling deliverable and does not explicitly request PowerPoint. Generate PowerPoint/PPTX only when the user asks for slides, a deck, PowerPoint, PPTX, or a file to present in PowerPoint. After delivering HTML, offer to continue into PowerPoint if a deck version would be useful.

Use image generation for original cute art, spot illustrations, friendly icons, stickers, characters, scene backgrounds, or metaphor visuals when they improve the deck. Do not invent or redraw official logos, mascots, screenshots, product marks, or brand identity assets; use verified or user-provided assets for those.

When the user asks for better design, more professional slides, comic style, modern/high-end style, Google/Material style, infographics, timelines, roadmaps, or richer formatting, read `references/design-systems-and-formats.md` before planning layouts.

## Intake

Ask only for missing facts that would materially change the deck. If the user gives a broad request, proceed with reasonable assumptions and state them briefly.

Capture:

- audience and decision-maker
- deck purpose: inform, persuade, update, apply, sell, teach, or celebrate
- desired format: HTML, PPTX, PDF, images, or outline
- default format: HTML first unless the user explicitly asks for PPTX, PowerPoint, slides, or a deck file
- tone: executive, warm, playful, editorial, analytical, cute, bold, calm
- source material: notes, metrics, resume, screenshots, links, previous decks
- constraints: brand, length, deadline, confidentiality, must-include items

## Workflow

1. Route the story using `references/deck-patterns.md`.
2. Write a one-sentence promise for the deck: what the audience should believe, understand, or do after viewing it.
3. Build a claim spine: one sharp claim per slide, not topic labels.
4. Choose a design system and slide format library. Use `references/design-systems-and-formats.md` for professional styles, timelines, roadmaps, diagrams, comic panels, data stories, and source-library guidance.
5. Create a slide plan with title, claim, proof object, slide format, visual treatment, and speaker intent for each slide.
6. Generate or gather assets. For cute art, follow `references/art-direction.md`. For third-party templates, icons, illustrations, or photos, verify license terms and add a credits slide when required.
7. Build the requested artifact. Default to one polished, self-contained HTML file for portfolios, visual stories, and presentation drafts unless the user requested PPTX.
8. For HTML, verify the file exists, parses, has responsive layout rules, and contains no placeholder text.
9. For PPTX, export a real `.pptx` file and verify it exists, is non-empty, and contains the expected number of slides.
10. Iterate weak sections or slides before final delivery.

## HTML-First Delivery Rules

For beginner-friendly portfolio and story delivery, Codex should create a usable HTML artifact before proposing PowerPoint.

- Produce a final `.html` file with a useful filename, such as `resume-portfolio.html`.
- Put the final file in an obvious `output/` folder or the user-requested folder.
- Keep it self-contained when practical: inline CSS, inline SVG, semantic HTML, no fragile external dependencies.
- Design it like a presentation story: hero, claim spine, proof sections, timeline or case studies, credentials, and closing.
- Verify the file with local checks before responding:
  - file exists and size is greater than zero
  - HTML parses without obvious syntax errors
  - no `TODO`, `Lorem`, or placeholder copy remains unless deliberately marked for user replacement
- In the final response, give the exact `.html` path first.
- Ask whether the user wants to continue into PPTX only after the HTML is delivered, unless the user already requested PPTX.

## PPTX Delivery Rules

Generate PPTX only when the user explicitly asks for PowerPoint, slides, a deck, PPTX, or a presentation file. For beginner-friendly delivery, Codex must do the conversion/export work itself.

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
- license check: third-party assets and templates are either user-provided, original, public/open-license, or credited according to their terms

## Deck Archetypes

Use `references/deck-patterns.md` when choosing structure. Common starting points:

- weekly update: progress, evidence, blockers, decisions, next week
- work story: context, tension, insight, recommendation, plan
- resume or portfolio: positioning, proof, selected wins, working style, next role
- executive narrative: market shift, strategic bet, operating model, milestones, asks
- playful explainer: hook, analogy, steps, example, takeaway

Use `references/design-systems-and-formats.md` when choosing visual systems and slide formats. Common format needs:

- timeline or roadmap: milestones, history, launch plan, implementation phases
- graphical explainer: process, system map, flywheel, hierarchy, journey map
- comic or storyboard: beginner teaching, scenario walkthrough, playful narrative
- data story: annotated chart, small multiples, KPI shift, before/after metric
- Google/Material-inspired deck: product, tech, workflow, or internal training

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

When delivering HTML, include:

- final `.html` file path first
- what type of story or portfolio was created
- verification performed, especially parse and placeholder checks
- a short note that PPTX can be generated next if useful

Keep the response short and useful.
