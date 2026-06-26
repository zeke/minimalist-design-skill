---
name: minimalist-design
description: >
  Apply a minimalist monospace design system using IBM Plex Mono at a single
  size with ASCII-style structure. No opacity, no weight variation, no type
  scale. Hierarchy comes from spacing, indentation, and ASCII punctuation.
  Use this skill when the user asks for a minimal, minimalist, simple, clean,
  stark, bare, understated, monospace, ASCII, terminal, typewriter, or
  typographic design. Also invoke when the user says things like "keep it
  simple", "nothing fancy", "just make it clean", "strip it back", "plain
  design", "no frills", "utilitarian", "raw", "text-first", or "developer
  aesthetic". Use for documentation, dev tools, CLIs, portfolios, landing
  pages, or any interface where clarity and restraint are valued over
  decoration.
license: MIT
metadata:
  author: zeke
  version: "2.0"
---

## Core principles

1. **One font, one size, one weight.** IBM Plex Mono at 1rem / 400 weight everywhere. No type scale, no bold, no italic.
2. **Opacity sparingly.** Every character is the same brightness by default. Use opacity only where it genuinely helps — faint dividers, unselectable prompt characters. Not for text hierarchy.
3. **Stone by default.** `stone-950` on `stone-50` in light mode, reversed in dark. Honor `prefers-color-scheme` with no JavaScript.
4. **No decoration.** No shadows, gradients, rounded corners, or borders unless functionally necessary. Whitespace is the structure.
5. **Swappable palette.** Substitute any single-hue Tailwind scale (slate, zinc, neutral, gray). Never mix scales.

## Typography

```css
font-family: 'IBM Plex Mono', ui-monospace, 'Cascadia Code', 'Fira Code', 'Courier New', monospace;
font-size: 1rem;    /* 16px — the only size */
font-weight: 400;   /* the only weight */
line-height: 1.6;
font-style: normal; /* no italic */
```

Load from Google Fonts:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono&display=swap" rel="stylesheet">
```

Only one variant is needed: 400 normal. Do not load 500 or italic.

## Structure

Hierarchy comes from ASCII conventions, not typographic variation:

```
Page title          <- first line, nothing special
Tagline             <- second line, nothing special

---

SECTION HEADING     <- all-caps, preceded by blank line

Body text flows here as paragraphs separated by blank lines.

  Indented content suggests subordination or a code example.

- bullet list item
- another item

key    value         <- two-space-aligned columns for key/value pairs
```

Section headings are ALL-CAPS text followed by a blank line. No `<h2>` styling, no border, no color. Visually distinct through convention, not CSS.

## Color

Light mode:
```
background: #FAFAF9   (stone-50)
text:       #0C0A09   (stone-950)
```

Dark mode (`prefers-color-scheme: dark`):
```
background: #0C0A09   (stone-950)
text:       #FAFAF9   (stone-50)
```

Two colors only. No surface tints, no border colors, no opacity variants.

## Layout

```css
max-width: 640px;
margin: 0 auto;
padding: 3rem 1.5rem 6rem;
```

Single column. Left-aligned. No grid, no flexbox for layout (flexbox is fine for inline alignment). Line length naturally constrained by `max-width`.

## What NOT to do

- No `font-weight` other than 400
- No `font-style: italic`
- No `opacity` for text hierarchy — use it only for decoration (dividers, prompt characters, etc.)
- Links use underlines (`text-decoration: underline`), not color changes
- No `text-xl`, `text-2xl`, etc.
- No `font-bold`, `font-medium`, `font-semibold`
- No `text-gray-400`, `text-stone-500`, or any muted color variant
- No `shadow-*`, `rounded-*`, or `gradient-*`
- No background colors other than the base bg token
- No borders as decoration — only as functional separators (e.g., `<hr>`)

## References

- [design-system.md](references/design-system.md) — CSS tokens, color values, dark mode
- [components.md](references/components.md) — paste-ready HTML patterns
- [tailwind-config.md](references/tailwind-config.md) — Tailwind v3/v4 config
- [prompting.md](references/prompting.md) — audit checklist for existing pages
