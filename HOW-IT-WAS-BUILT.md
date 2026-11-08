# How it was built

These are the prompts used to build and ship this project with [Claude Code](https://claude.com/claude-code), copied word for word and in order. The notes under each one say what it led to.

---

### 1. Start the rebuild

```text
ok now /clone-website https://github.com/alagappan567/travel-agency  do this
```

This ran the `clone-website` workflow in an AI website-cloner template (Next.js 16, Tailwind v4).

- **Read the reference.** It is a full Next.js 14 + Tailwind v3 app called **Movade**, with a 197-frame hero sequence, 16 travel photos, 8 reviewer photos, a logo video and a footer photo. The repo also holds the author's own browser screenshots, from an older version branded "Malvora". The rebuild follows the current code.
- **Ported every section** into small components: the pinned hero and frame canvas, the search card, 10 content sections, the footer, and shared tilt, magnetic-button, reveal, accordion and toast pieces. The real assets were copied, and the original's Tailwind v3 design tokens were carried into Tailwind v4.
- **Measured and fixed:**
  - **World map.** Building it in the browser blocked the page for about 2 seconds, so it is now pre-rendered once to a static SVG.
  - **Phone hero.** On phones the search card covered the headline; the copy now sits above it, and the fields use two columns.
  - **Phone menu.** The ☰ menu was see-through over the page; it's now solid.
  - **Small controls.** Social icons that did nothing now respond, and the video popup also closes with Esc.
- **Checked it.**
  - Lint, typecheck and production build pass.
  - Headless-Chrome passes at 1600px (the width of the author's screenshots) and 390px drive every interaction with real wheel, mouse, touch and keyboard input.
  - The world map, footer and search card line up with the author's screenshots.

### 2. Ship it

```text
Push and deploy
```

This created a new Vercel project, `movade-travel`, and deployed it to production at **https://movade-travel.vercel.app**.

```text
use this repo to push https://github.com/Guru1315/travel-agency
```

The project was pushed here. That first push included the full source.

```text
continue
```

Every desktop interaction was re-run against the live URL and passed.

### 3. Showcase only

```text
i said u to commit and push only what we did in this projects such as that screensshots , assessts , how it done , how it works also put 3d animated READMe sections with live site url
```

The repo's contents were replaced with this showcase:

- screenshots from the live site at desktop and phone width
- `assets/hero-scroll.gif`, recorded by scrolling the live hero in headless Chrome
- `assets/banner.svg`, a hand-written animated SVG: a rotating wireframe globe, a plane orbiting in front of and behind it, pulsing destination pins, and a running scroll-to-frame counter
- a filmstrip of the hero frames
- this file and [HOW-IT-WORKS.md](HOW-IT-WORKS.md)
