---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use when Sensei asks to build websites, landing pages, dashboards, HTML/CSS/JS components, web UIs, or anything visual for the web. Output is a .html or .jsx file sent to Discord — a live preview link is automatically appended to the message.
---

This skill guides creation of distinctive, production-grade frontend interfaces that avoid generic "AI slop" aesthetics. Implement real working code with exceptional attention to aesthetic details and creative choices.

## Delivery Model (Arona-specific)

Output is a **`.html`** or **`.jsx`** file written to `OUTPUT_DIR`, sent to Discord via `send_output: "true"`. A live preview link is automatically appended — Sensei can click it to view instantly in browser.

**Choose format based on complexity:**
- **`.html`** — vanilla HTML/CSS/JS. Best for landing pages, static layouts, simple interactivity.
- **`.jsx`** — React component with hooks. Best for dashboards, interactive UIs, stateful apps.

### HTML output
```python
# page.html
import os
OUTPUT_DIR = os.environ.get("OUTPUT_DIR", "./output")
os.makedirs(OUTPUT_DIR, exist_ok=True)
html = """<!DOCTYPE html>..."""
with open(os.path.join(OUTPUT_DIR, "page.html"), "w", encoding="utf-8") as f:
    f.write(html)
```

### JSX output
```python
# app.jsx
import os
OUTPUT_DIR = os.environ.get("OUTPUT_DIR", "./output")
os.makedirs(OUTPUT_DIR, exist_ok=True)
jsx = """
import { useState } from "react";
export default function App() {
  return <div>Hello</div>;
}
"""
with open(os.path.join(OUTPUT_DIR, "app.jsx"), "w", encoding="utf-8") as f:
    f.write(jsx)
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

## Allowed CDN Imports

### For `.html` (self-contained)
For `.html`: use vanilla HTML/CSS/JS or lightweight CDN libs — no React.

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

### For `.jsx`
For `.jsx`: React 18 + hooks available. Use Tailwind utility classes for styling (pre-loaded in viewer). Available libraries: `recharts`, `lucide-react`, `lodash`, `d3`, `mathjs`.

```jsx
import { useState, useEffect, useRef } from "react";
import { LineChart, XAxis, YAxis, Tooltip, Line } from "recharts";
import { Camera } from "lucide-react";
import _ from "lodash";
```

---

## Starter Template

### HTML
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

### JSX
```jsx
import { useState } from "react";

export default function App() {
  const [count, setCount] = useState(0);

  return (
    <div className="min-h-screen bg-gray-950 text-white flex items-center justify-center">
      <div className="text-center">
        <h1 className="text-4xl font-bold mb-4">Title</h1>
        <button
          onClick={() => setCount(c => c + 1)}
          className="px-6 py-2 bg-violet-600 rounded-lg hover:bg-violet-500 transition"
        >
          Count: {count}
        </button>
      </div>
    </div>
  );
}
```

---

## Quality Checklist (before sending)

- [ ] Fonts load from Google Fonts CDN
- [ ] **HTML**: All CSS/JS inline or from CDN. Works from `file://`.
- [ ] **JSX**: Uses only available libraries. Default export is the root component. No required props.
- [ ] No broken images (use CSS shapes/gradients, or data URIs)
- [ ] Responsive (`viewport` meta tag, fluid widths)
- [ ] Animations feel intentional — not scattered
- [ ] Color palette is cohesive and defined in `:root` variables (HTML) or Tailwind classes (JSX)

---

Remember: this is an opportunity for extraordinary creative work. Don't hold back — commit fully to a distinctive vision. No two designs should look the same.
