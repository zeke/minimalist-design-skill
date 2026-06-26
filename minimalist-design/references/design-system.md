# Design System Reference

## CSS custom properties

```css
:root {
  /* Font */
  --font-mono: 'IBM Plex Mono', ui-monospace, 'Cascadia Code', 'Fira Code', 'Courier New', monospace;
  --font-size-base: 1rem;       /* 16px — the only size */
  --line-height: 1.6;

  /* Stone light */
  --color-bg:      #FAFAF9;   /* stone-50  */
  --color-surface: #F5F5F4;   /* stone-100 */
  --color-border:  #E7E5E4;   /* stone-200 */
  --color-text:    #0C0A09;   /* stone-950 */
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-bg:      #0C0A09;  /* stone-950 */
    --color-surface: #1C1917;  /* stone-900 */
    --color-border:  #292524;  /* stone-800 */
    --color-text:    #FAFAF9;  /* stone-50  */
  }
}

* {
  font-family: var(--font-mono);
  font-size: var(--font-size-base);
  line-height: var(--line-height);
}

body {
  background-color: var(--color-bg);
  color: var(--color-text);
}
```

## Stone color scale

| Token      | Hex       | Light mode role        | Dark mode role         |
| ---------- | --------- | ---------------------- | ---------------------- |
| stone-50   | #FAFAF9   | Background             | Primary text           |
| stone-100  | #F5F5F4   | Surface / card bg      | —                      |
| stone-200  | #E7E5E4   | Border                 | —                      |
| stone-300  | #D6D3D1   | Subtle border          | —                      |
| stone-400  | #A8A29E   | Placeholder text       | Tertiary text          |
| stone-500  | #78716C   | Muted text             | Secondary text         |
| stone-600  | #57534E   | —                      | Subtle border          |
| stone-700  | #44403C   | —                      | Border                 |
| stone-800  | #292524   | —                      | Border (strong)        |
| stone-900  | #1C1917   | —                      | Surface / card bg      |
| stone-950  | #0C0A09   | Primary text           | Background             |

## Opacity ladder

Opacity is the only tool for text hierarchy. Never change the stone hue to de-emphasize text.

| Role             | CSS                       | Tailwind                     |
| ---------------- | ------------------------- | ---------------------------- |
| Primary          | `opacity: 1`              | (no class needed)            |
| Secondary        | `opacity: 0.6`            | `opacity-60`                 |
| Tertiary / hint  | `opacity: 0.35`           | `opacity-35`                 |
| Disabled         | `opacity: 0.25`           | `opacity-25`                 |

Example — a card with a title, subtitle, and hint:
```html
<div>
  <p>Primary label</p>
  <p class="opacity-60">Secondary description</p>
  <p class="opacity-35">Optional hint text</p>
</div>
```

## Typography

```css
/* All text: same size, same font */
font-family: 'IBM Plex Mono', ui-monospace, 'Cascadia Code', 'Fira Code', monospace;
font-size: 1rem;
line-height: 1.6;

/* Headings: medium weight only */
font-weight: 500;

/* Body: normal weight */
font-weight: 400;

/* Asides / captions: italic */
font-style: italic;
```

Weight is the only typographic differentiator:

| Role              | Weight        | Tailwind         |
| ----------------- | ------------- | ---------------- |
| Headings          | 500 (medium)  | `font-medium`    |
| Body / UI labels  | 400 (normal)  | `font-normal`    |
| Captions / asides | 400 italic    | `italic`         |

No `font-bold`, no `text-xl`, no `text-sm`. Size is fixed at `1rem`.

## Spacing

Vertical rhythm uses a consistent `0.5rem` (8px) base unit:

| Scale | Value  | Tailwind  | Use                          |
| ----- | ------ | --------- | ---------------------------- |
| 1     | 4px    | `gap-1`   | Tight inline gaps            |
| 2     | 8px    | `gap-2`   | Within a component           |
| 4     | 16px   | `gap-4`   | Between components           |
| 6     | 24px   | `gap-6`   | Between sections (small)     |
| 8     | 32px   | `gap-8`   | Between sections (normal)    |
| 16    | 64px   | `py-16`   | Section padding              |
| 24    | 96px   | `py-24`   | Hero / large section padding |

## Layout constraints

```
Max content width (prose):  max-w-3xl   (48rem / 768px)
Max content width (wide):   max-w-5xl   (64rem / 1024px)
Horizontal padding:         px-6 (mobile) → px-8 (md+)
```

Tailwind:
```html
<main class="max-w-3xl mx-auto px-6 md:px-8 py-16">
```

## Dark mode implementation

Pure CSS, no JavaScript:

```css
@media (prefers-color-scheme: dark) {
  /* Override color tokens here */
}
```

In Tailwind, use the `dark:` variant with `@media` strategy (default in v3):
```html
<body class="bg-stone-50 text-stone-950 dark:bg-stone-950 dark:text-stone-50">
```

Every color class needs a `dark:` counterpart. Checklist:
- `bg-*` → `dark:bg-*`
- `text-*` → `dark:text-*`
- `border-*` → `dark:border-*`
- `divide-*` → `dark:divide-*`

Opacity-based text (e.g. `opacity-60`) works in both modes automatically — no dark variant needed.

## Borders

Use borders sparingly — only when they separate genuinely distinct content:

```html
<!-- Subtle divider -->
<hr class="border-stone-200 dark:border-stone-800">

<!-- Card outline -->
<div class="border border-stone-200 dark:border-stone-800">

<!-- Input -->
<input class="border border-stone-300 dark:border-stone-700 ...">
```

No decorative borders. No double borders. No rounded corners beyond `rounded` (4px).

## Swapping the palette

Replace `stone` with any single-hue Tailwind scale:

| Option    | Character                        |
| --------- | -------------------------------- |
| `stone`   | Warm, slightly brown (default)   |
| `zinc`    | Neutral, slightly blue-gray      |
| `neutral` | Perfectly neutral gray           |
| `slate`   | Cool, blue-tinted gray           |
| `gray`    | Standard gray                    |

Do a global find-and-replace: `stone` → your chosen scale. Never mix scales.
