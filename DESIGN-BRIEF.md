# BrightPath AI Literacy Summit 2026 — Design Brief

## What This Is

Build a single-page event website for a **fictional brand called "BrightPath"** hosting the **"AI Literacy Summit 2026"** — a free virtual conference for educators learning to integrate AI into their classrooms.

This is a **portfolio-safe adaptation** of a real project I built for Intuit for Education. The design system, layout, interactions, and animations are all based on that real site, but with all proprietary content, branding, and assets swapped out.

**Reference site (the original I built):** https://emilyblaster.github.io/VEC-2026/VEC-v3.html

---

## Page Section Order (top to bottom)

1. **Sticky Navigation** — dark navy background, frosted glass effect, logo left, nav links right, "Register Free" CTA button
2. **Hero Banner** — full viewport height, animated morphing gradient background (6 independent blob divs), large bold headline, subtitle, two CTA buttons, floating 3D icon (large, right side, with gentle rocking animation)
3. **Stats Bar** — dark navy background, 4 large animated counter numbers (count up on scroll) with labels below each
4. **Countdown Section** — Mode B gradient background (warm orange/coral dominant), "The Conference Is Coming" headline, 4-cell countdown timer (days/hours/minutes/seconds), "Free to all educators" text, register CTA
5. **Opening Keynote** — dark navy background, two-column layout: headline + description + CTA on left, large speaker placeholder photo on right (rounded corners, glass border)
6. **Community Photo Grid** — light/lavender background, "5,000+ Educators. One Mission." headline, asymmetric masonry grid of 7 placeholder images with stat counter overlays (white cards with large numbers), each image has a colored gradient tint overlay
7. **Why Attend** — Mode B gradient background (warm orange dominant, morphing blobs), "What You Will Walk Away With" headline, 4 glass-morphism cards numbered 01-04 with gradient bottom borders
8. **Session Tracks / Agenda** — cream/off-white background, 4 cards in a 2x2 grid, each representing a conference room/track with a colored top border accent, "View Full Agenda" CTA button
9. **Speakers** — dark navy background, "Experts in AI Education" headline, 6 speaker placeholder cards in a 3x2 grid, each with a gradient circle avatar, name, role, and colored category tag
10. **Curved Text Marquee** — light background section, large text following a downward arc/bowl SVG path that scrolls horizontally continuously, decorative 3D coin icon below, two diamond icons in opposite corners
11. **Stats / Social Proof** — light background continuation, large coin icon centered, "The Data Is In. It's Worth Every Minute." headline, 4 stat numbers in a row (97%, 89%, 92%, 4+)
12. **Sponsors** — light background fading to warm cream, "Presented With Support From" headline, row of gray sponsor placeholder boxes
13. **Footer** — dark navy background, logo + tagline left, nav link columns center, copyright bottom

---

## Design System

### Color Palette (CSS Custom Properties)

```css
:root {
  --fuchsia: #E523FF;    /* Hero gradient dominant */
  --agave: #00D0E0;      /* Cyan accent */
  --kiwi: #3BD85E;       /* Success/green accent */
  --cavendish: #FFE01B;  /* Yellow — NOT used for text, only decorative */
  --tomato: #FF5C37;     /* Warm orange, Mode B gradient dominant */
  --watermelon: #FF6C7A; /* Soft pink accent */
  --superblue: #3D6AFF;  /* Primary CTA buttons, links */
  --navy: #060B2B;       /* Dark backgrounds */
  --cream: #F5F3EE;      /* Light section backgrounds */
}
```

### Two Gradient Modes

