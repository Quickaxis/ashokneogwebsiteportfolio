# Design System — Ashok Kumar Neog Personal Portfolio Website

This document outlines the core visual direction, color system, typography roles, and layout grid guidelines implemented for the **Ashok Kumar Neog** editorial personal portfolio.

---

## 1. Visual Direction & Identity

- **Style Tone**: Soft luxury editorial, founder-led personal brand.
- **Vibe**: Calm, spacious, elegant, and professional.
- **Industry Profile**: Premium real estate construction profile and regional land planner.
- **Structure**: Rounded canvas wrapper (`.site-shell`) representing an expensive editorial magazine layout, floating over an organic, textured, gradient-filled ivory background.

---

## 2. Color Palette

The custom color variables are defined in the CSS `:root` layer:

| Variable Name | Hex Code / Value | Role in Design System |
| :--- | :--- | :--- |
| `--canvas` | `#F6F1E7` | Outer page body background color |
| `--cream` | `#FFF7E8` | Light section backgrounds |
| `--cream-deep` | `#EFE2C8` | Subtle border accents, muted cream fills |
| `--card` | `#FFFDF8` | Container blocks, text grids, and white cards |
| `--forest` | `#1F332B` | Primary highlights, dark elements, brand accents |
| `--forest-deep`| `#14251F` | Deep solid background colors, main titles |
| `--sage` | `#C8D0B3` | Soft sage green canvas panels |
| `--sage-dark` | `#9EA981` | Accent outlines and border contrasts |
| `--gold` | `#B8A35B` | Luxury highlighting, subtitle tags, and active status |
| `--construction-gold` | `#C9A227` | Secondary highlighting |
| `--charcoal` | `#141414` | Body copy and primary content reading texts |
| `--muted` | `#4A524D` | Detailed paragraphs, card descriptions |
| `--soft-muted` | `#74796F` | Caption details and subtext elements |
| `--blue-soft` | `#A9C3D8` | Auxiliary split columns and modern gradients |
| `--line` | `rgba(31, 51, 43, 0.14)` | Elegant divider lines and borders |
| `--white-glass` | `rgba(255, 253, 248, 0.72)`| Sticky header and contact panel backgrounds |
| `--border-glass`| `rgba(255, 255, 255, 0.58)`| Glassmorphism card borders |

---

## 3. Typography Rules

The typography is loaded via Google Fonts using:
- **Playfair Display**: Bold, expressive serif for primary display headings.
- **Cormorant Garamond**: Italicized elegance for highlighted action terms inside headings.
- **Manrope**: Humanist sans-serif for nav links, labels, stats, button labels, and body paragraphs.

### CSS Declaration
```css
h1, h2, h3 {
  font-family: 'Playfair Display', serif;
  color: var(--charcoal);
  letter-spacing: -0.045em;
}

.italic {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-weight: 500;
  color: var(--forest);
}

body, nav, buttons, label {
  font-family: 'Manrope', sans-serif;
}
```

---

## 4. Spacing & Structure Layouts

- **Rounded Website Shell**: Centered wrapper wrapping the page content to feel like an expensive magazine issue.
  ```css
  .site-shell {
    max-width: 1180px;
    margin: 42px auto;
    border-radius: 34px;
    background: #FFFDF8;
    border: 8px solid rgba(255,255,255,0.85);
    box-shadow: 0 30px 90px rgba(31, 51, 43, 0.18);
  }
  ```
- **Section Padding**: Open, roomy layout padding configured via CSS clamp functions:
  ```css
  section {
    padding: clamp(70px, 9vw, 130px) clamp(22px, 5vw, 78px);
  }
  ```
- **Mobile Layout Transitions**:
  - Drops the outer margin on viewports under `768px` so the container fits the screen width cleanly.
  - Converts horizontal layouts and columns into unified vertical streams.
  - Shrinks headings proportionally (`clamp` values) to ensure headings don't cause horizontal overflow.

---

## 5. UI Elements & Components

### 1. Sticky Navigation Header
Height is set at `78px` with a backdrop blur and glass background to keep site links accessible:
```css
.header {
  height: 78px;
  background: rgba(255, 253, 248, 0.72);
  backdrop-filter: blur(14px);
}
```

### 2. Auto-Scrolling Marquee Strip
Used to build dynamic movement. Moves from right to left infinitely without slowing down performance.
```css
.marquee {
  height: 48px;
  overflow: hidden;
  white-space: nowrap;
}
```

### 3. Glassmorphic Panel Cards
Used for the contact submission details, statistics summary, and section accents.
```css
.glass-card {
  background: rgba(255, 253, 248, 0.68);
  backdrop-filter: blur(14px);
  border: 1px solid rgba(255, 255, 255, 0.58);
  box-shadow: 0 18px 55px rgba(31, 51, 43, 0.08);
}
```

### 4. Interactive Accordions
FAQ panels feature thin solid lines, rotate animations on their plus icons, and toggling heights using JS `scrollHeight` properties.

---

## 6. Imagery Guidelines

All image paths:
- `photos/ashok1.jpg` (Founder Portrait)
- `photos/ashok2.jpg` (Secondary Editorial Image)
- `photos/ashokwork.jpg` (On-site construction scene)
- `photos/toradevelopers.jpg` (Gated community land plotting)
- `photos/toraconstructions.jpg` (Modern residential architecture build)
- `photos/tora-logo.png` (Minimal modern logo)

- **Rules**:
  - Image blocks must feature clean, rounded corners (`border-radius: 20px` to `border-radius: 34px`).
  - Set `object-fit: cover` with custom focus alignments to ensure crop consistency.
  - Set `loading="lazy"` on blocks below the fold.
  - Fallback `.image-placeholder` elements are styled as rich radial-gradients in case of path mismatches.
