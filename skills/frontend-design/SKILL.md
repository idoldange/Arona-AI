---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use when Sensei asks to build websites, landing pages, dashboards, HTML/CSS/JS components, web UIs, or anything visual for the web. Output is a single self-contained .html file sent to Discord — Sensei downloads and opens it in browser.
---

This skill guides creation of distinctive, production-grade frontend interfaces that avoid generic "AI slop" aesthetics. Implement real working code with exceptional attention to aesthetic details and creative choices.

## Delivery Model (Arona-specific)

Output is always a **single self-contained `.html` file** — all CSS and JS inline, no external dependencies except CDN imports. Write to `OUTPUT_DIR` and set `send_output: "true"` so it's sent to Discord automatically. Sensei downloads and opens it locally in their browser.

```python
# page.html
import os

OUTPUT_DIR = os.environ.get("OUTPUT_DIR", "./output")
os.makedirs(OUTPUT_DIR, exist_ok=True)

html = """<!DOCTYPE html>
<html lang="en">
<!-- ... all CSS/JS inline ... -->
</html>"""

with open(os.path.join(OUTPUT_DIR, "page.html"), "w", encoding="utf-8") as f:
    f.write(html)
print("Done.")
```

Run via: `run_code(action="run_code", code=<above>, send_output="true")`

---

## Design Thinking

Before writing a single line of code, commit to a **BOLD aesthetic direction**:

- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick an extreme — brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian. Use these for inspiration but design something true to context.
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work — the key is intentionality, not intensity.

---

## Frontend Aesthetics Guidelines

- **Typography**: Beautiful, unique, distinctive fonts from Google Fonts (CDN — works in self-contained HTML). Avoid Arial, Inter, Roboto. Pair a distinctive display font with a refined body font.
- **Color & Theme**: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant color + sharp accent > timid evenly-distributed palettes.
- **Motion**: CSS animations and transitions. Focus on high-impact moments — one well-orchestrated page load with staggered reveals (`animation-delay`) creates more delight than scattered micro-interactions. Hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density.
- **Backgrounds & Visual Details**: Atmosphere and depth — gradient meshes, noise textures, geometric patterns, layered transparencies, dramatic shadows, grain overlays, custom cursors.

**NEVER** use: purple gradients on white, Inter/Roboto/Space Grotesk, predictable card layouts, cookie-cutter component patterns, generic hero sections.

---

## Allowed CDN Imports (self-contained HTML)

These load from CDN and work offline once cached:

```html
<!-- Fonts (Google Fonts) -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=DM+Sans:wght@300;400;600&display=swap" rel="stylesheet">

<!-- Icons -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<!-- Animation library -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>

<!-- Charts -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<!-- Highlight.js (code blocks) -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/styles/github-dark.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>
```

No React, no Tailwind CDN (too large) — use vanilla HTML/CSS/JS or lightweight libs.

---

## Starter Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Page Title</title>
<link href="https://fonts.googleapis.com/css2?family=CHOSEN_FONT&display=swap" rel="stylesheet">
<style>
  :root {
    --bg:      #0f0f13;
    --surface: #1a1a24;
    --accent:  #7c6aff;
    --text:    #e8e6f0;
    --muted:   #888;
    --font-display: 'Chosen Font', serif;
    --font-body:    'Other Font', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* === ANIMATIONS === */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .reveal { animation: fadeUp 0.8s cubic-bezier(.16,1,.3,1) both; }
  .delay-1 { animation-delay: 0.15s; }
  .delay-2 { animation-delay: 0.30s; }
  .delay-3 { animation-delay: 0.45s; }

  /* === YOUR COMPONENTS HERE === */
</style>
</head>
<body>

  <!-- Content here -->

<script>
  // Interactivity here
</script>
</body>
</html>
```

---

## Quality Checklist (before sending)

- [ ] Fonts load from Google Fonts CDN
- [ ] All CSS inline (no external `.css` files)
- [ ] All JS inline or from CDN (no local `.js` files)
- [ ] Works when opened directly from filesystem (`file://`)
- [ ] No broken images (use CSS shapes/gradients, or data URIs)
- [ ] Responsive (`viewport` meta tag, fluid widths)
- [ ] Animations feel intentional — not scattered
- [ ] Color palette is cohesive and defined in `:root` variables

---

Remember: this is an opportunity for extraordinary creative work. Don't hold back — commit fully to a distinctive vision. No two designs should look the same.
