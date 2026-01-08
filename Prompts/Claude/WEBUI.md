---
publish:
title: WEBUI.md
type:
status:
date: 2026-01-08
tags:
---

# WEBUI.md

Guidance for frontend and UI work in this workspace.  
Project-specific instructions (PROJECT.md) take precedence.

## Frontend Philosophy

- Prefer **server-rendered HTML** as the default.
- Treat JavaScript as a progressive enhancement, not a requirement.
- Favor boring, predictable UI behavior over clever client-side abstractions.
- Avoid introducing frontend complexity unless it materially improves usability.
- Design and implement UI **mobile-first**, then enhance for larger screens.

## HTML and Semantics

- Use semantic HTML elements (`nav`, `main`, `article`, `section`, etc.).
- Prefer accessibility-friendly markup by default.
- Do not rely on JavaScript to provide core navigation or content visibility.

## Mobile-First Design

- Assume mobile and touch-based devices as the primary interaction model.
- Design layouts for small screens first, then progressively enhance for larger viewports.
- Avoid hiding critical functionality behind hover-only or desktop-specific interactions.
- Ensure text, buttons, and controls are usable without precise pointing devices.

## CSS

- Use **TailwindCSS** for styling.
- Prefer utility classes over custom CSS.
- Extract reusable UI patterns into partials/components before reaching for shared CSS.
- Avoid global CSS overrides unless absolutely necessary.
- Do not introduce CSS frameworks beyond Tailwind.
- Prefer Tailwind’s mobile-first responsive utilities; add breakpoints only when needed.

## JavaScript

- Prefer **Turbo** for navigation and partial page updates.
- Use **Stimulus** for small, focused behavior attached to existing HTML.
- Keep Stimulus controllers minimal and declarative.
- Avoid client-side state management unless explicitly required.

## Hotwire Usage

- Turbo Frames and Turbo Streams are preferred over custom JS solutions.
- Use Turbo to reduce page reloads, not to simulate an SPA.
- If behavior becomes complex, reconsider the UI design before adding JS.

## Accessibility

- UI changes should not break keyboard navigation.
- Interactive elements must remain accessible without a mouse.
- Prefer native HTML controls over custom widgets.

## Performance

- Minimize JavaScript payload and execution.
- Avoid loading JS on pages that do not require it.
- Prefer CSS and HTML solutions over JS-driven layout or behavior.

## Anti-Patterns to Avoid

- Inline JavaScript in views.
- Page-specific one-off CSS hacks.
- Adding a JS framework “because it’s easier.”
- Hiding application logic inside frontend behavior.
