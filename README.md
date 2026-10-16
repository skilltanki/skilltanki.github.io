# SkillTanki Landing

Landing page for **SkillTanki**, a free browser tank arcade in the spirit of the 2010 classic. No registration, no pay-to-win, nothing to install.

The site is a single static page built with Next.js and exported as plain HTML, ready to be hosted on GitHub Pages or any static file server.

![SkillTanki](assets/logo.webp)

## Screenshots

### Mobile (PWA)

| Battle: joystick, Fire and supplies | Garage: hulls and turrets |
| --- | --- |
| ![Mobile battle](assets/mob-14.webp) | ![Mobile garage](assets/mob-19.webp) |

| New room: mode, bots, password | Map selection |
| --- | --- |
| ![Mobile new room](assets/mob-20.webp) | ![Mobile map selection](assets/mob-13.webp) |

### Desktop

| Beach map | Deck 9 in space | City map with ramps | Red versus blue on the hills | Supplies bar in battle |
| --- | --- | --- | --- | --- |
| ![Beach map](assets/shot-1.webp) | ![Deck 9 in space](assets/shot-3.webp) | ![City map with ramps](assets/shot-4.webp) | ![Red versus blue on the hills](assets/shot-5.webp) | ![Supplies bar in battle](assets/shot-2.webp) |

| Battle over scoreboard | Tank selection | Map selection | Deathmatch: solo or multiplayer | Open battles list |
| --- | --- | --- | --- | --- |
| ![Battle over scoreboard](assets/shot-6.webp) | ![Tank selection](assets/shot-8.webp) | ![Map selection](assets/shot-11.webp) | ![Deathmatch: solo or multiplayer](assets/shot-9.webp) | ![Open battles list](assets/shot-10.webp) |

## What the page covers

The page is one scrolling layout with anchored sections:

| Section    | Anchor       | Content                                                                 |
| ---------- | ------------ | ----------------------------------------------------------------------- |
| Hero       | `#top`       | Headline, short pitch, Play button, key numbers (7 hulls, 9 turrets, 101 paints, 91 maps) |
| Why        | `#why`       | The problems the game solves: lost Flash game, pay-to-win, grind, accounts, no place to play with friends |
| Modes      | `#modes`     | Deathmatch, Team Deathmatch, Capture the Flag, Assault, Explore Map; public and private rooms |
| Tanks      | `#tanks`     | Seven hulls (Wasp to Mammoth) and nine turrets (Smoky to Shaft)         |
| Maps       | `#maps`      | 91 battlefields and 101 paints                                          |
| Controls   | `#controls`  | Keyboard-only layout: WASD / arrows, Space to fire, 1–5 for supplies, Tab for scoreboard |
| Mobile     | `#mobile`    | Installable PWA with touch controls, no app store required              |
| Gamepad    | `#gamepad`   | Controller and Steam Deck support in the mobile PWA                     |
| Play       | `#play`      | Final call to action with a one-line summary                            |

The Play buttons link to the game itself at `https://mobile.skilltanki.workers.dev/`.

## Tech stack

- [Next.js 15](https://nextjs.org/) with the App Router (`app/` directory), static export mode
- [React 19](https://react.dev/)
- Google font [Russo One](https://fonts.google.com/specimen/Russo+One) loaded via `next/font`
- Inline styles in JSX plus a tiny `app/globals.css` for resets and hover effects
- No TypeScript, no CSS framework, no runtime JavaScript beyond what Next ships

## Project structure

```mermaid
graph LR
    root["/ (repo root)"]
    root --> app["app/"]
    root --> public[""]
    root --> jsconfig["jsconfig.json<br/>baseUrl for absolute imports"]
    root --> nextconfig["next.config.mjs<br/>static export, trailingSlash,<br/>unoptimized images"]
    root --> pkg["package.json<br/>scripts and dependencies"]

    app --> layout["layout.jsx<br/>root layout, font setup,<br/>metadata and Open Graph tags"]
    app --> page["page.jsx<br/>the entire landing page"]
    app --> css["globals.css<br/>global resets and hover styles"]

    public --> nojekyll[".nojekyll<br/>lets GitHub Pages serve _next/"]
    public --> assets["assets/<br/>screenshots, artwork, logo,<br/>icon, supply icons (webp/png)"]
```

## Getting started

Requires Node.js 18.18 or newer.

```bash
npm install
npm run dev
```

Open http://localhost:3000 to see the page with hot reload.

## Building for production

```bash
npm run build
```

This runs `next build` with `output: 'export'` and writes the fully static site to the `out/` directory. To preview the exported site locally:

```bash
npm start
```

`npm start` serves the `out/` folder with [serve](https://www.npmjs.com/package/serve) via `npx`.

## Editing content

- **Copy and sections**: everything lives in `app/page.jsx`. Each section is a `<section id="...">` block with inline styles.
- **Page title, description, Open Graph**: edit the `metadata` export in `app/layout.jsx`.
- **Images**: drop new files into `assets/` and reference them with a relative path such as `assets/shot-1.webp`. Image optimization is disabled, so files are served exactly as committed. Prefer `.webp` for screenshots.
- **Colours and hover effects**: see `app/globals.css`. The dark palette (`#0b0d0a` background, `#8fdc8f` accent green) is repeated inline throughout the page.
