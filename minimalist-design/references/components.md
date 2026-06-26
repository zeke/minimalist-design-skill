# Component Reference

Paste-ready HTML. No Tailwind required — all patterns work with plain CSS and the token block from design-system.md.

One font, one size, one weight, one color. No opacity classes. Hierarchy from spacing and ASCII convention only.

---

## Page shell

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page title</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono&display=swap" rel="stylesheet">
  <style>
    :root { --bg: #FAFAF9; --text: #0C0A09; }
    @media (prefers-color-scheme: dark) { :root { --bg: #0C0A09; --text: #FAFAF9; } }
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html {
      font-family: 'IBM Plex Mono', ui-monospace, monospace;
      font-size: 1rem; font-weight: 400; line-height: 1.6;
      background: var(--bg); color: var(--text);
    }
    body { max-width: 640px; margin: 0 auto; padding: 3rem 1.5rem 6rem; }
  </style>
</head>
<body>
  <!-- content -->
</body>
</html>
```

---

## Page header

```html
<p>Site or project name</p>
<p>One-line description of what this is.</p>
```

No nav bar. No logo. Name and tagline as plain paragraphs.

---

## Section

```html
<section style="margin-top: 3rem">
  <p>SECTION HEADING</p>
  <p style="margin-top: 1rem">Body text here. Paragraphs separated by 1rem margin.</p>
  <p style="margin-top: 1rem">Another paragraph.</p>
</section>
```

All-caps text as the heading convention. No border, no font-weight change, no color change.

---

## Horizontal rule

```html
<hr style="border: none; border-top: 1px solid currentColor; margin: 3rem 0;">
```

Used between major sections only.

---

## List

```html
<ul style="padding-left: 1.5rem; margin-top: 1rem;">
  <li>First item</li>
  <li style="margin-top: 0.25rem">Second item</li>
  <li style="margin-top: 0.25rem">Third item</li>
</ul>
```

---

## Key/value list

```html
<dl style="margin-top: 1rem;">
  <div style="display: flex; gap: 2rem; margin-top: 0.5rem;">
    <dt style="min-width: 8rem;">version</dt>
    <dd>1.0.0</dd>
  </div>
  <div style="display: flex; gap: 2rem; margin-top: 0.5rem;">
    <dt style="min-width: 8rem;">license</dt>
    <dd>MIT</dd>
  </div>
  <div style="display: flex; gap: 2rem; margin-top: 0.5rem;">
    <dt style="min-width: 8rem;">updated</dt>
    <dd>2025-06-26</dd>
  </div>
</dl>
```

---

## Code block

```html
<pre style="margin-top: 1rem; padding: 1rem; border: 1px solid currentColor; overflow-x: auto;"><code>const result = await fetch('/api/data')
const json = await result.json()</code></pre>
```

Inline code:
```html
<code>inline</code>
```

---

## Table

```html
<table style="width: 100%; border-collapse: collapse; margin-top: 1rem;">
  <thead>
    <tr>
      <th style="text-align: left; padding: 0.5rem 2rem 0.5rem 0; border-bottom: 1px solid currentColor;">token</th>
      <th style="text-align: left; padding: 0.5rem 2rem 0.5rem 0; border-bottom: 1px solid currentColor;">value</th>
      <th style="text-align: left; padding: 0.5rem 0 0.5rem 0; border-bottom: 1px solid currentColor;">role</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 0.5rem 2rem 0.5rem 0;">--bg</td>
      <td style="padding: 0.5rem 2rem 0.5rem 0;">#FAFAF9</td>
      <td style="padding: 0.5rem 0;">page background</td>
    </tr>
    <tr>
      <td style="padding: 0.5rem 2rem 0.5rem 0;">--text</td>
      <td style="padding: 0.5rem 2rem 0.5rem 0;">#0C0A09</td>
      <td style="padding: 0.5rem 0;">primary text</td>
    </tr>
  </tbody>
</table>
```

---

## Form

```html
<form style="margin-top: 1rem;">
  <div style="margin-top: 1.5rem;">
    <label for="name" style="display: block;">name</label>
    <input
      id="name" type="text" placeholder="your name"
      style="display: block; width: 100%; margin-top: 0.5rem; padding: 0.5rem 0;
             background: transparent; border: none; border-bottom: 1px solid currentColor;
             color: inherit; font: inherit; outline: none;">
  </div>
  <div style="margin-top: 1.5rem;">
    <label for="message" style="display: block;">message</label>
    <textarea
      id="message" rows="3" placeholder="say something..."
      style="display: block; width: 100%; margin-top: 0.5rem; padding: 0.5rem 0;
             background: transparent; border: none; border-bottom: 1px solid currentColor;
             color: inherit; font: inherit; outline: none; resize: none;"></textarea>
  </div>
  <button type="submit"
    style="margin-top: 1.5rem; background: none; border: 1px solid currentColor;
           color: inherit; font: inherit; padding: 0.5rem 1.5rem; cursor: pointer;">
    submit
  </button>
</form>
```

---

## Blockquote

```html
<blockquote style="margin-top: 1rem; padding-left: 1.5rem; border-left: 2px solid currentColor;">
  The session is the story.
</blockquote>
```

---

## Footer

```html
<footer style="margin-top: 6rem; border-top: 1px solid currentColor; padding-top: 1.5rem;">
  <p>MIT license · <a href="https://github.com/you/project">github</a></p>
</footer>
```

---

## Navigation (minimal)

```html
<nav style="display: flex; justify-content: space-between; margin-bottom: 3rem;">
  <a href="/">project name</a>
  <div style="display: flex; gap: 2rem;">
    <a href="/docs">docs</a>
    <a href="/about">about</a>
  </div>
</nav>
```

No styling beyond layout. Links are the same color as everything else.
