# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is **not an application** — it is the source for portable Codex/Claude **skills** for making presentations. The "product" is prompt/instruction content (Markdown), not running code. Most edits here are changes to skill instructions, not software features. There are two sibling skills, each in its own top-level folder with the same shape (`SKILL.md` + `references/` + `agents/openai.yaml`):

- **`slide-storyteller/`** — story-first HTML presentations and `.pptx` export. Defaults to HTML; produces PowerPoint when explicitly asked. Also covers long-form scrolling story/portfolio pages.
- **`slide-show/`** — a single self-contained HTML file that opens as a *real fullscreen presentation* (one slide per screen; arrow-key/space/swipe navigation; progress bar; `F` toggles browser fullscreen). HTML-only, no dependencies. Deliberately picks bold, varied themes and asks for the user's brand colors up front (it must never default to a nature/garden palette). Hands off to `slide-storyteller` for `.pptx`.

Pick the skill by intent: *"looks/plays like a deck in the browser"* → `slide-show`; *"PowerPoint file" or "scrolling story page"* → `slide-storyteller`.

A skill is consumed by *installing* its folder into an agent's skills directory, e.g.:

```bash
mkdir -p ~/.codex/skills && cp -R slide-storyteller slide-show ~/.codex/skills/
```

After editing, validate the skill with the **Skill Creator quick validator** before considering work complete (see AGENTS.md). There is no build, lint, or test suite — `npm test` is a placeholder that exits 1.

## The one piece of runnable code

`create-deck.js` is a **standalone, hand-written `pptxgenjs` example** that hardcodes a 7-slide manager 1-on-1 deck and writes it to an absolute path (`output/manager-1on1-improved.pptx`). It is a demonstration artifact, not part of the skill runtime.

```bash
npm install        # installs pptxgenjs
node create-deck.js
```

Note the output path inside the file is an absolute `/Users/...` path; change it before running elsewhere.

## Architecture: how a skill is structured

Both skills follow a **thin-entrypoint + lazy-loaded references** pattern: an always-loaded `SKILL.md` (operating standard, intake, numbered workflow, delivery rules, quality bar) that tells the agent *when* to read each file in `references/`, plus `agents/openai.yaml` for UI metadata. The detail below describes `slide-storyteller`; `slide-show` mirrors the same pattern with `references/fullscreen-html-deck.md` (the copy-ready fixed-stage HTML/CSS/JS deck scaffold and layout components), `references/themes-and-color.md` (brand-color intake + a library of bold themes), and `references/consulting-style.md` (MBB/executive deck discipline — pyramid structure, action titles, one-message-per-slide).

### slide-storyteller

- `slide-storyteller/SKILL.md` — the always-loaded entrypoint. Defines the operating standard, intake questions, the numbered workflow, delivery rules, and the quality bar. It tells the agent *when* to read each reference.
- `slide-storyteller/references/` — focused guidance read **only when relevant** (per the conditional triggers in SKILL.md):
  - `design-systems-and-formats.md` — read before planning layouts when better design / specific styles (comic, Material, editorial, timelines, roadmaps) are requested. Contains the design-system routing table, slide-format library, format-family variety budget, and vetted free source libraries.
  - `manager-1on1-updates.md` — read before planning monthly / 1-on-1 / personal-growth / feedback decks.
  - `deck-patterns.md` — reusable deck spines, routed in workflow step 1.
  - `art-direction.md` — guidance for cute-but-professional original illustration.
- `slide-storyteller/agents/openai.yaml` — UI metadata (display name, default prompt, implicit-invocation policy).

### Two core behavioral rules encoded in SKILL.md

1. **HTML-first default.** For broad storytelling / portfolio / resume requests, the skill produces a self-contained `.html` artifact first and only generates `.pptx` when the user explicitly says PowerPoint / slides / deck / PPTX. Both paths require post-generation verification (file exists, parses, expected slide count, no placeholder text) and require giving the final file path first in the response.
2. **Skill self-improvement is gated.** The skill may update its own instructions when a real deck reveals a reusable lesson — but only if the user asked for skill improvement, and only with **anonymized** guidance (never real project names, teammates, customers, internal systems, or exact examples).

## Supporting directories

- `examples/` — committed sample outputs (one HTML monthly update, one real `.pptx`) with preview PNGs. Referenced from README; treat as published artifacts.
- `showcase/` — a static gallery (`index.html` + SVG style previews) of the deck aesthetics the skill targets.
- `output/` and `outputs/` — generated artifacts, git-ignored. Do not rely on their contents being tracked.

## Editing conventions (from AGENTS.md)

- Keep the skill concise and practical; push reusable detail into `references/` rather than bloating `SKILL.md`.
- Do not add broad README-style documentation unless the user asks for it.
- When changing what the agent should *read*, keep SKILL.md's conditional triggers and the reference filenames in sync.
