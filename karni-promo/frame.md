# frame.md — design truth for "דסק מעקב ותוכן" promo

Every scene pulls its look from this file. Copy text for each scene comes from STORYBOARD.md, never from here.

## Canvas

- 1080 × 1920 portrait (Instagram/Facebook Reels), 30 fps, 25 s, **no audio**.
- **Reels safe zones**:
  - Top 230 px: the platform covers this with UI. No meaningful content.
  - **Headline band (y 250–520)**: belongs to the ROOT headline layer that `index.html` draws in scenes 1–3. Scene compositions keep this band clear in scenes 2 and 3. Their app UI starts at y ≥ 560. In scene 1 the chaos may fill the whole frame, because the headline slams over it.
  - **App stage (y 560–1600)**: the rebuilt dashboard lives here.
  - Bottom (y > 1600): the platform's caption and username area. Decorative only (glow, sparkles, background), never text or UI you need to read.
  - Right edge x > 960 and y > 1150: the reel action buttons sit here. Never put a key interaction (click target, check mark) there.

## Palette — purple, light purple, white (from the dashboard's own tokens, karnidashbord/style.css :root)

| token | value | use |
|---|---|---|
| `--brand` | `#6D00CC` | primary purple: buttons, rings, active states, glow core |
| `--brand-rgb` | `109, 0, 204` | for rgba() glows |
| `--brand-hover` | `#5B00AB` | pressed button |
| `--violet` | `#A518DB` | gradient mid (sidebar gradient) |
| `--orchid` | `#D63ACF` | gradient start; use sparingly, only inside the brand gradient |
| `--grad-brand` | `linear-gradient(198deg, #D63ACF 0%, #A518DB 48%, #6D00CC 100%)` | the dashboard's sidebar gradient |
| `--brand-soft` | `#F5EBFF` | light purple surfaces, chips |
| `--brand-mid` | `#E5CFFA` | light purple borders, ring track |
| `--lilac` | `#C9A8F5` | light purple text on dark |
| `--white` | `#FFFFFF` | cards, text on purple |
| `--bg` | `#F8F7FB` | app page background |
| `--border` | `#ECE8F2` | card borders |
| `--text` | `#221933` | app body text |
| `--text-soft` | `#5D5470` | app secondary text |
| `--muted` | `#918AA3` | app meta text |
| `--night` | `#14052B` | deep purple video background (outside the app window) |
| `--night-2` | `#2A0A52` | background gradient partner |

Non-palette colors, used ONLY where the real dashboard uses them as data:
- Client colors (gantt dots, client tags): `#EAB308 #EC4899 #8B5CF6 #14B8A6 #881337` (CLIENT_COLORS, in client-id order).
- Status dots: planned `#667085`, waiting `#F79009`, scheduled `#2970FF`, published `#12B76A`. Facebook blue `#1877F2` and the Instagram gradient only on their platform icons.
- Scene 1 chaos may use desaturated greys plus a few red `#D92D20` notification badges. Clutter should feel noisy and grey against the clean purple-white answer.

## Video background (outside the app window)

- Deep purple field: `radial-gradient(ellipse at 50% 30%, #2A0A52 0%, #14052B 70%)`.
- Plus one or two soft brand glows: radial `rgba(109,0,204,0.5)`→transparent, about 900 px, drifting slowly.
- Each scene paints its own full-bleed background as a dedicated full-duration `class="clip"` layer, never on `#root`.

## Typography

