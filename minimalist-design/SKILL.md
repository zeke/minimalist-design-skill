---
name: minimalist-design
description: >
  Apply a minimalist monospace design system using IBM Plex Mono, a single
  font size, monochromatic stone palette, and opacity-based text hierarchy.
  Use this skill when the user asks for a minimal, minimalist, simple, clean,
  stark, bare, understated, monospace, or typographic design. Also invoke when
  the user says things like "keep it simple", "nothing fancy", "just make it
  clean", "strip it back", "plain design", "no frills", "utilitarian", "raw",
  "text-first", or "developer aesthetic". Use for dashboards, documentation
  sites, dev tools, CLIs, portfolios, landing pages, or any interface where
  clarity and restraint are valued over decoration.
license: MIT
metadata:
  author: zeke
  version: "1.0"
---

## Core principles

1. **One font, one size.** IBM Plex Mono everywhere, `1rem` (16px) throughout. No type scale. Size conveys nothing; weight and opacity do.
2. **Opacity creates hierarchy.** Primary text at full opacity, secondary at 60%, tertiary/disabled at 35%. Never change the hue to de-emphasize.
3. **Stone by default.** Use Tailwind's `stone` palette. Light mode: `stone-950` text on `stone-50` background. Dark mode: `stone-50` text on `stone-950` background. Honor `prefers-color-scheme` with no JavaScript.
4. **No decoration.** No shadows, no gradients, no rounded corners unless functional. Borders only when they carry meaning. Whitespace is the structure.
5. **Swappable palette.** The user can substitute any single-hue Tailwind scale (slate, zinc, neutral, gray) for stone. Keep it monochromatic — no mixing scales.

## Typography

```css
font-family: 'IBM Plex Mono', ui-monospace, 'Cascadia Code', 'Fira Code', 'Courier New', monospace;
font-size: 1rem;      /* 16px — the only size */
line-height: 1.6;     /* comfortable reading */
font-weight: 400;     /* normal body */
```

Load from Google Fonts:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet">
```

Weight usage:
- `font-normal` (400) — body text, labels, most UI
- `font-medium` (500) — headings, emphasis, interactive labels
- `font-normal italic` — captions, asides, inline annotations

## Opacity ladder

| Role             | Tailwind class  | Opacity |
| ---------------- | --------------- | ------- |
| Primary text     | (none / default) | 100%   |
| Secondary text   | `opacity-60`    | 60%     |
| Tertiary / hint  | `opacity-35`    | 35%     |
| Disabled         | `opacity-25`    | 25%     |

Apply to text only. Never apply opacity to interactive elements in a way that hides their state.

## Color

Light mode (default):
```
background: stone-50   (#FAFAF9)
surface:    stone-100  (#F5F5F4)
border:     stone-200  (#E7E5E4)
text:       stone-950  (#0C0A09)
```

Dark mode (`prefers-color-scheme: dark`):
```
background: stone-950  (#0C0A09)
surface:    stone-900  (#1C1917)
border:     stone-800  (#292524)
text:       stone-50   (#FAFAF9)
```

No accent color by default. If the user requests one, use a single hue at `stone-900` / `stone-100` equivalent weight — or pick a contrast color from a separate Tailwind scale (e.g. `sky-500`), used sparingly.

## Layout

- Max content width: `max-w-3xl` (48rem) for prose, `max-w-5xl` for wide layouts
- Padding: `px-6` on mobile, `px-8` on md+
- Vertical rhythm: `space-y-6` between sections, `py-16` for section padding
- No multi-column layouts unless the content is genuinely tabular
- Align everything to a left edge — centered text only for single-line labels

## What NOT to do

- No `text-2xl`, `text-3xl`, etc. — size is fixed at `1rem`
- No `font-bold` — use `font-medium` at most
- No color other than the stone scale (unless user explicitly requests an accent)
- No `rounded-xl`, `rounded-2xl` — use `rounded` (4px) or `rounded-md` (6px) at most, only for inputs and buttons
- No `shadow-lg`, `shadow-xl`, or decorative shadows
- No gradients
- No background images or patterns

## References

Load these on demand for more detail:

- [design-system.md](references/design-system.md) — CSS custom properties, full token table, dark mode implementation
- [components.md](references/components.md) — paste-ready Tailwind HTML for nav, hero, buttons, cards, forms, tables, code blocks
- [tailwind-config.md](references/tailwind-config.md) — Tailwind v3 config and v4 `@theme` block
- [prompting.md](references/prompting.md) — audit checklist for applying this system to existing pages
