# KumoHop Design System & Style Guide

A complete reference guide for the KumoHop aesthetic, visual language, UI components, typography, and frontend tokens. Use this specification to ensure any sister project, companion app, or new website looks and feels authentically aligned with **KumoHop**.

---

## 1. Design Philosophy & Aesthetic Essence

The KumoHop design language is inspired by **modern editorial craft, Swiss modernism, and quiet studio minimalism**:

- **Warm Minimalist Base**: Avoid stark clinical `#000000` / `#ffffff`. Instead, use a warm paper-tinted neutral background (`#f7f7f5`) paired with deep charcoal (`#171717`).
- **Hairline Architectural Grid**: Structural layout dividers use crisp `1px solid` hairline borders (`#ddddda`) rather than drop shadows or heavy cards.
- **Tight, Confident Typography**: High-contrast typographic scale with expressive negative letter-spacing on bold headings, contrasted with wide-spaced uppercase eyebrow labels.
- **Selective Micro-Color**: The UI is 95% monochrome, allowing intentional accent pops — notably signature **KumoHop Orange** (`#ff5e3a`), **Signal Green** (`#59c36a`), and **Electric Blue** (`#2563eb`) — to draw immediate visual focus.
- **Sharp & Grounded**: Avoid bubbly pills or exaggerated rounded corners on buttons and structural containers. Rectangular precision gives tools and projects a refined, tactile feel.
- **Editorial Motion**: Subtle `fade-up` scroll reveals using smooth cubic bezier easing (`cubic-bezier(0.16, 1, 0.3, 1)`).

---

## 2. Color Palette & Design Tokens

### Core Color Palette

| Token Name | Hex Code | Role / Usage |
| :--- | :--- | :--- |
| `--bg` | `#f7f7f5` | Warm paper base page background |
| `--surface` | `#ffffff` | Pure white container surfaces |
| `--surface-hover` | `#f0f0ed` | Hover background for interactive grid cells & cards |
| `--text` | `#171717` | Primary high-contrast text & primary button fill |
| `--text-hover` | `#333333` | Primary button hover / dark interactive hover |
| `--muted` | `#6b6b6b` | Secondary text, captions, descriptions, metadata |
| `--border` | `#ddddda` | Structural 1px hairline dividers and borders |
| `--orange` (Signature) | `#ff5e3a` | Primary brand accent, live dot, link underlines, "In Progress" |
| `--blue` | `#2563eb` | Secondary accent, "Idea / Concept" status badge |
| `--green` | `#59c36a` | "Live / Active" status badge dot |

### Raw CSS Variables Snippet

```css
:root {
  /* Surface & Backgrounds */
  --bg: #f7f7f5;
  --surface: #ffffff;
  --surface-hover: #f0f0ed;

  /* Typography & Dividers */
  --text: #171717;
  --text-hover: #333333;
  --muted: #6b6b6b;
  --border: #ddddda;

  /* Accent Colors */
  --accent: #171717;
  --orange: #ff5e3a;
  --blue: #2563eb;
  --green: #59c36a;

  /* Layout */
  --max-width: 1100px;
  --safe-left: env(safe-area-inset-left, 0px);
  --safe-right: env(safe-area-inset-right, 0px);
  --safe-bottom: env(safe-area-inset-bottom, 0px);
}
```

### Tailwind CSS Configuration (Optional)

