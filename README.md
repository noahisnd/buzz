# Stick — landing site

A static build of the [Stick](https://www.getstick.website) landing page: hand-written HTML,
CSS and vanilla JavaScript, no build step, no dependencies. The copy is Stick's own —
hero, how it works, the comparison, pricing, modes, details, lost-key, platforms and the
full FAQ — carried over onto a bespoke motion-heavy layout.

## Run it

Any static server works:

```bash
python3 -m http.server 4173
```

Then open <http://localhost:4173>.

## What's here

```
index.html          the page
assets/styles.css   all styling
assets/app.js       bees, scroll-driven background, reveals, typewriter
assets/icon.svg     favicon
assets/how/         step media: two WebP stills, the step 3 MP4 and its poster
pages/              faq / refunds / terms / privacy / contact
```

## What it does

- **Fuzzy wordmark** — the `stick` logotype runs through an animated SVG
  `feTurbulence` + `feDisplacementMap` filter. The filter constants are tuned for a 380px
  render and rescaled in JS whenever the viewport changes.
- **Bee swarms** — bees are generated in JS and flown on a sine-wander path in a single
  `requestAnimationFrame` loop, each rotating to face its own velocity. Fields pause when
  scrolled out of view.
- **Scroll-driven background** — section colors are interpolated against the scroll
  position and written to `--bg-top`, so the page moves pink → blue → lime → pink. Each
  section holds its own color and cross-fades through the middle third of the gap.
- **Custom cursor** — a `mix-blend-mode: difference` dot that eases toward the pointer.
  Disabled on touch and under `prefers-reduced-motion`.
- **How it works** — each step carries its own media: the Modes screen, the key in hand,
  and a screen recording of a session starting. The clip is muted and looping, plays only
  while on screen, and shows its poster with controls under reduced motion.
- **Reveal on scroll, an accordion FAQ, and a typewriter footer line.**

Every animation respects `prefers-reduced-motion`.

## Notes

Built on a layout originally derived from another site's structure, then rewritten around
Stick's copy. Type is a system UI stack rather than a licensed webfont.

"Get Stick" links point at getstick.website/buy. The sub-pages under `pages/` are
placeholders apart from the FAQ, which carries the real answers from the homepage.
