# Flexbox vs Grid — Pricing Layout Comparison

A frontend internship project that implements the **same modern SaaS pricing page** twice — once using **CSS Flexbox** and once using **CSS Grid** — to compare the two layout methods on identical content and design.

Built with **only HTML5 and CSS3**. No JavaScript, no Bootstrap, no Tailwind, no external CSS frameworks. The mobile-nav hamburger and the FAQ accordion are both done with pure CSS / native HTML5 (checkbox toggle and `<details>`) — zero JS.

> 📖 **Prefer reading in a browser?** Open [`README.html`](./README.html) and [`comparison.html`](./comparison.html) instead — same content, rendered with the site's own styling rather than raw Markdown.

---

## 🔗 Project Overview

- `index.html` — landing page that introduces the project and links to both versions
- `flexbox.html` — the pricing page laid out with **Flexbox only**
- `grid.html` — the pricing page laid out with **CSS Grid only**

Both pricing pages share **identical markup structure, copy, and visual design** (header, hero, 3 pricing cards, footer). The only difference is the CSS technique used to arrange the three pricing cards — so the comparison is a fair, apples-to-apples test.

---

## ✨ Features

- Sticky, responsive header with logo, nav links, and CTA buttons
- Pure-CSS mobile hamburger menu (checkbox toggle, no JS)
- Clean white background with a warm gold-metallic accent, Playfair Display + Poppins type pairing
- Gradient hero section with heading, subtitle, and dual CTAs
- Three pricing cards: **Basic**, **Pro** (highlighted), **Enterprise**
  - "Most Popular" badge and scale effect on the Pro plan
  - Hover lift animation, rounded corners, soft shadows on every card
- **FAQ accordion** built with native HTML5 `<details>`/`<summary>` — no JavaScript
- Fully responsive: 3 columns (desktop) → 2 columns (tablet) → 1 column (mobile)
- Footer with brand blurb, social links, and copyright
- CSS custom properties (variables) for colors, spacing, shadows, and radii
- Google Fonts (Poppins + Playfair Display) for clean, modern typography
- Semantic HTML5 (`header`, `nav`, `main`, `section`, `article`, `footer`, `details`)
- Accessible: skip link, visible focus states, `aria-label`s on icon-only links

---

## 📁 Folder Structure

```
Responsive-Layouts/
│
├── index.html            # Landing page linking to both versions
├── flexbox.html           # Pricing page — Flexbox layout
├── grid.html               # Pricing page — Grid layout
├── README.html             # Browser-readable version of this file
├── comparison.html         # Browser-readable version of comparison.md
├── css/
│   ├── common.css         # Shared: variables, header, hero, card content, footer
│   ├── flexbox.css        # Flexbox-only rules for the pricing card container
│   ├── grid.css            # Grid-only rules for the pricing card container
│   ├── index.css           # Page-specific styles for index.html only
│   └── docs.css             # Typography for README.html / comparison.html
├── assets/                 # Reserved for images/icons (currently unused — inline SVG icons used instead)
├── README.md
└── comparison.md
```

> **Note on `common.css`:** the task's suggested structure listed only `flexbox.css` and `grid.css`. A third shared file, `common.css`, was added to avoid duplicating the header, hero, footer, and card-content CSS in two places (per the "no duplicated code" requirement). `common.css` contains **zero rules for the pricing-card container** — that layout logic lives entirely in `flexbox.css` (`display: flex`) or `grid.css` (`display: grid`), so each version still stands on its own as a pure Flexbox / pure Grid implementation of the part being tested. `index.css` and `docs.css` were also added so `index.html` and the doc pages don't rely on inline `<style>` blocks.

---

## 🛠️ Technologies Used

- **HTML5** — semantic markup
- **CSS3** — Flexbox, Grid, custom properties, gradients, transitions, media queries
- **Google Fonts** — Poppins
- No JavaScript, no build tools, no frameworks

---

## ▶️ How to Run

No build step or server required.

1. Download / clone the `Responsive-Layouts` folder.
2. Open `index.html` directly in any modern browser (double-click it, or right-click → Open With → your browser).
3. From there, click **Flexbox Version** or **Grid Version** to view each pricing page, or open `flexbox.html` / `grid.html` directly.

Optional — serve locally instead of opening the file directly:

```bash
cd Responsive-Layouts
python3 -m http.server 8080
# then visit http://localhost:8080
```

---

## 🧪 Try It Responsively

Resize your browser window or open DevTools → Toggle Device Toolbar to see the pricing cards reflow:

| Breakpoint | Layout |
|---|---|
| Desktop (> 900px) | Basic · Pro · Enterprise in one row |
| Tablet (600px – 900px) | Basic + Pro in one row, Enterprise below |
| Mobile (< 600px) | Basic → Pro → Enterprise, stacked |


## 📄 Related Docs

See [`comparison.md`](./comparison.md) (or the browser-friendly [`comparison.html`](./comparison.html)) for a written breakdown of when to use Flexbox vs. Grid, and which was easier for this specific pricing layout.