If your target project uses Tailwind CSS:

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        kh: {
          bg: '#f7f7f5',
          surface: '#ffffff',
          'surface-hover': '#f0f0ed',
          text: '#171717',
          'text-hover': '#333333',
          muted: '#6b6b6b',
          border: '#ddddda',
          orange: '#ff5e3a',
          blue: '#2563eb',
          green: '#59c36a'
        }
      },
      fontFamily: {
        sans: ['Inter', '-apple-system', 'BlinkMacSystemFont', '"Segoe UI"', 'sans-serif'],
      },
      maxWidth: {
        kh: '1100px'
      }
    }
  }
}
```

---

## 3. Typography Rules & Scales

### Font Stack
```css
font-family: Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
```

### Typographic Hierarchy

1. **Massive Hero Display (`h1`)**
   - Size: `clamp(3.5rem, 9.5vw, 8.5rem)` (Mobile: `clamp(2.5rem, 11vw, 4.2rem)`)
   - Font Weight: `700` (Bold)
   - Line Height: `0.92` (Extremely tight, editorial)
   - Letter Spacing: `-0.075em` (Tightly tracked)
   - Overflow handling: `overflow-wrap: break-word; word-break: break-word;`

2. **Section Headings (`h2`)**
   - Size: `clamp(2.5rem, 6vw, 4.5rem)` (Mobile: `clamp(2rem, 7.5vw, 2.75rem)`)
   - Font Weight: `700`
   - Line Height: `1.0`
   - Letter Spacing: `-0.06em`

3. **Card / Item Titles (`h3`)**
   - Size: `1.8rem – 2.0rem` (Mobile: `1.35rem – 1.55rem`)
   - Font Weight: `700`
   - Letter Spacing: `-0.04em – -0.05em`
   - Margin: `55px 0 14px` inside grid cells

4. **Eyebrows / Overline Badges (`.eyebrow`)**
   - Size: `0.75rem – 0.78rem`
   - Text Transform: `uppercase`
   - Letter Spacing: `0.12em – 0.14em` (Expansive tracking)
   - Color: `var(--muted)`
   - Accompanied by: An 8px circular colored dot (`--orange`)

5. **Body Copy & Descriptions**
   - Hero Description: `1.15rem`, `var(--muted)`, `line-height: 1.6`, `max-width: 580px`
   - Section Intro: `0.9rem`, `var(--muted)`, `max-width: 300px`
   - General Paragraphs: `1.0rem – 1.05rem`, `var(--muted)`, `line-height: 1.6`
   - About Text: `1.45rem`, `var(--muted)`, `letter-spacing: -0.025em`, `line-height: 1.6`

---

## 4. Spacing, Layout & Grid Architecture

### Container Width
```css
.container {
  width: min(var(--max-width), calc(100% - 40px));
  margin: auto;
}
/* Mobile (<= 750px): calc(100% - 32px) */
/* Mobile small (<= 380px): calc(100% - 24px) */
```

### Section Cadence
- Desktop: `padding: 110px 0; border-top: 1px solid var(--border);`
- Hero Desktop: `padding: 100px 0; min-height: 680px;`
- Mobile: `padding: 55px 0;`

### Architectural Grid Cells (No Float / No Dropshadows)
Projects use a unified grid frame where borders share seamless 1px hairline lines:

```css
.project-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  border-top: 1px solid var(--border);
  border-left: 1px solid var(--border);
}

.project {
  min-height: 380px;
  padding: 38px;
  border-right: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  display: flex;
  flex-direction: column;
  transition: background 0.2s ease;
}

.project:hover {
  background: var(--surface-hover);
}

@media (max-width: 750px) {
  .project-grid {
    grid-template-columns: 1fr;
  }
}
```

---

## 5. UI Components Specification

### 5.1 Buttons

Buttons are sharp-cornered (no rounded border radius), confident, and rectangular:

```css
.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 13px 20px;
  border: 1px solid var(--text);
  font-size: 0.9rem;
  font-weight: 500;
  text-decoration: none;
  cursor: pointer;
  transition: 0.2s ease;
}

/* Primary Button: Solid Charcoal Inverted */
.button.primary {
  background: var(--text);
  color: var(--bg);
}
.button.primary:hover {
  background: var(--text-hover);
  border-color: var(--text-hover);
  color: var(--bg);
}

/* Secondary Button: Subtle Hairline Outline */
.button.secondary {
  border-color: var(--border);
  color: var(--muted);
  background: transparent;
}
.button.secondary:hover {
  border-color: var(--text);
  color: var(--text);
}
```

### 5.2 Eyebrow Header with Dot

```html
<div class="eyebrow">
  <span class="eyebrow-dot"></span>
  Independent project studio
</div>
```

```css
.eyebrow {
  display: flex;
  align-items: center;
  gap: 10px;
  color: var(--muted);
  font-size: 0.78rem;
  text-transform: uppercase;
  letter-spacing: 0.14em;
  margin-bottom: 30px;
}

.eyebrow-dot {
  width: 8px;
  height: 8px;
  background: var(--orange);
  border-radius: 50%;
  flex-shrink: 0;
}
```

### 5.3 Status Indicators

Status badges use a compact dot + uppercase micro-label (`0.72rem`, `letter-spacing: 0.1em`):

```html
<!-- Live Project -->
<span class="status live">Live</span>

