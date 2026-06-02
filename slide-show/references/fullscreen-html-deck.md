# Fullscreen HTML Deck — Build Reference

Use this when building the deck. It gives a complete, copy-ready scaffold for a single self-contained `.html` file that opens as a fullscreen, keyboard/swipe-navigable presentation. Adapt the content and theme; keep the structure and the navigation script.

## Core technique: a fixed stage, scaled to fit

Real slides keep their exact layout on every screen. To get that, lay every slide out on a **fixed 1280×720 stage** and scale the whole stage to the viewport with a CSS transform (centered, letterboxed). You design once at a known size; the browser fits it to any monitor or phone.

- Stage size: `1280 × 720` (16:9). For 4:3 use `1280 × 960`; for 16:10 use `1280 × 800`. Pick one and keep it constant.
- `scale = min(viewportWidth / 1280, viewportHeight / 720)`.
- One `.slide` is active at a time; advancing swaps which slide is visible inside the stage.

## Copy-ready scaffold

Replace the `:root` palette with the chosen theme (see `themes-and-color.md`), and replace the slide bodies with real content. Keep the IDs, classes, and the script.

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
<title>Deck Title</title>
<style>
  /* ---- Theme: replace these with the chosen palette ---- */
  :root {
    --bg: #0f1020;          /* deck backdrop / letterbox */
    --slide-bg: #15172e;    /* slide surface */
    --ink: #f4f4fb;         /* primary text */
    --muted: #a6a8c8;       /* secondary text */
    --primary: #6c5ce7;     /* main brand color */
    --accent: #00d2a8;      /* accent */
    --accent-2: #ff7a59;    /* second accent */
    --stage-w: 1280px;
    --stage-h: 720px;
    --display: "Georgia", "Times New Roman", serif;     /* headline face */
    --body: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif; /* body face */
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }
  html, body { height: 100%; overflow: hidden; background: var(--bg); }
  body { font-family: var(--body); color: var(--ink); }

  /* Fixed stage, centered and scaled by JS */
  #stage {
    position: fixed; top: 50%; left: 50%;
    width: var(--stage-w); height: var(--stage-h);
    transform: translate(-50%, -50%) scale(1);
    transform-origin: center center;
  }

  .slide {
    position: absolute; inset: 0;
    width: var(--stage-w); height: var(--stage-h);
    background: var(--slide-bg);
    padding: 72px 88px;
    display: flex; flex-direction: column; justify-content: center;
    opacity: 0; visibility: hidden;
    transition: opacity .45s ease;
  }
  .slide.is-active { opacity: 1; visibility: visible; }

  /* Typography defaults */
  .slide h1 { font-family: var(--display); font-size: 84px; line-height: 1.04; letter-spacing: -1px; }
  .slide h2 { font-family: var(--display); font-size: 56px; line-height: 1.08; }
  .slide p  { font-size: 26px; line-height: 1.5; color: var(--muted); max-width: 18em; }
  .eyebrow  { font-size: 18px; letter-spacing: 3px; text-transform: uppercase; color: var(--accent); margin-bottom: 18px; }

  /* Chrome: progress, counter, nav */
  #progress { position: fixed; top: 0; left: 0; height: 4px; width: 0%; background: var(--accent); z-index: 50; transition: width .3s ease; }
  #counter { position: fixed; bottom: 18px; right: 22px; font-size: 14px; color: var(--muted); z-index: 50; font-variant-numeric: tabular-nums; }
  .nav-btn { position: fixed; bottom: 14px; z-index: 50; width: 40px; height: 40px; border: none; border-radius: 50%;
             background: rgba(255,255,255,.08); color: var(--ink); font-size: 20px; cursor: pointer; }
  #prev { right: 108px; } #next { right: 62px; }
  .nav-btn:hover { background: rgba(255,255,255,.18); }
  #hint { position: fixed; bottom: 18px; left: 22px; font-size: 13px; color: var(--muted); z-index: 50; opacity: .8; }

  /* Invisible click zones for click-to-advance */
  .click-zone { position: fixed; top: 0; height: 100%; width: 18%; z-index: 40; cursor: pointer; }
  #zone-prev { left: 0; } #zone-next { right: 0; }

  @media print { #progress, #counter, .nav-btn, #hint, .click-zone { display: none; } }
</style>
</head>
<body>
  <div id="progress"></div>

  <div id="stage">
    <!-- One <section class="slide"> per slide. First gets is-active. -->
    <section class="slide is-active">
      <span class="eyebrow">Eyebrow / section</span>
      <h1>A claim, not a label</h1>
      <p>One supporting line that earns the headline.</p>
    </section>

    <section class="slide">
      <h2>Slide two uses a different layout</h2>
      <p>Vary the layout slide to slide.</p>
    </section>

    <section class="slide" style="align-items:center;text-align:center;">
      <h1 style="font-size:140px;color:var(--accent);">73%</h1>
      <p style="color:var(--ink);max-width:24em;">A single big number is its own slide.</p>
    </section>
  </div>

  <div id="zone-prev" class="click-zone"></div>
  <div id="zone-next" class="click-zone"></div>
  <button id="prev" class="nav-btn" aria-label="Previous slide">&#8249;</button>
  <button id="next" class="nav-btn" aria-label="Next slide">&#8250;</button>
  <div id="counter">1 / 1</div>
  <div id="hint">&larr; &rarr; navigate &middot; F fullscreen</div>

<script>
(function () {
  var slides = Array.prototype.slice.call(document.querySelectorAll('.slide'));
  var stage = document.getElementById('stage');
  var progress = document.getElementById('progress');
  var counter = document.getElementById('counter');
  var i = 0;

  function clamp(n) { return Math.max(0, Math.min(slides.length - 1, n)); }

  function show(n) {
    i = clamp(n);
    slides.forEach(function (s, idx) { s.classList.toggle('is-active', idx === i); });
    counter.textContent = (i + 1) + ' / ' + slides.length;
    progress.style.width = ((i + 1) / slides.length * 100) + '%';
    history.replaceState(null, '', '#' + (i + 1));
  }
  function next() { show(i + 1); }
  function prev() { show(i - 1); }

  function fit() {
    var s = Math.min(window.innerWidth / stage.offsetWidth, window.innerHeight / stage.offsetHeight);
    stage.style.transform = 'translate(-50%, -50%) scale(' + s + ')';
  }

  document.addEventListener('keydown', function (e) {
    switch (e.key) {
      case 'ArrowRight': case ' ': case 'PageDown': e.preventDefault(); next(); break;
      case 'ArrowLeft': case 'Backspace': case 'PageUp': e.preventDefault(); prev(); break;
      case 'Home': show(0); break;
      case 'End': show(slides.length - 1); break;
      case 'f': case 'F':
        if (!document.fullscreenElement) { document.documentElement.requestFullscreen && document.documentElement.requestFullscreen(); }
        else { document.exitFullscreen && document.exitFullscreen(); }
        break;
    }
  });

  document.getElementById('next').addEventListener('click', next);
  document.getElementById('prev').addEventListener('click', prev);
  document.getElementById('zone-next').addEventListener('click', next);
  document.getElementById('zone-prev').addEventListener('click', prev);

  // Touch swipe
  var x0 = null;
  document.addEventListener('touchstart', function (e) { x0 = e.touches[0].clientX; }, { passive: true });
  document.addEventListener('touchend', function (e) {
    if (x0 === null) return;
    var dx = e.changedTouches[0].clientX - x0;
    if (Math.abs(dx) > 40) { dx < 0 ? next() : prev(); }
    x0 = null;
  }, { passive: true });

  window.addEventListener('resize', fit);

  // Deep link: ?slide=N or #N
  var params = new URLSearchParams(location.search);
  var start = parseInt(params.get('slide') || location.hash.replace('#', ''), 10);
  fit();
  show(isNaN(start) ? 0 : start - 1);
})();
</script>
</body>
</html>
```

## Layout components (drop into `.slide` bodies)

Vary these across the deck. Style with the theme variables, not hardcoded colors.

- **Cover**: eyebrow + oversize `h1` + one-line promise; optional inline-SVG accent shape in a corner.
- **Big statement / full-bleed type**: a single large claim centered or flush-left, minimal supporting text.
- **Big number / metric**: one huge figure (`120px`+) in an accent color with a short caption; or a before→after pair.
- **Two-column (asymmetric)**: 60/40 split — headline + body on one side, a visual/quote/number on the other. Use `display:flex; gap` inside the slide.
- **Card row**: 3 equal cards (`display:flex; gap:28px`) each with a small title and one line. Don't overfill.
- **Quote spread**: a large pull quote (`h2`) with a thin accent rule above and a small attribution below.
- **Steps / list**: numbered items with accent-colored numerals; one idea per line, generous spacing.
- **Chart (inline SVG)**: hand-build a simple bar/line chart as inline `<svg>` with the theme colors and 1–3 text callouts. No charting libraries.
- **Section divider**: full accent-colored background with one short label to reset attention.
- **Closing**: recap claim or call-to-action, contact line, optional small logo (user-provided only).

## Rules and pitfalls

- Keep it **one file**: inline all CSS, JS, and SVG. Avoid CDNs and external fonts unless the user approves a specific web-font `<link>`.
- Put exactly one `.slide` per slide and give the **first** slide `is-active`. The JS counts slides from the DOM, so the counter stays correct automatically.
- Design inside the `1280×720` stage coordinates — sizes are absolute, so the scaling stays predictable. Do not use `vw`/`vh` units inside slides; they fight the stage transform.
- Maintain contrast: body text against `--slide-bg` should pass WCAG AA. Don't put low-contrast muted text on a busy background.
- Don't animate everything. One tasteful transition (the opacity fade above) is enough; heavy per-element animation distracts.
- For images/logos, only use user-provided or original assets; never fabricate official brand marks.
- The deck must work opened directly from disk (`file://`) — so no `fetch`, no module imports, no server-only features.

## Verification checklist for the built file

- file exists, size > 0
- exactly one `.slide` per intended slide; first has `is-active`
- the `<script>` is present and contains the `show()`/`fit()` functions and a `resize` listener
- `#progress`, `#counter`, `#prev`, `#next` exist
- no `Lorem`/`TODO`/empty slide remains
- opening in a browser shows slide 1 fullscreen; arrows, click zones, and swipe change slides; the counter updates
