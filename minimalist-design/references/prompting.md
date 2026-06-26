# Prompting Guide

How to apply the minimalist design system to new and existing pages.

---

## Starting a new page

Give the model this context up front:

> Use the minimalist-design skill. IBM Plex Mono, 1rem, 400 weight, no opacity, no italic, stone palette, prefers-color-scheme dark mode. No decoration. Structure from spacing and ALL-CAPS section headings only.

Then describe the content. The model should reach for `components.md` for paste-ready patterns.

---

## Auditing an existing page

Work through these steps in order.

### 1. Check the font

- Is IBM Plex Mono loaded from Google Fonts (400 only)?
- Is it applied globally via `html { font-family: ... }`?
- Are there any overrides elsewhere (`font-sans`, `font-serif`)?

Fix: load only `IBM+Plex+Mono` (no weight or style params) and set `* { font-family: inherit }`.

### 2. Collapse the type scale

Search for and remove:
- `text-xs`, `text-sm`, `text-lg`, `text-xl`, `text-2xl`, etc.
- `font-bold`, `font-semibold`, `font-medium`
- `italic`, `font-style: italic`
- `letter-spacing`, `text-transform` (except ALL-CAPS section labels)

Everything becomes `font-size: 1rem`, `font-weight: 400`, `font-style: normal`.

### 3. Remove opacity

Search for and remove:
- `opacity-*` on any element
- `text-stone-400`, `text-stone-500`, `text-stone-600` — muted color variants
- `text-gray-400`, `text-zinc-500`, or any lighter-shade text color
- `placeholder:opacity-*`

Replace structural opacity with spacing. If something was muted to signal it was secondary, consider whether it needs to be on the page at all. If it does, leave it at full brightness.

### 4. Remove decoration

Search for and remove:
- `shadow-*` (all decorative shadows)
- `rounded-xl`, `rounded-2xl`, `rounded-full` — remove or reduce to `rounded` at most
- `bg-gradient-*`, `from-*`, `to-*`
- `ring-*` (decorative rings, keep focus rings)
- `border` classes used decoratively — keep only functional borders (inputs, `<hr>`, tables)
- `bg-stone-100`, `bg-stone-900`, `bg-white` — surface tints that aren't the base bg

### 5. Fix dark mode

Only two tokens needed:
```css
:root { --bg: #FAFAF9; --text: #0C0A09; }
@media (prefers-color-scheme: dark) { :root { --bg: #0C0A09; --text: #FAFAF9; } }
```

In Tailwind: every `bg-stone-50` needs `dark:bg-stone-950` and every `text-stone-950` needs `dark:text-stone-50`. Nothing else.

### 6. Replace visual hierarchy with spatial hierarchy

Old pattern (typographic):
```html
<h2 class="text-xl font-semibold text-stone-900">Section</h2>
<p class="text-stone-500">Description here.</p>
```

New pattern (spatial):
```html
<p>SECTION</p>
<p style="margin-top: 1rem">Description here.</p>
```

Use blank lines (margin) and ALL-CAPS labels to create hierarchy, not font variation.

---

## Pre-ship checklist

Before calling a page done:

- [ ] IBM Plex Mono loads from Google Fonts (400 only)
- [ ] No `font-weight` other than 400
- [ ] No `font-style: italic`
- [ ] No opacity on any element
- [ ] No muted color variants (`text-stone-400`, etc.)
- [ ] No `text-sm`, `text-xs`, `text-lg`, `text-xl`, etc.
- [ ] Only two background colors: stone-50 (light) and stone-950 (dark)
- [ ] No surface tints, no card backgrounds different from page background
- [ ] No decorative shadows or gradients
- [ ] No decorative borders (keep functional ones: inputs, hr, tables)
- [ ] Section headings are ALL-CAPS plain text, no special styling
- [ ] Content width constrained (640px or similar)
- [ ] Page tested in light mode
- [ ] Page tested in dark mode

---

## Common mistakes

| Mistake | Fix |
| --- | --- |
| `opacity-70` on secondary text | Remove. Everything is full brightness. |
| `font-medium` on headings | Remove. 400 weight everywhere. |
| `text-stone-500` for muted text | Remove. Use full-brightness text or cut the content. |
| `bg-stone-100` on cards | Remove. No surface tints. |
| `italic` for captions | Remove. No italic. |
| Two-level heading hierarchy | Use ALL-CAPS labels + spacing instead. |
| `border` on cards | Remove unless it's a functional input border or `<hr>`. |
