# How it works

The live site is at **https://movade-travel.vercel.app**. It's one page, built with Next.js 16, React 19, TypeScript, Tailwind CSS v4, GSAP ScrollTrigger, Lenis and Framer Motion. There's no WebGL. The "3D" comes from a pre-rendered camera flight played back by scroll, plus perspective tilt on the cards.

## Page order

| # | Section | What moves |
|---|---|---|
| 0 | Preloader | Logo clip on black, ends when the clip ends (5s at most), 0.6s fade |
| – | Nav | Frosted, fixed; hides while the hero is mid-scroll; ☰ menu on phones |
| 1 | **Hero**: "Explore the World, One Journey at a Time." | Pinned 197-frame scroll sequence, word-by-word intro, glass search card |
| 2 | Find your next escape. | Tilt cards, spinning "Adventure awaits" badge |
| 3 | Popular destination | Snap-scrolling rail; photos drift inside their frames |
| 4 | Let's drive your journey | 4-step accordion (GSAP height), play-button video popup |
| 5 | Adventures from Around the World | Blog cards, featured story, photo mosaic |
| 6 | Moments Worth The Trip | 4 photo columns moving at 1.25×–3.3× scroll speed |
| 7 | Why Movade | Counters 0 → 12k / 10yrs / 50+, feature cards |
| 8 | Popular Tourist Spots | Featured 2×2 card with price, two smaller cards |
| 9 | Testimonials | 8 travelers drifting around a hub; hover pins one and opens its quote |
| 10 | Every Trip, Connected | Dotted world map; arcs draw Dhaka → 6 destinations in a loop |
| 11 | Footer | Links, newsletter, socials over a hills photo |

## 1. The pinned hero

![Six frames from the hero sequence](assets/frames-hero.jpg)

```text
ScrollTrigger(hero, start "top top", end "+=180%", scrub 1, pin: true)
  onUpdate(progress):
    progressRef = progress
    window.dispatch("hero-scroll-progress", progress)
  timeline: headline  y → -60, opacity → 0

every animation frame:
  frame = floor(progress × 196)
  draw images[frame] cover-fit onto the canvas
    — if it hasn't loaded yet, draw the nearest earlier loaded frame (up to 20 back)

loading: frames 1–3 first → 4–30 in batches of 6 → the rest in batches of 12
```

Other parts listen to `hero-scroll-progress`:

- **Nav:** hides (slides up 120px) while the hero is between 8% and 95% scrolled.
- **Search card:** fully visible up to 20%, gone by 35%, and it stops taking clicks once faded.

## 2. Smooth scroll that stays in sync

Lenis (duration 1.2, exponential ease) is driven by `gsap.ticker`, and every Lenis scroll calls `ScrollTrigger.update`. Pins, scrubs and reveals all read the same smoothed position. With reduced motion turned on, Lenis is skipped and native scrolling is used.

## 3. Motion details

- **Tilt cards:** the pointer position maps to ±4–7° of `rotateX/rotateY` through framer-motion springs (stiffness 200, damping 20) with 1000px perspective.
- **Magnetic buttons:** the button drifts up to 12px toward the cursor on a spring.
- **Reveals:** headings wipe in with `clip-path: inset(0 0 100% 0) → inset(0)` at 85% of the viewport. Cards rise with a blur-to-sharp fade.
- **Parallax wall:** each column starts offset above the frame (−45%, −95%, −45%, −75%). It then travels down by 2×, 3.3×, 1.25× and 3× the viewport height while the gallery crosses the screen (framer `useScroll`).
- **Testimonials:** idle avatars loop small drift-and-wobble keyframes (6–8.5s each). The active one stops, gets a lime ring, and its quote bubble slides to it.
- **World map:**
  - Each arc is a quadratic curve that draws in turn: 0.3s apart, 2s each, then a 2s pause before it repeats.
  - A glowing arrowhead rides each arc using CSS `offset-path`.
  - The pins pulse with SVG `<animate>`.

## 4. Faster than the original

The original page built its dotted world map in the browser on every visit, about 2 seconds of main-thread work. That delayed hydration, and so the preloader's 5-second fail-safe. Here the map is generated once into a static SVG, and the page responds about 3 seconds sooner on a first visit.

## 5. Phones (390px)

Every section stays, in the same order:

- the headline sits above the search card, which uses two-column fields
- the ☰ menu is a solid panel
- rails and testimonials become swipeable carousels
- the parallax wall becomes a 2-column photo grid
