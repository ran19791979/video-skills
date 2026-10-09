---
workflow: general-video
flow: automation
storyboard: no
message: "כל התוכן, כל הלקוחות, מערכת אחת: מחזירים לכם את הזמן"
destination: instagram-reels
aspect: 1080x1920
language: he
length: 25s
angle: problem-solution product promo
---

## Intent

A promo test video for the "דסק מעקב ותוכן" dashboard (built by רובי יניר אוטומציה for הדס קרני, a digital marketing consultant). It goes from chaos (spreadsheets, sticky notes, alerts) to one clean system, and ends on the brand and a call to action. The user wants the best result possible with what is available here, without external files.

## Customizations

- Vertical 1080×1920 for Reels, **no sound**.
- **No screenshots**: the dashboard screens are rebuilt in HTML from the `karnidashbord` repo's code (read-only), so every element can move separately. The demo data and client names are fictional.
- Colors: purple, light purple, white.
- Scenes (user's wording):
  1. 0–4s: chaos of spreadsheets, sticky notes and notifications, then a sharp cut to the clean home page with "שלום, הדס" and rings running 0→100%. Text: "טובעים בטבלאות?"
  2. 4–11s: the gantt board with colored dots landing on it one after another, then a zoom to the tasks page with a check mark ticked on a task. Text: "כל התוכן. כל הלקוחות. מערכת אחת."
  3. 11–18s: the writing desk. A brief writes itself with purple sparkles, the check marks next to Facebook and Instagram light up, and a button is clicked. Text: "יוצרים, מתזמנים ומשגרים – בקליק אחד."
  4. 18–25s: a purple-white color transition, "רובי יניר אוטומציה" with a subtle neon effect, below it "מחזירים לכם את הזמן", and at the end "שלחו הודעה לפרטים".
- Effects: fast transitions, glow and sparkles, 2D only (no 3D).
- Hebrew: RTL only on text elements, never on `<html>`.
- **No dashes** (– — -) anywhere in on-screen text (user request, after the first build). Headline 3 reads "יוצרים, מתזמנים ומשגרים / בקליק אחד."

## Notes

- Rubik (the dashboard's own font) is vendored from the npm package `@fontsource/rubik` (OFL). Noto Color Emoji is copied from the system fonts. GSAP is vendored. Nothing is fetched at render time.
- Registry catalog searched (typewriter, oversized-cursor, caption-neon-glow, particle components exist). Every look is hand-built from the local rule recipes instead, to keep the project free of external files and keep full control of the Hebrew RTL text.
- No Studio preview handoff is possible from this cloud session. The user asked directly for a rendered MP4 plus an opinion, then iteration.