**Mode A — Fuchsia Dominant (Hero):**
- 6 independently animated div elements (NOT a single CSS background gradient)
- Each blob is a large soft circle with `border-radius: 50%`, `filter: blur(80-120px)`, and its own unique `@keyframes` animation with different duration (18s, 22s, 25s, 20s, 28s, 32s)
- Fuchsia (#E523FF) dominates 60%+ of the canvas (3 of 6 blobs are fuchsia)
- Agave (#00D0E0) bleeds from left edge only
- Tomato (#FF5C37) is a small warm pocket
- Base background color: #CC10EE (vivid fuchsia so it's never dark)
- SVG noise texture overlay at 18% opacity with mix-blend-mode: overlay

**Mode B — Tomato/Orange Dominant (Countdown + Why Attend):**
- Same 6-blob animated div system
- Tomato (#FF5C37) dominates
- Fuchsia accent from upper area
- Agave cool edge on left
- Base background: #E85A00 (warm orange)

**CRITICAL: Never simplify the 6-blob system to a single CSS gradient. The individual divs are required for the morphing/breathing effect.**

### Typography

For portfolio version, use **freely available fonts**:
- **Display/Headlines:** Montserrat 800/900 from Google Fonts (bold, heavy, condensed feel)
- **Body:** Montserrat 400/500 or DM Sans 400/500
- **Labels/Tags/Mono:** DM Mono 400 from Google Fonts (letter-spaced, uppercase)

### Key Visual Effects

1. **Morphing gradient blobs** — each blob drifts on its own animation timer. Because timers are co-prime, the gradient never visibly loops. Wrap all animations in `@media (prefers-reduced-motion: reduce)` to pause.

2. **Floating 3D icon** — a large decorative icon (for BrightPath: use a brain, lightbulb, or robot icon) positioned on the right side of the hero, with a gentle CSS rocking/rotating animation.

3. **Curved text marquee** — SVG `<textPath>` on an arc path. Text scrolls continuously along the arc using `<animate>` on `startOffset`. Duplicate the text at -100% offset for seamless loop. Text is large, bold, ~30% opacity.

4. **Counter animations** — stat numbers count up from 0 when they scroll into view using IntersectionObserver + requestAnimationFrame.

5. **Scroll fade-in** — sections fade and slide up as they enter the viewport via IntersectionObserver.

6. **Glass morphism cards** — `background: rgba(255,255,255,0.07)`, `backdrop-filter: blur(12px)`, `border: 1px solid rgba(255,255,255,0.14)`.

7. **Sticky registration widget** — fixed to bottom-right of viewport, appears after scrolling past hero. White glass card with countdown, "Did we mention FREE?" text, and register CTA. Has close button.

8. **Diamond decorative icons** — small decorative gems placed in opposite corners of the marquee section, tilted at angles, with gentle floating animation.

9. **Photo grid color overlays** — each image in the community grid has a semi-transparent gradient overlay using brand colors (pink, green, orange, purple tints).

---

## Content for BrightPath AI Literacy Summit

### Event Details
- **Brand:** BrightPath
- **Event:** AI Literacy Summit 2026
- **Format:** Free virtual conference for educators
- **Theme:** Integrating AI into education

### Headline Ideas
- "Where AI Education Meets the Future"
- "Empowering Educators in the Age of AI"

### Stats Bar Numbers
- 5,000+ Educators Expected
- 20+ Breakout Sessions
- 4+ Audience Tracks
- 100% Free

### Conference Tracks (4 Rooms)
1. **Foundations Room** (Blue accent) — K-12 General Teachers: AI Basics, Prompt Engineering for Educators, Classroom AI Tools
2. **Applied Room** (Red/Orange accent) — CTE/STEM Teachers: AI in Project-Based Learning, Machine Learning Demos, Student AI Projects
3. **Ethics Room** (Orange accent) — Higher Ed Faculty: Responsible AI, AI Policy in Schools, Academic Integrity
4. **Leadership Room** (Green accent) — Administrators: AI Strategy for Districts, Budget Planning for AI, Change Management

### Why Attend Cards
1. Hands-On AI Activities — Prompt engineering workshops, AI tool demos, and lesson plan templates you can use tomorrow
2. Track-Specific Content — Four dedicated rooms for K-12 teachers, STEM/CTE, higher ed, and administrators
3. Industry Certifications — AI literacy credentials and professional development hours
4. Real-World Tech Skills — ChatGPT, Copilot, AI assessment tools, and classroom integrations

### Curved Marquee Text
"Invest In Your Classroom. Transform How Students Learn. Spend Your Time Teaching Students To Think."

### Satisfaction Stats
- 97% Satisfaction Rate
- 89% Would Attend Again
- 92% Found Content Actionable
- 4+ Audience Tracks

---

## Technical Requirements

- **Single HTML file** — all CSS and JS inline, no external dependencies except Google Fonts
- **No emojis** anywhere on the page
- **No Bootstrap or Tailwind** — pure CSS only
- **All colors via CSS custom properties** — never hardcode hex inline
- **mix-blend-mode: screen** on any icons/logos placed on dark backgrounds
- **@media (prefers-reduced-motion: reduce)** on ALL animations (blobs, floats, marquee, counters)
- **Placeholder images** — use solid gradient fills or https://picsum.photos for stock images until real ones are sourced
- **3D icons** — source free alternatives (e.g., from icons8.com/3d, flaticon, or create simple SVG illustrations). Need: brain/AI icon (hero), lightbulb, circuit/chip, robot/bot head

---

## What NOT to Do
- Do not reference Intuit, Intuit for Education, or any Intuit branding
- Do not use Avenir Next font (it's proprietary to Intuit)
- Do not use the Intuit 3D icon assets (piggy bank, coins, diamond) — source free alternatives
- Do not copy the VEC HTML directly — build fresh using this brief as the spec
- Do not use financial literacy content — this is about AI literacy

---

*This design brief describes the visual and interaction design of a portfolio project by Emily Green.*
*Original production site: Intuit for Education Virtual Educator Conference 2026*
*Portfolio adaptation: BrightPath AI Literacy Summit 2026*
