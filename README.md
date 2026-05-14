# Slide Storyteller

`slide-storyteller` is a Codex skill for creating polished, editable slide decks for work updates, beginner training, resumes, portfolio stories, leadership narratives, and playful visual explainers.

It is designed for people who want the final output, not a conversion chore. When you ask for a deck, the skill tells Codex to produce a real `.pptx`, verify it, and give you the file path first.

## Why This Exists

Most AI slide attempts stop at an outline, a script, or a rough mockup. This skill pushes Codex toward a more useful workflow:

- understand the audience and goal
- write slide claims instead of topic labels
- choose a visual system
- build editable slides
- export an actual PowerPoint file
- verify the deck before handing it back

## Install

Clone or download this repository, then copy the skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R slide-storyteller ~/.codex/skills/
```

Restart Codex or start a new session, then ask for the skill by name:

```text
Use $slide-storyteller to create a 7-slide beginner training deck about using Codex and Claude Code well. Make it friendly, practical, and shareable with my team.
```

## Requirements

This skill works best in Codex with access to the Presentations plugin/runtime. The skill can help with structure and story anywhere, but actual `.pptx` export depends on presentation tooling being available in the Codex environment.

## Example Output

A real generated example is included:

- [AI Coding for Beginners PPTX](examples/ai-coding-for-beginners/ai-coding-for-beginners.pptx)

Preview slides:

| Cover | Five Questions | Starter Prompt |
|---|---|---|
| ![AI coding deck cover](examples/ai-coding-for-beginners/previews/slide-01.png) | ![Five questions slide](examples/ai-coding-for-beginners/previews/slide-03.png) | ![Starter prompt slide](examples/ai-coding-for-beginners/previews/slide-07.png) |

## Design Range

These lightweight previews show the kinds of deck styles the skill is meant to guide.

| Executive Brief | Cute Learning |
|---|---|
| ![Executive brief slide preview](showcase/assets/executive-brief.svg) | ![Cute learning slide preview](showcase/assets/cute-learning.svg) |

| Data Story | Resume Portfolio |
|---|---|
| ![Data story slide preview](showcase/assets/data-story.svg) | ![Resume portfolio slide preview](showcase/assets/resume-portfolio.svg) |

| Weekly Update | Storybook Explainer |
|---|---|
| ![Weekly update slide preview](showcase/assets/weekly-update.svg) | ![Storybook explainer slide preview](showcase/assets/storybook-explainer.svg) |

You can also open the visual gallery at [showcase/index.html](showcase/index.html).

## More Example Prompts

```text
Use $slide-storyteller to turn these weekly notes into a short update deck for my boss. Keep it clear, honest, and decision-oriented.
```

```text
Use $slide-storyteller to create a resume portfolio deck from my experience. Make it polished and warm, with 2 case-study slides.
```

```text
Use $slide-storyteller to create a playful onboarding deck that teaches non-technical teammates how to brief an AI coding agent.
```

## Skill Contents

- [slide-storyteller/SKILL.md](slide-storyteller/SKILL.md): main Codex instructions
- [deck-patterns.md](slide-storyteller/references/deck-patterns.md): reusable deck structures
- [art-direction.md](slide-storyteller/references/art-direction.md): guidance for cute but professional art
- [showcase/index.html](showcase/index.html): design gallery

## Project Status

This is an early prototype, but it is useful enough to share.

Good current uses:

- personal slide experiments
- team learning decks
- weekly updates
- resume or portfolio story drafts
- beginner-friendly Codex skill examples

Not yet perfect:

- It has one bundled example deck, not a full template library.
- Results depend on the local Codex presentation runtime.
- Brand-specific decks still need user-provided brand assets and source material.

## Recommended Next Improvements

- Add more real `.pptx` examples.
- Add a short video or GIF walkthrough.
- Add a troubleshooting section for environments without PPTX export.
- Add optional company brand template examples.

## License

MIT. See [LICENSE](LICENSE).
