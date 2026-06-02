# Themes And Color

Use this to ask for brand colors, turn them into a usable palette, and pick a bold visual theme. The goal is variety: each deck should look deliberately different. **Never default to a nature/garden/sage theme** unless the user asks for it.

## Asking for brand colors

Ask once, briefly, during intake:

> "What are your ~3 main brand colors (hex codes, a logo, or just a company/vibe to match)? If you're not sure, I'll pick a bold theme for you."

Handle the answer:

- **Hex codes or named colors given** → build the palette around them (rules below).
- **A company or brand named** → use widely-known brand colors only if you are confident; otherwise pick a theme that matches the vibe and say so. Do not reproduce a company's exact proprietary identity or logo.
- **A vibe given** ("techy," "elegant," "playful," "corporate") → pick the matching theme below.
- **Nothing / "you pick"** → choose one theme from the library, rotate so you don't reuse the last one, and state your pick in one line. Do not stall.

## Building a palette from brand colors

A deck needs more than the brand colors — it needs a working system. Map the user's colors onto these roles:

| Role | Variable | Guidance |
|---|---|---|
| Backdrop | `--bg` | deck letterbox; usually darkest or a near-black/near-white neutral |
| Slide surface | `--slide-bg` | the slide canvas; a clean dark or light tone |
| Ink | `--ink` | primary text; must hit WCAG AA on `--slide-bg` |
| Muted | `--muted` | secondary text; lower contrast but still legible |
| Primary | `--primary` | the dominant brand color; structure, headers, key shapes |
| Accent | `--accent` | the punch color; numbers, highlights, progress bar |
| Accent 2 | `--accent-2` | sparing third color for contrast or a second data series |

Rules:

- If the user gives 3 colors, usually make the most neutral/darkest the surface, the boldest the primary, and the brightest the accent.
- Generate tints/shades from the brand colors instead of introducing unrelated hues (e.g. a 12% lighter primary for cards).
- Always verify text contrast. If a brand color is too light for text, use it for fills/accents and choose a darker ink.
- Keep it to ~4–6 active colors. Resist rainbow palettes.
- Decide light vs dark deck based on the brand and tone; offer to flip it if unsure.

## Bold theme library

Pick one. Each lists a ready palette (backdrop / surface / ink / muted / primary / accent / accent-2) and a type pairing. Treat these as starting points; nudge toward the brand when colors are provided.

| Theme | Mood | Palette (bg · surface · ink · muted · primary · accent · accent2) | Type pairing |
|---|---|---|---|
| **Midnight neon** | techy, startup, product launch | `#0f1020 · #15172e · #f4f4fb · #a6a8c8 · #6c5ce7 · #00d2a8 · #ff7a59` | Grotesk display + system sans |
| **Bold brutalist** | confident, opinionated, dev/creator | `#111111 · #ffffff · #111111 · #555555 · #ff3b30 · #1a1aff · #ffd400` | Heavy sans (Arial Black stack) + mono |
| **Editorial mono** | elegant, premium, keynote | `#0c0c0c · #141414 · #f5f1e8 · #9b968a · #c8a24a · #e0d6c2 · #7d7466` | Serif display + clean sans |
| **Sunset gradient** | energetic, marketing, consumer | `#1a0b2e · #241246 · #fff4ef · #d9b8d4 · #ff5e87 · #ffb056 · #7b5cff` | Rounded sans + sans |
| **Corporate confident** | enterprise, B2B, investor | `#0a1f44 · #ffffff · #0a1f44 · #5b6b86 · #1f6feb · #00b8a9 · #ff8c42` | Clean sans + sans |
| **Mono noir** | minimal, agency, design review | `#000000 · #0d0d0d · #ffffff · #8a8a8a · #ffffff · #ff2d55 · #00e0ff` | Mono display + sans |
| **Warm terracotta** | human, brand story, hospitality | `#1c1410 · #2a1d16 · #f7ede2 · #c4a48c · #e07a5f · #f2cc8f · #81b29a` | Humanist serif + sans |
| **Electric corporate** | fintech, SaaS, data | `#06121f · #0d1f33 · #eaf4ff · #7fa8c9 · #0af · #14ffb1 · #ffd166` | Geometric sans + mono |

When the user gives brand colors, you can still borrow a theme's *structure* (light vs dark, accent strategy) while swapping in their hues.

## Keeping variety across slides and decks

- Across one deck: vary layouts (see the layout components in `fullscreen-html-deck.md`), not the palette. Reuse the visual system; alternate the proof object.
- Across decks: rotate themes. Don't reach for the same look twice in a row. If the last deck was Midnight neon, pick something tonally different next time.
- Use the accent color with intent — for the one thing that matters on a slide (a number, a verb, a callout), not as decoration everywhere.
- Let one or two slides be visually quiet (a single statement in whitespace) so the bold slides land harder.

## Inline-SVG accents

Since the deck is dependency-free, build visual interest with inline SVG using the theme variables:

- corner blobs, arcs, or geometric shapes as section markers
- simple bar/line/donut charts with 1–3 callouts
- big-number backdrops (an oversized translucent numeral behind a metric)
- a thin accent rule above a quote

Keep SVG decoration supporting the claim, never competing with it.
