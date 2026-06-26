# Prompting Guide

How to apply the minimalist design system to new and existing pages.

---

## Starting a new page

Give the model this context up front:

> Use the minimalist-design skill. IBM Plex Mono, one font size (1rem), stone palette, opacity for hierarchy, dark/light via prefers-color-scheme. No shadows, no gradients, no large rounded corners.

Then describe the page content. The model should reach for `components.md` for paste-ready snippets.

---

## Auditing an existing page

Work through these steps in order:

### 1. Check the font

- Is `IBM Plex Mono` loaded from Google Fonts?
- Is it applied via `* { font-family: ... }` or a Tailwind base style?
- Are there any elements overriding the font (e.g., `font-sans` utility classes)?

Fix: add the `<link>` tag and the `*` override from `tailwind-config.md`.

### 2. Collapse the type scale

- Search for `text-xs`, `text-sm`, `text-lg`, `text-xl`, `text-2xl`, `text-3xl`, etc.
- Remove all of them. Size is `1rem` everywhere.
- Search for `font-bold` — replace with `font-medium`.
- Search for `font-semibold` — replace with `font-medium`.

### 3. Collapse the color palette

- Search for any non-stone color classes (`blue-`, `indigo-`, `purple-`, `pink-`, `green-`, etc.).
- Remove all of them unless they serve a semantic purpose (error = red, warning = amber).
- Replace color-based emphasis (`text-gray-400`) with opacity-based emphasis (`opacity-60`).

Correct pattern:
```html
<!-- before -->
<p class="text-gray-400">Secondary text</p>

<!-- after -->
<p class="opacity-60">Secondary text</p>
```

### 4. Fix dark mode coverage

Every `bg-*`, `text-*`, `border-*`, and `divide-*` class needs a `dark:` counterpart:

```html
<!-- before -->
<div class="bg-white text-gray-900 border-gray-200">

<!-- after -->
<div class="bg-stone-50 text-stone-950 dark:bg-stone-950 dark:text-stone-50 border-stone-200 dark:border-stone-800">
```

Opacity classes (`opacity-60`, `opacity-35`) work in both modes — no dark variant needed.

### 5. Remove decoration

Search for and remove:
- `shadow-*` (except `shadow-none`) — remove all decorative shadows
- `rounded-xl`, `rounded-2xl`, `rounded-3xl`, `rounded-full` on non-pill elements — replace with `rounded` or `rounded-md`
- `bg-gradient-*` — remove gradients
- `ring-*` — remove decorative rings (keep focus rings)
- `drop-shadow-*` — remove

### 6. Fix spacing

Ensure sections breathe:
- Section padding: `py-16` minimum, `py-24` for hero
- Between text blocks: `space-y-6` or `mb-6`
- Cards: `p-6` internal padding
- Nav: `h-14` height, `gap-8` between links

### 7. Constrain line length

Body prose should not exceed `max-w-3xl` (48rem). Wide layouts (data tables, dashboards) can use `max-w-5xl`.

```html
<main class="max-w-3xl mx-auto px-6 md:px-8">
```

### 8. Fix text alignment

- Body text: left-aligned (`text-left`, which is default)
- Center-aligned text only for single-line labels inside constrained containers (buttons, badges, nav items)
- Never center multi-line prose

---

## Pre-ship checklist

Before calling a page done, verify:

- [ ] IBM Plex Mono loads from Google Fonts
- [ ] `*` font override is in place
- [ ] No `text-sm`, `text-xs`, `text-lg`, `text-xl` etc. — size is uniform
- [ ] No `font-bold` or `font-semibold` — max is `font-medium`
- [ ] No non-stone colors (except red/amber for semantic states)
- [ ] Hierarchy expressed via `opacity-60`, `opacity-35` not color changes
- [ ] Every `bg-*` has a `dark:bg-*`
- [ ] Every `text-*` has a `dark:text-*`
- [ ] Every `border-*` has a `dark:border-*`
- [ ] No decorative `shadow-*`
- [ ] No `rounded-xl` or larger (use `rounded` or `rounded-md`)
- [ ] No gradients
- [ ] Content width constrained: `max-w-3xl` or `max-w-5xl`
- [ ] Section padding is at least `py-16`
- [ ] Body text is left-aligned
- [ ] Page tested in light mode
- [ ] Page tested in dark mode (toggle via browser devtools or system setting)

---

## Accent color decision guide

The system is monochrome by default. Add an accent only when the user explicitly asks or when a UI genuinely needs a focal point (e.g., a primary CTA on a marketing page).

Rules for accents:
1. One accent color per page, maximum
2. Use it on at most 1-2 elements (primary button, active nav item)
3. Pick a color from a single Tailwind scale (e.g., `sky-500`)
4. Always pair with a dark mode variant (`dark:sky-400`)
5. Never use the accent for text decoration (underlines, italics)

If in doubt, skip the accent. The default monochrome works.

---

## Common mistakes

| Mistake | Fix |
| --- | --- |
| Using `text-stone-400` for muted text | Use `opacity-60` instead |
| `font-bold` on headings | Use `font-medium` |
| `text-xl` or larger for headings | Remove — all text is `1rem` |
| `rounded-2xl` on cards | Use `rounded` (4px) or remove entirely |
| Forgetting `dark:` on `border-*` | Add `dark:border-stone-800` |
| Multiple font sizes in one component | Flatten to `1rem` for all |
| Using blue links | Use `opacity-60` + `hover:opacity-100` |
| Shadow on cards | Remove — use border instead |
