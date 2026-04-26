# `src/` — Frontend Source Files

This directory contains all frontend source files for the Hoopstat Haus
analytics dashboard. No build step is required — serve these files with any
static web server to preview.

## File Structure

```text
src/
├── index.html          # Main analytics dashboard (data browser)
├── health.html         # Pipeline health dashboard
├── assets/
│   ├── styles.css      # Mobile-first responsive CSS (shared across pages)
│   └── favicon.svg     # SVG favicon (basketball logo)
├── scripts/
│   ├── app.js          # Data browser JS (fetch artifacts, render charts)
│   └── health.js       # Health dashboard JS (pipeline status, 7-day chart)
└── README.md           # This file — documents structure and conventions
```

## Architecture

The frontend follows a **vanilla HTML/CSS/JavaScript approach** as documented
in ADR-019. Charts are rendered with Chart.js loaded via CDN (ADR-036).

- **Static-First**: No build process required, can be hosted on any web server
- **Progressive Enhancement**: Core functionality works without JavaScript
- **Minimal Dependencies**: Chart.js (via CDN) is the only external library
- **Gold Artifacts**: Fetches JSON artifacts directly from CloudFront

## Local Development

Serve the files with any static web server:

```bash
cd src
python -m http.server 8080
```

Then open <http://localhost:8080> for the main dashboard or
<http://localhost:8080/health.html> for the pipeline health dashboard.

### Configuration

The data browser is configured via the `CONFIG` object in `scripts/app.js`:

```javascript
const CONFIG = {
  GOLD_BASE_URL: 'https://CLOUDFRONT_DOMAIN_PLACEHOLDER',
  REQUEST_TIMEOUT_MS: 10000,
};
```

Replace `CLOUDFRONT_DOMAIN_PLACEHOLDER` with the actual CloudFront domain.

## Conventions

### HTML

- **Semantic elements** — Use `<header>`, `<main>`, `<nav>`, `<section>`,
  `<footer>` instead of generic `<div>` elements.
- **Accessibility attributes** — Every page must include:
  - `lang` attribute on `<html>`
  - Viewport `<meta>` tag for responsive design
  - ARIA labels and roles for interactive elements
  - Proper heading hierarchy (one `<h1>`, then `<h2>`, `<h3>`, etc.)
- **Progressive enhancement** — Core content is accessible without JavaScript.

### CSS (`assets/styles.css`)

- **CSS custom properties** for all colors, fonts, and spacing values.
- **WCAG 2.1 AA color contrast** — All text/background combinations meet the
  4.5:1 minimum ratio for normal text.
- **Mobile-first** — Base styles target small screens; use `@media` queries for
  larger breakpoints.
- **No frameworks** — Vanilla CSS only. Add preprocessors or frameworks as
  needed via an ADR.

### JavaScript

- **Vanilla ES6+** — No dependencies by default (Chart.js via CDN is the
  exception, per ADR-036).
- **Progressive enhancement** — The page works without JavaScript; scripts add
  interactive enhancements.
- **Accessibility** — Interactive elements include proper ARIA attributes and
  keyboard support.
- **Chart.js guard** — All chart code checks `typeof Chart !== 'undefined'`
  before using Chart.js, so pages degrade gracefully if the CDN is unavailable.

## Accessibility Testing

### Browser DevTools (Quick Check)

1. Open `src/index.html` in Chrome, Firefox, or Edge.
2. Open DevTools → **Lighthouse** (Chrome) or **Accessibility** panel.
3. Run an accessibility audit and review the results.

### Keyboard Navigation Test

1. Press `Tab` to move through all interactive elements.
2. Confirm all buttons and links are reachable and operable with
   `Enter` or `Space`.
3. Check that focus indicators are clearly visible.

### Color Contrast Verification

Use one of these tools to verify WCAG 2.1 AA compliance (4.5:1 for normal text,
3:1 for large text):

- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Colour Contrast Analyser (desktop app)](https://www.tpgi.com/color-contrast-checker/)
- Chrome DevTools → Elements → Computed → contrast ratio display

## Resources

- [WCAG 2.1 Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/)
- [MDN Accessibility Guide](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
- [The A11Y Project Checklist](https://www.a11yproject.com/checklist/)
- [HTML5 Semantic Elements Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