- Family: **Rubik** (the dashboard's font), vendored at `assets/fonts/`. Every composition must declare these `@font-face` rules **inside its own `<template>`**:

```css
@font-face { font-family: "Rubik"; src: url("assets/fonts/rubik-hebrew-400-normal.woff2") format("woff2"); font-weight: 400; unicode-range: U+0307-0308, U+0590-05FF, U+200C-2010, U+20AA, U+25CC, U+FB1D-FB4F; }
@font-face { font-family: "Rubik"; src: url("assets/fonts/rubik-latin-400-normal.woff2") format("woff2"); font-weight: 400; }
/* repeat both lines for weights 500, 600, 700, 800 with the matching file names */
@font-face { font-family: "Noto Color Emoji"; src: url("assets/fonts/NotoColorEmoji.ttf") format("truetype"); }
```

  Paths are relative to the **project root** (sub-composition markup is cloned into `index.html`'s document, so `url()` resolves against `index.html`). Verify in a snapshot that the Hebrew renders in Rubik: round, geometric letterforms. If you see the narrower DejaVu shapes, the path is wrong.
- Stack: `font-family: "Rubik", "Noto Color Emoji", sans-serif;`. The only emoji the dashboard really shows here is 👋 in "שלום, הדס 👋" and ✨ on the generate button. Other icons are inline SVG (stroke 2, round caps, like the dashboard's sidebar icons).
- **App UI scale = 2× the dashboard's CSS px.** The dashboard's sizes are tuned for desktop. In this 1080-wide frame, every value from style.css is doubled: kpi-num 30px → 60px, card radius 14px → 28px, `--fs-base` 14.5px → 29px, `--fs-sm` 12.5px → 25px, and so on. This keeps the UI readable on a phone.
- Headline layer (root, drawn by the index): Rubik 800, 88–96 px, white, line-height 1.12, glow `text-shadow: 0 0 24px rgba(165,24,219,0.55), 0 0 2px rgba(255,255,255,0.6)`. Emphasis words in `--lilac`.

## Hebrew / RTL — hard rule

- **Never** put `dir="rtl"` on `<html>`. In HyperFrames it renders a fully black video.
- Put `direction: rtl` (and `text-align: right` where needed) **on the text-bearing elements or on an app-window wrapper div**. The browser's bidi algorithm then shapes mixed Hebrew/Latin/number text correctly.
- RTL layout means the app's "start" side is on the RIGHT: page titles, labels and list content align right; the date column in the gantt reads from right to left (day 1 on the right). Mirror the dashboard faithfully.
- Hebrew copy is feminine second-person, like the dashboard ("צרי לי פוסט", "צפי ואשרי").

## The app window (shared component, used in scenes 1b, 2 and 3)

A rebuilt **mobile layout** of the dashboard (its `@media (max-width: 960px)` mode, with no sidebar and a bottom `.mobile-nav`), drawn at 2× scale inside a device-like window:

- Window: x 60–1020 (width 960), y 560–1600 (height 1040), radius 44 px, background `--bg`, `overflow: hidden`.
  - Shadow: `0 40px 120px rgba(20,5,43,0.55), 0 0 0 1px rgba(255,255,255,0.08)`.
  - Outer purple glow ring: `0 0 80px rgba(109,0,204,0.45)`.
- Inside, top to bottom:
  - **Topbar**: 112 px tall, white, bottom border `--border`. On the right (RTL start) the page title, Rubik 700 34 px. On the left, a search pill (light bg, magnifier icon, placeholder "חיפוש…") and a bell icon with a small purple badge.
  - **Content**: padding 36 px 36 px.
  - **Mobile nav**: 120 px tall, white, top border `--border`, `box-shadow: 0 -8px 40px rgba(34,25,51,0.08)`. Five items with an icon plus a 20 px label: בית · משימות · מעקב · תכנון · כתיבה. The active item is `--brand`, the others `--muted`.
- Cards: white, radius 28, border 2 px `--border`, shadow `0 4px 20px rgba(34,25,51,0.07)`, padding 36.
- Primary button (`.btn-primary`): `--brand` background, white Rubik 600, radius 20, height 96, shadow `0 8px 32px rgba(109,0,204,0.38)`.

## Effects vocabulary (2D only, no 3D transforms/perspective)

- **Glow**: layered `box-shadow` / `text-shadow` in brand purple; `filter: drop-shadow(...)` for SVG. Peak glow opacity ≤ 0.6.
- **Sparkles**: 2D four-point stars (inline SVG, or `clip-path` diamond plus cross) in white, `--lilac` and `--brand`. Drive them from a **seeded** deterministic PRNG (for example mulberry32 with a fixed seed), never `Math.random()`. Bursts run ≤ 40 particles, scale/opacity twinkle, ballistic drift (rule `particle-burst`).
- **Fast transitions**: 0.25–0.45 s, using `expo.out` / `power4.out` / `back.out(1.6)`. Scene entrances may whip in with a brief scale + blur (`filter: blur()` 10 → 0 px) over ≤ 0.35 s.
- Ambient: slow background glow drift (`ambient-glow-bloom`). No motion loops that never settle; any repeat must be finite.

## Demo data (fictional; NEVER use the dashboard's real seed clients)

Clients, in client-id order, which also sets the client color:
1. סטודיו לוטוס — `#EAB308`
2. מאפיית השקד — `#EC4899`
3. קליניקה ירוקה — `#8B5CF6`
4. בוטיק אלמה — `#14B8A6`
5. גלריה כחולה — `#881337`

Month shown: אוקטובר 2026. The greeting date line reads "יום חמישי, 15 באוקטובר".
