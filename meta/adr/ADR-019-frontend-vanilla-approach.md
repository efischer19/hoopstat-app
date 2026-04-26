---
title: "ADR-019: Frontend Framework Selection — Vanilla HTML/CSS/JavaScript Approach"
status: "Accepted"
date: "2025-01-21"
tags:
  - "frontend"
  - "architecture"
  - "simplicity"
---

## Context

* **Problem:** The Hoopstat Haus project requires a simple static frontend application foundation that provides a data browser for basketball statistics without authentication complexity. The frontend needs to be simple and maintainable with minimal dependencies, mobile-responsive, stateless without client-side session management, ready for API gateway integration, and aligned with the project's simplicity-first development philosophy.

## Decision

We will implement the frontend using vanilla HTML5, CSS, and minimal JavaScript without a frontend framework. This approach follows the "Static Over Dynamic" and "YAGNI" principles from our development philosophy.

### Key Technical Decisions

1. **No Frontend Framework**: Use vanilla HTML/CSS/JavaScript for maximum simplicity and minimal dependencies
2. **Static File Structure**: Organize as static files that can be hosted on any web server or CDN
3. **Progressive Enhancement**: Core functionality works without JavaScript, enhanced features layer on top
4. **Mobile-First Design**: CSS designed with mobile-first responsive approach
5. **Minimal JavaScript**: Only essential JavaScript for form handling and future API integration

### File Structure

```text
src/
├── index.html              # Main application entry point
├── health.html             # Pipeline health dashboard
├── assets/
│   ├── styles.css         # CSS styles with mobile-first design
│   └── favicon.svg        # SVG favicon
├── scripts/
│   ├── app.js             # JavaScript for data browsing and artifact fetching
│   └── health.js          # JavaScript for health dashboard rendering
└── README.md              # Frontend-specific documentation
```

## Considered Options

1. **Vanilla HTML/CSS/JS (Chosen):** No framework, no build process, no runtime dependencies.
    * *Pros:* Zero build process complexity; no framework dependencies to maintain; easy to host on any static hosting platform; simple debugging and maintenance; fast loading times; maximum browser compatibility.
    * *Cons:* May need to reconsider for complex UI features later; no built-in state management patterns; manual DOM manipulation required; no component reusability patterns.

2. **React/Vue/Svelte SPA:** Modern component-based framework with build tooling.
    * *Pros:* Component reuse; declarative UI; large ecosystem.
    * *Cons:* Requires build process; adds framework dependency; overkill for a data browser; conflicts with static-first philosophy.

3. **Web Components (Custom Elements):** Native browser component model without a framework.
    * *Pros:* Native browser support; encapsulation via Shadow DOM; reusable components.
    * *Cons:* More boilerplate than vanilla; polyfills may be needed for older browsers; less mature tooling.

## Consequences

* **Positive:** This approach eliminates framework complexity and dependencies. Simple HTML/CSS/JS is readable by any web developer. No build process or dynamic rendering complexity. We implement only what's needed for the MVP functionality.
* **Negative:** If the application grows in complexity, we may need to introduce web components or migrate to a framework. Manual DOM manipulation is required for dynamic content.
* **Future Implications:** If the application grows, we can add a build process for optimization, introduce web components for reusability, migrate to a framework while keeping the same static hosting model, or add TypeScript compilation for type safety. This decision provides a solid foundation that can evolve without breaking the core simplicity principle.
