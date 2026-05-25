# Manager 1-on-1 Update Decks

Use this pattern for monthly updates, 1-on-1 check-ins, personal growth updates, and gentle feedback to a manager.

## Story Shape

Keep the deck short: 6-8 slides is usually enough.

1. Monthly headline
2. What changed or what was learned
3. Product or project progress
4. User/customer signal
5. Operational finding or support path
6. Growth reflection or working-model feedback
7. Specific asks for next month

Write slide titles as **claims, not labels**. Use the formula: **subject + verb + object + stake**. Each title should stand alone as a sentence that the manager can absorb in five seconds.

**The formula:**
- **subject**: who (I, the team, the project)
- **verb**: action or insight (learned, want, plan to, discovered, need)
- **object**: what changed or what's needed
- **stake**: why it matters or what happens next

**Before/after examples:**

| Avoid | Better |
|---|---|
| `AI Became Practical` | `I want to use agents more systematically next month because the handoff got clearer` |
| `Pilot Is Launching` | `We're ready to launch the pilot, and I need sign-off on the team scope by Friday` |
| `Plan to Display Historical Items` | `We're planning to surface old revisions so users can compare versions` |
| `Working Model Reflection` | `I want clearer ownership so I can keep growing and we can move faster together` |
| `What Would Help Next Month` | `Three things I'd like to focus on: stronger code review, a demo moment, and one learning target` |

**Why it works:**
- Claims are scannable and memorable.
- They create accountability (the manager knows what you're asking or announcing).
- They avoid vague implication; the point is explicit.
- Each slide can stand alone.

Operational or unfamiliar topics benefit most from concrete claims. Compare `Plan to display historical items` (label) with `We're surfacing old revisions so users can compare versions` (claim: team + action + proof + why).

## Make Abstract Learning Concrete

When a slide says the user learned a tool, method, agent, skill, PRD process, or workflow, add a small example. Otherwise the slide can feel generic.

Examples:

- Define unfamiliar terms in one compact note: `Agent: an AI helper that can work through a task. Skill: a reusable instruction set for a specific workflow.`
- Show a miniature linked artifact instead of only saying "linked user stories":

| PRD | Linked User Stories |
|---|---|
| `PRD-001: Example Workflow` | `US-001 Complete first action`; `US-002 Review the action`; `US-003 Track status` |

Keep examples realistic but lightweight. They should prove the concept without becoming documentation.

## Privacy And Reuse Guardrail

Do not add the user's real project names, outcomes, teammate details, customer names, internal systems, or exact work examples to this public skill or its references. When learning from a real deck exercise, generalize the lesson into reusable patterns and anonymized examples.

Use placeholders such as:

- `Project A`
- `Internal Search Tool`
- `PRD-001: Example Workflow`
- `US-001 Complete first action`
- `Data table`
- `Partial availability`

Keep the user's actual content only in the generated deck or private working artifact, not in skill documentation.

## Vary Slide Formats

Do not use the same card grid on every slide. Keep one visual system, but vary the proof object by slide purpose. Refer to the format families in `design-systems-and-formats.md#format-families-for-variety-budget` and aim for ≥4 distinct families in a 6–8 slide update.

Recommended pairings for 1-on-1 updates:

- **Learning**: full-bleed type (oversize headline + short definition) + capability card grid (3–4 cards with example) + small inline note
- **Launch**: timeline/rail (2–3 rollout phases with dates) or full-bleed type
- **User feedback**: quote/callout spread (one strong quote from user) + diagram/flow (heard → changed → shipped)
- **Support boundary**: table/grid (availability rows: available now / later) with supporting short note
- **Operational update**: card grid (3–4 short bullets or points) or diagram/flow (dependency → plan → timeline)
- **Sensitive feedback**: quote/callout spread (current model reflection) + diagram/flow (possible improvement path) — keep it gentle and non-adversarial
- **Closing asks**: card grid with icon-led tiles OR timeline/rail (3 milestones) — avoid a list unless the user explicitly requests one

**Thumbnail test**: lay out all slides at once. Each should be visually distinct from its neighbors. If you see two slides that look similar, reformat one using a different family.

**Adjacent-slide check**: no two slides next to each other should use the same format family. If slide N is a card grid, slide N+1 must be timeline/table/diagram/quote/type — anything except card grid.

## Alignment And Spacing QA

For icon-led tiles, numbered rows, and closing asks, verify the layout at desktop and tablet widths before delivery.

Check:

- numbers stay inside their tile and align consistently, usually top-right or top-left
- generic text rules do not override badge or number positioning
- icons, numbers, titles, and body text use a clear grid, not accidental offsets
- cards do not stack into a tall column too early; keep rows at tablet widths when content still fits
- tile height matches the amount of content; avoid large empty areas around short ask text
- responsive breakpoints preserve professional spacing and do not create awkward vertical gaps

If a user comments that a tile uses too much space, tighten padding, min-height, icon size, and responsive breakpoints before changing the content.

## Handle Sensitive Feedback Gently

Frame the feedback as a working-model or growth-fit discussion, not a personal complaint.

Use:

- `I appreciate my teammate and respect their strengths.`
- `Our work is often independent, so the close pairing does not always create the learning benefit I hoped for.`
- `I am okay to continue, but clearer ownership may create more value.`
- `This is not about blame; it is about finding the model where both of us contribute well and I can continue growing.`
- Neutral titles such as `Working Model Reflection`; avoid titles that sound like a verdict on the current setup.
- When the user is unsure or the situation may change soon, frame the slide as an observation to revisit next month rather than a conclusion.

Avoid:

- direct blame
- "wasting resource" as written
- saying "I am bored" directly
- implying the teammate is the problem
- saying "better working model" in a title when it could imply the current model is wrong
- naming a specific teammate in sensitive feedback unless the user explicitly wants that wording on the slide

Translate frustration into a manager-actionable ask:

- one clearer ownership area
- one showcase or demo moment
- one learning target or stretch direction

Keep the closing proportional to the story. If the previous slide already frames the next month as observation, use 1-2 gentle alignment points instead of a full list of targets.

## Use Original Spot Art

For personal growth or closing asks, make the ask list itself visually intentional before adding separate art. Icon-led tiles, numbered rows, roadmap steps, bridge motifs, toolkit symbols, or launch paths work well.

Keep visuals secondary to the message:

- no text inside the image
- no fake logos or brand assets
- no dense decoration behind readable copy
- consistent palette with the deck
