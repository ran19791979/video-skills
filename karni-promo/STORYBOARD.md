---
format: 1080x1920
duration: 25s
message: "כל התוכן, כל הלקוחות, מערכת אחת: מחזירים לכם את הזמן"
arc: Chaos → Clean home → Plan & do → Create & launch → Brand + CTA
audience: small-business owners and marketing consultants drowning in spreadsheets
mode: autonomous
---

<!--
Orchestrator-owned ROOT layers in index.html (scene workers do NOT build these):
  • Headline band y 250–520 for scenes 1–3:
      0.25–1.95  "טובעים בטבלאות?"   (slam, shakes with the chaos, glitches out on the cut)
      4.35–10.9  "כל התוכן. כל הלקוחות. מערכת אחת."  (three phrases arriving 4.35 / 4.85 / 5.45)
      11.35–17.9 "יוצרים, מתזמנים ומשגרים" + "בקליק אחד." (second line lands 11.9, re-glows at the click, 16.0)
  • Seam light-sweeps + flashes at 4.0, 11.0, 18.0 (≈0.3 s each).
Scene compositions keep the headline band clear (scenes 2–3) and never draw these texts.
All times inside a frame block are LOCAL to that scene (0 = the scene's first frame).
-->

## Frame 1 — Chaos → clean home

- src: compositions/s1-chaos-home.html
- duration: 4s
- poster: 3.4s
- transition_in: cut
- status: outline
- blueprint: compose
- rules: spring-pop-entrance, chromatic-glitch, stat-bars-and-fills, particle-burst
- scene: Spreadsheets, sticky notes and alerts pile up and shake. Glitch-snap, hard cut to the clean dashboard home: "שלום, הדס 👋" and three rings running 0→100%.
- voiceover: (none, silent video; reveal on the beats below)

Scene 1 (0.00–1.85s) CHAOS. It fills the whole 1080×1920 frame over the night-purple background, deliberately messy, grey and noisy. Every element is HTML:
  - 3 spreadsheet sheets: white/grey grid tables with header row "לקוח | פוסט | תאריך | סטטוס | הערות", 6–8 rows of fictional data (client names from frame.md, dates like 12.10, statuses like "באיחור!", "???", "לבדוק", "טיוטה 3"), a few cells highlighted pale red, one cell with a red circle scribble. They are tilted ±4–9° and overlap, and slam in from off-frame at 0.00 / 0.12 / 0.24 (fast expo.out). The first sheet is already visible by 0.15 s.
  - 6 sticky notes (lavender `#EBDDFB`, white, light grey; one may be pale yellow) with short scribbled Hebrew: "לשלוח ללוטוס עד 12:00!!", "איפה הבריף של השקד?", "לתזמן רילס לראשון", "לא לשכוח אישור לקוח", "סטורי?? רילס??", "דדליין מחר!!!". Each is rotated with a pin dot. They pop in one after another between 0.25 and 1.2 (spring-pop-entrance, back.out).
  - 5 notification toasts (white rounded cards with an app-icon circle and a red badge), sliding down and stacking 0.40–1.50: "WhatsApp · 23 הודעות חדשות", "תזכורת: פוסט לא פורסם", "מייל: איפה הטיוטה?", "יומן: 3 דדליינים היום", "פייסבוק: 12 תגובות ממתינות". A bell icon with a red badge counts 3 → 99+.
  - Keep a clear zone y 250–520 roughly in the middle of the chaos (sheets may pass behind it), because the root headline "טובעים בטבלאות?" slams there at 0.25.
  - From 1.0 to 1.85 the whole chaos wrapper shakes harder and harder: deterministic sine jitter, amplitude 0 → 12 px, plus a ±1° wobble.
Scene 2 (1.80–1.95s) THE SNAP. A chromatic-glitch slice burst on the chaos wrapper: RGB-split copies plus 4–6 horizontal slice bands displaced, quantized-time jitter.
Scene 3 (1.95s) HARD CUT. `tl.set` hides the chaos and shows the home, with a white flash layer at full opacity at 1.95 fading to 0 by 2.12.
Scene 4 (1.95–4.00s) CLEAN HOME. The app window from frame.md (y 560–1600). Topbar title "דף הבית", mobile-nav active item "בית". Rebuild faithfully from karnidashbord `renderHome()` and `donut()` (script.js ~1610–1720) and the `.home-greeting`/`.kpi-*` CSS (style.css ~366–410), at 2× scale:
  - 2.00–2.35: greeting "שלום, הדס 👋" (Rubik 700, 54 px) and sub-line "יום חמישי, 15 באוקטובר · הנה תמונת המצב של הדסק שלך" (muted, 28 px) rise in, 24 px with fade.
  - 2.15–2.50: KPI grid, 2×2 (gap 24). The tiles spring-pop in with a ≤0.35 s stagger:
      ① ring + "8" + "ממתינים לאישורך" + "מתוך 21 בתהליך"
      ② ring + "13" + "מתוזמנים לפרסום" + "הקרוב: 16.10 בשעה 18:00"
      ③ ring + "24" + "פורסמו החודש" + "מתוך 24 בתוכנית החודשית"
      ④ people icon (kpi-icon) + "5" + "לקוחות" + "5 עם תוכן בתהליך"
    Draw the rings bigger than 2× for impact: about 150 px diameter, stroke 14, track `#EFE7F8`, progress `--brand`, round cap, starting at 12 o'clock.
  - 2.40–3.60: **the three rings run 0% → 100%** (stroke-dashoffset), each with its center % text counting 0 → 100 (Math.round, tabular-nums), staggered 0.12 s. The KPI numbers count up from 0 at the same time.
  - 3.55–3.95: each ring hitting 100% gets a quick glow pulse plus a small white/lilac sparkle burst (≤12 particles, seeded).
  - 2.50–2.85: under the grid, the card "🔔 דורש את הטיפול שלך" peeks in with 2 todo rows (client-color inline-end border, status chip, title, "צפי ואשרי" button) so the window is filled down to the nav.
  - Background outside the window: night-purple with a soft brand glow that brightens slightly after the cut.

## Frame 2 — Gantt dots → tasks check

- src: compositions/s2-gantt-todos.html
- duration: 7s
- poster: 5.6s
- transition_in: wipe
- status: outline
- blueprint: compose
- rules: spring-pop-entrance, viewport-change, svg-path-draw, particle-burst
- scene: The monthly gantt fills with colored client dots, one after another. Zoom into the tasks page, where a task gets checked with a drawn check mark and sparkles.
- voiceover: (none)

Scene 1 (0.00–0.35s) WHIP-IN. The app window enters with scale 1.06 → 1 and blur 10 → 0 px (expo.out). The night background is already there. Topbar "תכנון חודשי", mobile-nav active "תכנון". Keep y 250–520 clear (root headline band).
Scene 2 (0.30–3.40s) GANTT. Rebuild faithfully from karnidashbord `ganttSection()` (script.js ~2969–3100) and the `.gantt*`/`.g-dot` CSS (style.css ~769–860) at 2×:
  - Toolbar: month title "אוקטובר 2026" with ‹ › arrows and a client-filter pill.
  - Grid: the client-name column on the RIGHT (5 fictional clients, each with a color swatch). Day columns are 8–19 October (12 days; RTL, so day 8 is next to the names and the dates run leftward). Day-name/number header, weekend columns shaded `--bg`, today column (15) tinted `--brand-soft` with a brand top marker.
  - **Dots land one after another**: 13 client-colored g-dots (about 38 px, 4 px white border, soft shadow) drop into their cells from about 90 px above with back.out(2.2). Each landing shows a squash (scaleY 0.8 → 1) plus a faint expanding ring in the client color. Cadence: the first 4 dots every 0.28 s, the rest every 0.18 s (accelerating), with the last landing by 3.2. Spread them over different clients and days so the board looks planned and full.
  - 2.9–3.4: the legend row (client color dots + names) fades up under the grid.
Scene 3 (3.45–4.30s) ZOOM. viewport-change camera: the whole window content pushes in (scale 1 → 2.6, `power3.in`, blur ramps 0 → 8 px) toward the "משימות" item of the mobile nav. That nav item lights up (brand color plus glow) at 3.5, just before the push. A white-lilac flash peaks at 4.15. The tasks page then comes in with scale swap transition (recipe in RULES_DIR): scale 1.18 → 1, blur 8 → 0, expo.out, 4.15–4.45.
Scene 4 (4.15–7.00s) TASKS PAGE. Rebuild from `renderTodos()`/`renderTodosList()`/`todoRowHtml` (script.js ~2000–2150) and the `.todo-*` CSS at 2×. Topbar "משימות", nav active "משימות":
  - Summary line "4 משימות פתוחות · 2 להיום" and an urgent panel "דחוף היום" with 2 small entries.
  - List card with 4 rows. Each row has the round check button on the RIGHT, the title, and meta (client tag in client color, due date, priority flag):
      "לאשר טיוטה לסטודיו לוטוס" · היום
      "לתזמן רילס למאפיית השקד" · היום
      "לצלם מוצרים חדשים לבוטיק אלמה" · מחר
      "דו״ח חודשי לקליניקה ירוקה" · יום ראשון
    The rows waterfall in, 4.30–4.65 (≤0.35 s total stagger).
  - 4.90–5.60: **check the first task**. A tap cursor (white arrow with purple glow) arrives at the first row's check button at 4.90. Press at 5.05 (press release spring (recipe in RULES_DIR)). The circle fills `--brand`, a white check-mark path draws in 0.28 s (svg-path-draw), a sparkle burst (≤20, seeded, lilac/white) fires from the button, a strike-through line draws across the title right-to-left, and the title fades to `--muted`. The summary counts "4" → "3".
  - 5.90–6.60: the checked row slides down under a new "בוצעו" divider at the bottom of the list. The remaining rows close the gap (transform only). Gentle settle after that; nothing exits.

## Frame 3 — Writing desk: brief writes itself → launch

- src: compositions/s3-write-desk.html
- duration: 7s
- poster: 5.2s
- transition_in: wipe
- status: outline
- blueprint: compose
- rules: discrete-text-sequence, particle-burst, cursor-click-ripple, ambient-glow-bloom
- scene: The writing desk. A brief types itself with purple sparkles shedding from the caret. The Facebook and Instagram check marks light up, the cursor clicks "✨ צרי לי פוסט", and the post is created and scheduled.
- voiceover: (none)

Scene 1 (0.00–0.35s) WHIP-IN, same as frame 2 (scale 1.06 → 1, blur 10 → 0). Topbar "כתיבת פוסט", nav active "כתיבה". Keep y 250–520 clear.
Scene 2 (0.20–0.60s) FORM. Rebuild from `renderWrite()` (script.js ~2342–2420) and the `.desk-layout`/`.field-group`/`.checkbox-row`/`.btn-primary` CSS at 2× (mobile, single column):
  - Page head "כתיבת פוסט חדש" + page-sub "בריף קצר, והמערכת מנסחת עבורך".
  - Card with fields, top to bottom: "לקוח" (a select showing "סטודיו לוטוס" with a `#EAB308` dot and a chevron) · "נושא הפוסט" (input already holding "סדנת יוגה בזריחה") · "בריף / נקודות עיקריות" (textarea, 3 lines tall, empty, focused with a brand focus ring) · "פלטפורמות לפרסום" (checkbox row: [ ] פייסבוק with the Facebook glyph, [ ] אינסטגרם with the Instagram glyph, both UNCHECKED at first) · full-width primary button "✨ צרי לי פוסט".
  - It must fit inside the window above the mobile nav. Tighten vertical spacing if needed, but keep the 2× type scale.
Scene 3 (0.60–3.50s) **THE BRIEF WRITES ITSELF**. Use discrete-text-sequence to type three lines into the textarea, RTL, about 22 chars/s:
      "• סדנת יוגה בזריחה, שבת 07:00"
      "• מתאים גם למתחילים"
      "• 20% הנחה לנרשמים השבוע"
  - Brand-colored caret (context sensitive cursor (recipe in RULES_DIR) blink driven from `tl.time()`).
  - **Purple sparkles**: a continuous seeded stream of small 2D four-point stars (brand, violet, lilac, white; 8–18 px) sheds from the typing frontier. Each drifts up/outward 30–90 px, twinkles (scale 0 → 1 → 0) and fades within 0.6–0.9 s. About 6–8 alive at a time. Use precomputed per-line x/y constants for the frontier (no layout measurement at render), since RTL lines grow leftward from the right edge.
  - The textarea border glow breathes softly while typing (ambient-glow-bloom, bounded).
Scene 4 (3.60–4.40s) PLATFORMS LIGHT UP. Check "פייסבוק" at 3.65, then "אינסטגרם" at 4.00: the box fills `--brand` with spring-pop (back.out), a white check draws, a purple glow halo blooms and settles, and the platform glyph brightens. A mini sparkle burst (≤10) per box.
Scene 5 (4.50–5.50s) CLICK. A cursor (white arrow, purple glow) glides in from the lower left to the button center (4.50–4.95, power3.out). Click at 5.00 (cursor-click-ripple): cursor and button compress together (press release spring (recipe in RULES_DIR)), a white ripple expands from the click point, a sparkle burst (≤24) fires, and the button glow flares.
Scene 6 (5.50–7.00s) RESULT. The button label swaps (scale-swap) to a shimmer "יוצרת…" at 5.50, then to "✓ הפוסט מוכן" at 5.95. A success toast slides up from the bottom of the window (above the nav) at 6.05: "נוצר ותוזמן · ראשון 18:00" with a blue "מתוזמן" status-chip dot and small Facebook and Instagram glyphs. Hold until the end, with a gentle glow breathe and no exits.

## Frame 4 — Brand + CTA

- src: compositions/s4-brand-cta.html
- duration: 7s
- poster: 5.5s
- transition_in: flash
- status: outline
- blueprint: compose
- rules: svg-path-draw, waterfall-entry, svg-icon-enrichment, ambient-glow-bloom
- scene: A purple-white color transition opens onto a glowing purple field. "רובי יניר אוטומציה" ignites as a subtle neon sign, "מחזירים לכם את הזמן" cascades in under it, and the CTA "שלחו הודעה לפרטים" springs up.
- voiceover: (none)

This frame has NO app window and the root headline band is empty, so use the whole frame. Keep all text between y 560 and y 1550 and centered horizontally.
Scene 1 (0.00–0.75s) **PURPLE-WHITE COLOR TRANSITION**. The frame starts pure white (it continues the root flash). A brand-gradient circle, `--grad-brand` with night-purple outer corners, expands from the center via clip-path circle 0% → 150% (expo.inOut). A soft white glow rim rides its edge. Behind it, a second lilac-to-white band sweeps diagonally just ahead of it. By 0.75 the frame is a rich purple field: brand gradient center, `--night` vignette corners, two slow-drifting radial glows.
Scene 2 (0.80–2.50s) NEON BRAND. Two lines, centered:
  - "רובי יניר": Rubik 800, about 140 px.
  - "אוטומציה": Rubik 600, about 92 px, letter-spacing 0.06em.
  - Style both in white with a subtle neon glow: text-shadow layers of white core 0 0 2px, lilac 0 0 10px, brand 0 0 28px, brand 0 0 60px at ~0.45 alpha.
  - Ignite each word like a neon tube, with a deterministic flicker over 0.45 s (opacity steps 0 → .85 → .15 → 1 → .5 → 1, stepped ease, driven from timeline time). Word 1 ignites at 0.85, word 2 at 1.25.
  - A thin rounded-rect neon outline (SVG stroke, lilac, with glow) draws around both lines, 1.4–2.3 (svg-path-draw). Keep it subtle (stroke ~4 px, opacity ~0.8).
  - From 2.5 to the end the glow breathes gently (sine wave loop (recipe in RULES_DIR), finite repeat, glow amplitude ±15%).
Scene 3 (2.60–3.70s) TAGLINE. "מחזירים לכם את הזמן" (Rubik 600, about 64 px, white with lilac glow) cascades in word by word (waterfall-entry, from below, binary arrival). Next to it on the line's right side (RTL start), a small clock icon (SVG, lilac stroke) whose hands spin BACKWARD two turns and settle (svg-icon-enrichment).
Scene 4 (3.90–4.80s) CTA. A white pill button (radius 999, height about 120, padding 0 64 px) with brand-purple text "שלחו הודעה לפרטים" (Rubik 700, about 54 px) and a chat-bubble icon on its right. It springs up (spring pop entrance (recipe in RULES_DIR), back.out(1.8)) with a lilac halo glow behind it.
Scene 5 (4.80–7.00s) FINAL HOLD. The CTA gives one soft press-pulse at 5.40 (press release spring (recipe in RULES_DIR), scale 0.96 → 1). 20–30 seeded sparkles twinkle around the logo and CTA in a finite stagger. The background glows keep drifting. The final frame must read cleanly: logo, tagline and CTA fully visible and nothing mid-flicker.
