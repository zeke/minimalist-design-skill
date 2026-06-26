# Tailwind Config Reference

## Google Fonts link tag

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet">
```

## Tailwind v3 config

```js
// tailwind.config.js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./src/**/*.{html,js,ts,jsx,tsx}'],
  darkMode: 'media',
  theme: {
    extend: {
      fontFamily: {
        mono: [
          'IBM Plex Mono',
          'ui-monospace',
          'Cascadia Code',
          'Fira Code',
          'Courier New',
          'monospace',
        ],
        // Override sans so font-sans also uses mono
        sans: [
          'IBM Plex Mono',
          'ui-monospace',
          'Cascadia Code',
          'Fira Code',
          'Courier New',
          'monospace',
        ],
      },
      fontSize: {
        // Lock all text to 1rem — no scale
        'base': ['1rem', { lineHeight: '1.6' }],
      },
    },
  },
  plugins: [],
}
```

## Tailwind v4 `@theme` block

```css
/* app.css */
@import "tailwindcss";

@theme {
  --font-family-mono:
    'IBM Plex Mono',
    ui-monospace,
    'Cascadia Code',
    'Fira Code',
    'Courier New',
    monospace;

  /* Make sans = mono so font-sans classes work too */
  --font-family-sans: var(--font-family-mono);

  /* Single font size — override the scale */
  --font-size-base: 1rem;
  --line-height-base: 1.6;
}

/* Apply the font globally */
* {
  font-family: var(--font-family-mono);
  font-size: var(--font-size-base);
  line-height: var(--line-height-base);
}
```

## Tailwind CDN Play config (for quick prototyping)

```html
<script src="https://cdn.tailwindcss.com"></script>
<script>
  tailwind.config = {
    darkMode: 'media',
    theme: {
      extend: {
        fontFamily: {
          mono: ['IBM Plex Mono', 'ui-monospace', 'Cascadia Code', 'Fira Code', 'monospace'],
          sans: ['IBM Plex Mono', 'ui-monospace', 'Cascadia Code', 'Fira Code', 'monospace'],
        }
      }
    }
  }
</script>
<style>
  * { font-family: 'IBM Plex Mono', ui-monospace, monospace; font-size: 1rem; line-height: 1.6; }
</style>
```

## Global CSS tokens (framework-agnostic)

Use this if you're not using Tailwind:

```css
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:ital,wght@0,400;0,500;1,400&display=swap');

:root {
  --font: 'IBM Plex Mono', ui-monospace, 'Cascadia Code', 'Fira Code', monospace;
  --font-size: 1rem;
  --line-height: 1.6;

  --bg:      #FAFAF9;   /* stone-50  */
  --surface: #F5F5F4;   /* stone-100 */
  --border:  #E7E5E4;   /* stone-200 */
  --text:    #0C0A09;   /* stone-950 */

  --opacity-secondary: 0.6;
  --opacity-tertiary:  0.35;
  --opacity-disabled:  0.25;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg:      #0C0A09;  /* stone-950 */
    --surface: #1C1917;  /* stone-900 */
    --border:  #292524;  /* stone-800 */
    --text:    #FAFAF9;  /* stone-50  */
  }
}

*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  font-family: var(--font);
  font-size: var(--font-size);
  line-height: var(--line-height);
  color: var(--text);
  background-color: var(--bg);
}
```

## Palette swap: replacing stone

To use a different neutral scale, replace `stone` with your preferred option:

| Scale     | Swap command                              |
| --------- | ----------------------------------------- |
| zinc      | `sed -i 's/stone/zinc/g' your-file.html`  |
| neutral   | `sed -i 's/stone/neutral/g' ...`          |
| slate     | `sed -i 's/stone/slate/g' ...`            |
| gray      | `sed -i 's/stone/gray/g' ...`             |

Or in your editor: Find All → `stone` → Replace → `zinc` (etc).