<!-- In Progress -->
<span class="status progress">In progress</span>

<!-- Concept / Idea -->
<span class="status idea">Exploring</span>
```

```css
.status {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  color: var(--muted);
  font-size: 0.72rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  white-space: nowrap;
}

.status::before {
  content: "";
  width: 7px;
  height: 7px;
  border-radius: 50%;
}

.status.live::before {
  background: #59c36a;
}

.status.progress::before {
  background: var(--orange);
}

.status.idea::before {
  background: var(--blue);
}
```

### 5.4 Text & Outbound Links

External links and interactive text links feature an understated border underline that shifts to `--orange` on hover, paired with an outward arrow glyph `↗`:

```html
<a href="https://example.com" class="text-link" target="_blank" rel="noopener noreferrer">
  Visit website ↗
</a>
```

```css
.text-link {
  color: var(--text);
  border-bottom: 1px solid var(--border);
  padding-bottom: 3px;
  transition: border-color 0.15s ease, color 0.15s ease;
}

.text-link:hover {
  border-color: var(--orange);
  color: var(--orange);
}
```

### 5.5 Navbar & Header

- Fixed or flowing top bar with `82px` height (`66px` on mobile).
- Clean `1px solid var(--border)` bottom edge.
- Brand lockup: 60px height logo + bold title (`font-size: 1.1rem; letter-spacing: -0.04em; font-weight: 700;`).
- Nav links: muted grey, `0.9rem`, transitioning to `--text` on hover.

### 5.6 Footer

- Modest `28px 0` padding (`24px` on mobile).
- Border top hairline `1px solid var(--border)`.
- Left: Copyright statement (`© 2026 KumoHop`).
- Right: Studio sign-off (`Keep hopping.`).

---

## 6. Motion & Scroll Animations

KumoHop uses an editorial staggered scroll reveal powered by an `IntersectionObserver`:

```css
.fade-up {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s cubic-bezier(0.16, 1, 0.3, 1),
              transform 0.7s cubic-bezier(0.16, 1, 0.3, 1);
  will-change: opacity, transform;
}

.fade-up.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.delay-1 { transition-delay: 0.1s; }
.delay-2 { transition-delay: 0.2s; }
.delay-3 { transition-delay: 0.3s; }
```

### Intersection Observer Script
```javascript
document.addEventListener("DOMContentLoaded", () => {
  const observer = new IntersectionObserver((entries, obs) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add("is-visible");
        obs.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });

  document.querySelectorAll(".fade-up").forEach(el => observer.observe(el));
});
```

---

## 7. Tone of Voice & Copywriting

When writing copy for any KumoHop project:

1. **Terse, Punchy Headings**: Break thoughts into concise fragments (e.g., *"Apps. Games. Experiments."*, *"Let's build something."*).
2. **Understated & Pragmatic**: Avoid empty corporate buzzwords (e.g., "synergy", "paradigm-shifting"). Frame work honestly: *"Things that have escaped the idea stage"*, *"A mix of hardware, touch interfaces, and a lot of trial and error"*.
3. **Numbered Progression**: Use two-digit ordinal numbers (`01`, `02`, `03`) to catalog elements in grids and lists.
4. **Sign-off**: Grounded, optimistic sign-off: *"Keep hopping."*

---

## 8. Summary Checklist for Sister Projects

Before shipping a sister project or sub-page, verify against this checklist:

- [ ] Background is warm paper `#f7f7f5` (not `#ffffff` or cold gray).
- [ ] Text is dark charcoal `#171717` (not `#000000`).
- [ ] Borders are hairline `#ddddda` (1px solid).
- [ ] Headings have tight negative letter-spacing (`-0.04em` to `-0.075em`).
- [ ] Eyebrows use uppercase wide letter-spacing (`0.12em` to `0.14em`) with the signature orange accent dot (`#ff5e3a`).
- [ ] Buttons are crisp rectangles without rounded corners (`border-radius: 0`).
- [ ] Hover states use `#f0f0ed` for cells and `#ff5e3a` for link underlines.
- [ ] External links use the `↗` arrow indicator.
- [ ] Tap highlight is disabled on mobile (`-webkit-tap-highlight-color: transparent;`).
