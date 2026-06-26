# Design System Reference

## CSS tokens

```css
:root {
  --font: 'IBM Plex Mono', ui-monospace, 'Cascadia Code', 'Fira Code', 'Courier New', monospace;
  --font-size: 1rem;
  --line-height: 1.6;
  --bg:   #E7E5E4;   /* stone-200 */
  --text: #44403C;   /* stone-700 */
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg:   #44403C;  /* stone-700 */
    --text: #E7E5E4;  /* stone-200 */
  }
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html {
  font-family: var(--font);
  font-size: var(--font-size);
  font-weight: 400;
  font-style: normal;
  line-height: var(--line-height);
  color: var(--text);
  background: var(--bg);
}
```

Two colors only. No opacity variants, no surface tints, no border palette.

## Stone color values

| Token     | Hex       | Role                 |
| --------- | --------- | -------------------- |
| stone-200 | #E7E5E4   | Light bg / Dark text |
| stone-700 | #44403C   | Light text / Dark bg |

Contrast: 8.18:1 (WCAG AAA). That is the entire palette. No intermediate steps.

## Dark mode

Pure CSS, no JavaScript:

```css
@media (prefers-color-scheme: dark) {
  :root { --bg: #0C0A09; --text: #FAFAF9; }
}
```

In Tailwind:
```html
<body class="bg-stone-50 text-stone-950 dark:bg-stone-950 dark:text-stone-50">
```

Every element inherits color from `html`. Nothing needs explicit color assignment except the body.

## Typography

One variant: 400 normal. Do not load or use 500 medium or italic.

```css
font-family: 'IBM Plex Mono', ui-monospace, 'Cascadia Code', 'Fira Code', monospace;
font-size: 1rem;
font-weight: 400;
font-style: normal;
line-height: 1.6;
```

Google Fonts — load only what is used:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono&display=swap" rel="stylesheet">
```

## Structure

Hierarchy comes from ASCII conventions:

```
SECTION HEADING

Body paragraph. One blank line between paragraphs.

  Indented text suggests subordination.

- List item
- List item

key     description text here
key     description text here

---
```

- Section headings: ALL-CAPS, followed by a blank line. No special styling.
- Dividers: `<hr>` rendered as a plain horizontal line, or a literal `---` in pre-formatted blocks.
- Lists: standard `<ul>` or `<ol>`, no custom markers needed.
- Key/value: `<dl>` or a two-column layout with consistent left-alignment.

## Layout

```css
body {
  max-width: 640px;
  margin: 0 auto;
  padding: 3rem 1.5rem 6rem;
}
```

Single column only. No grid, no multi-column layout. Content width is the only structural constraint.

## Spacing

| Use                        | Value      |
| -------------------------- | ---------- |
| Between paragraphs         | 1rem       |
| Between sections           | 3rem       |
| Between list items         | 0.25rem    |
| Section top padding        | 3rem       |
| Body bottom padding        | 6rem       |

## Palette swap

Replace `stone` with any single-hue Tailwind scale:

| Scale   | Character              |
| ------- | ---------------------- |
| stone   | Warm gray (default)    |
| zinc    | Slightly cool gray     |
| neutral | Perfectly neutral      |
| slate   | Blue-tinted gray       |
| gray    | Standard gray          |

Never mix scales. Find/replace `stone` → chosen scale throughout.
