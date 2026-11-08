<div align="center">

<a href="https://movade-travel.vercel.app"><img src="assets/banner.svg" alt="Movade: a rotating 3D wireframe globe with a plane orbiting it, pulsing destination pins and a scroll-to-frame counter" width="100%"></a>

# Movade · Travel Agency

A scroll-driven travel landing page. The hero stays pinned while scrolling plays a 197-frame camera flight from above the clouds into a jungle waterfall, behind a glass search card. Below it: tilt cards, a destination rail, a parallax photo wall, floating testimonials and an animated flight-route world map.

[![Live demo](https://img.shields.io/badge/LIVE_DEMO-movade--travel.vercel.app-b6ff3c?style=for-the-badge&logo=vercel&logoColor=0b0f0d&labelColor=0b0f0d)](https://movade-travel.vercel.app)

![Next.js](https://img.shields.io/badge/Next.js-16-000?logo=nextdotjs) ![GSAP](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02?logo=greensock&logoColor=white) ![Lenis](https://img.shields.io/badge/Lenis-smooth_scroll-ff98a2) ![Framer Motion](https://img.shields.io/badge/Framer_Motion-12-0055ff?logo=framer&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind-v4-38bdf8?logo=tailwindcss&logoColor=white) ![Built with Claude Code](https://img.shields.io/badge/built_with-Claude_Code-d97757)

</div>

---

## 🎬 The 3D scroll, live

<div align="center">

<a href="https://movade-travel.vercel.app"><img src="assets/hero-scroll.gif" alt="Scrolling the pinned hero: the camera drops through the clouds into a jungle, the search card and nav fade away, then the next section slides up" width="100%"></a>

<sub>Recorded from the live site. Scroll position picks every frame of the camera move: it isn't a video. Click it to open the demo.</sub>

</div>

**Try these on the live site:**

| | |
|---|---|
| 🖱️ **Scroll slowly** through the hero: the camera flies down into the jungle, and the nav and search card step aside | 🔁 **Scroll back up**: the flight plays in reverse |
| 🔎 **Search** with an empty destination, then with one. Switch the **Hotel / Villa** tabs | 🃏 **Hover any photo card**: it tilts toward your pointer on a spring |
| ▶️ **Play** on "Let's drive your journey" opens the video popup (Esc closes it) | 🪜 **Open the steps** of the how-it-works accordion |
| 🧑‍🤝‍🧑 **Hover the floating travelers** in Testimonials to read each story | 🗺️ **Watch the map**: flight arcs draw from Dhaka to six destinations |
| 📱 **On a phone**, open the ☰ menu and jump to any section | ✉️ **Subscribe** in the footer |

---

## 📸 Screenshots

All taken from the live deployment at 1600 × 1000.

<table>
  <tr>
    <td width="50%"><img src="screenshots/desktop/01-hero.jpg" alt="Hero with search card"><br><sub><b>Hero</b>: frame 1, headline and the glass search card</sub></td>
    <td width="50%"><img src="screenshots/desktop/02-hero-mid.jpg" alt="Hero mid-scroll in the jungle"><br><sub><b>Hero, mid-scroll</b>: nav and search card step aside</sub></td>
  </tr>
  <tr>
    <td><img src="screenshots/desktop/03-escape.jpg" alt="Find your next escape"><br><sub><b>Find your next escape.</b>: tilt cards, spinning badge</sub></td>
    <td><img src="screenshots/desktop/04-destinations.jpg" alt="Popular destination rail"><br><sub><b>Popular destination</b>: snap rail with drifting photos</sub></td>
  </tr>
  <tr>
    <td><img src="screenshots/desktop/05-lets-drive.jpg" alt="Let's drive your journey"><br><sub><b>Let's drive your journey</b>: 4-step accordion</sub></td>
    <td><img src="screenshots/desktop/06-adventures.jpg" alt="Adventures from Around the World"><br><sub><b>Adventures</b>: blog cards and a photo mosaic</sub></td>
  </tr>
  <tr>
    <td><img src="screenshots/desktop/07-moments.jpg" alt="Moments Worth The Trip parallax"><br><sub><b>Moments Worth The Trip</b>: 4 columns at different speeds</sub></td>
    <td><img src="screenshots/desktop/08-why.jpg" alt="Why Movade"><br><sub><b>Why Movade</b>: counters run up to 12k · 10yrs · 50+</sub></td>
  </tr>
  <tr>
    <td><img src="screenshots/desktop/09-spots.jpg" alt="Popular Tourist Spots"><br><sub><b>Popular Tourist Spots</b>: featured 2×2 card</sub></td>
    <td><img src="screenshots/desktop/10-testimonials-hover.jpg" alt="Testimonials constellation"><br><sub><b>Testimonials</b>: hover a traveler to read their story</sub></td>
  </tr>
  <tr>
    <td><img src="screenshots/desktop/11-network.jpg" alt="Every Trip, Connected world map"><br><sub><b>Every Trip, Connected</b>: animated flight arcs</sub></td>
    <td><img src="screenshots/desktop/12-footer.jpg" alt="Footer over green hills"><br><sub><b>Footer</b>: newsletter over the hills photo</sub></td>
  </tr>
</table>

### 📱 On phones (390 px)

<table>
  <tr>
    <td><img src="screenshots/mobile/01-hero.jpg" alt="Mobile hero"></td>
    <td><img src="screenshots/mobile/02-escape.jpg" alt="Mobile escape cards"></td>
    <td><img src="screenshots/mobile/03-lets-drive.jpg" alt="Mobile accordion"></td>
    <td><img src="screenshots/mobile/04-spots.jpg" alt="Mobile spots"></td>
  </tr>
  <tr>
    <td><img src="screenshots/mobile/05-testimonials.jpg" alt="Mobile testimonials carousel"></td>
    <td><img src="screenshots/mobile/06-network.jpg" alt="Mobile world map"></td>
    <td><img src="screenshots/mobile/07-menu.jpg" alt="Mobile menu"></td>
    <td><img src="screenshots/mobile/08-footer.jpg" alt="Mobile footer"></td>
  </tr>
</table>

---

## 🛠️ How it works

<img src="assets/frames-hero.jpg" alt="Six frames from the 197-frame hero sequence: clouds, canopy, waterfall, trail" width="100%">

- **The hero is a pinned scroll timeline.** GSAP ScrollTrigger pins the hero for 180% of the viewport. Scroll progress (0 → 1) picks one of 197 frames, which a canvas paints "cover"-fit on every animation frame.
- **One progress value drives everything.** The pin broadcasts its progress: the nav hides between 8% and 95%, the search card fades between 20% and 35%, and the headline lifts away.
- **Smooth, synced scrolling.** Lenis runs on GSAP's ticker, so the smooth scroll and the scroll animations never drift apart.
- **Springy 3D tilt.** Cards tilt toward the pointer with framer-motion springs. Buttons drift toward the cursor.
- **A static world map.** The dotted map is pre-rendered once to an SVG, so it doesn't cost 2 seconds of browser work on every visit. The flight arcs and arrowheads are animated SVG on top.

Full details are in **[HOW-IT-WORKS.md](HOW-IT-WORKS.md)**.

## 💬 How it was built

Rebuilt with Claude Code, starting with:

```text
/clone-website https://github.com/alagappan567/travel-agency
```

**[HOW-IT-WAS-BUILT.md](HOW-IT-WAS-BUILT.md)** lists every prompt word for word, with what each one did: reading the reference, porting it, fixing what broke on phones, testing, and deploying.

This repo holds the showcase only: screenshots, recordings and write-ups. The site's source code isn't included.

## 🙏 Credits

- Design, copy, photos and frame sequence come from **[alagappan567/travel-agency](https://github.com/alagappan567/travel-agency)**. This is an independent rebuild of that repo's page.
- Built with [Claude Code](https://claude.com/claude-code).

> **Concept site.** Movade is a fictional travel agency. Search, booking, sign-up and the newsletter are demos: they show a message, and nothing is booked or sent.
