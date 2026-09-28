# Buzz — landing site

A static recreation of the [Buzz](https://buzz.xyz) landing page, built from the rendered
markup as hand-written HTML, CSS, and vanilla JavaScript. No build step, no dependencies.

Buzz itself is an open source project by Block — the real app lives at
[github.com/block/buzz](https://github.com/block/buzz). This repo is only the marketing page.

## Run it

Any static server works:

```bash
python3 -m http.server 4173
```

Then open <http://localhost:4173>.

## What's here

```
index.html            the page
assets/styles.css     all styling
assets/app.js         bees, scroll-driven background, reveals, menus, typewriter
assets/icon.svg       favicon
assets/block-logo.svg "Built by Block" mark
pages/                support / terms / privacy / community guidelines
```

## What it does

- **Fuzzy wordmark** — the `Buzz` logotype runs through an animated SVG
  `feTurbulence` + `feDisplacementMap` filter. The filter constants are tuned for a 380px
  render and rescaled in JS whenever the viewport changes.
- **Bee swarms** — bees are generated in JS and flown on a sine-wander path in a single
  `requestAnimationFrame` loop, each rotating to face its own velocity. Fields pause when
  scrolled out of view.
- **Scroll-driven background** — section colors are interpolated against the scroll
  position and written to `--bg-top`, so the page fades yellow → blue → lime → yellow.
- **Custom cursor** — a `mix-blend-mode: difference` dot that eases toward the pointer.
  Disabled on touch and under `prefers-reduced-motion`.
- **Animated product mock** — the laptop screen runs a looping CSS/HTML mock of the app
  (people and agents in one room, ending in a PR) instead of a video file.
- **Reveal on scroll, dropdown menus, typewriter footer, waitlist form.**

Every animation respects `prefers-reduced-motion`.

## Differences from the original

The original site's proprietary assets aren't redistributable, so this build substitutes:

| Original | Here |
| --- | --- |
| Cash Sans webfont | system UI stack (SF / Segoe / Inter), same tracking |
| `demo.mp4` screen recording | animated HTML/CSS app mock |
| PNG frame-sequence agent avatars | the bee sprite, colored per card |
| PNG footer wordmark marquee | live text with the same displacement filter |

The waitlist form has no backend — it validates and stores the entry in `localStorage`.
The legal pages are placeholder copy, not legal documents.

"Buzz" and the Block logo are trademarks of Block, Inc.; this recreation is not affiliated
with or endorsed by Block.
