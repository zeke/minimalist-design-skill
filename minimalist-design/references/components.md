# Component Reference

Paste-ready Tailwind HTML. All components use IBM Plex Mono, stone palette, and opacity hierarchy.

Every color class requires a `dark:` counterpart. Opacity-based text (`opacity-60`, `opacity-35`) needs no dark variant.

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
  <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      darkMode: 'media',
      theme: {
        extend: {
          fontFamily: {
            mono: ['IBM Plex Mono', 'ui-monospace', 'Cascadia Code', 'Fira Code', 'monospace'],
          }
        }
      }
    }
  </script>
  <style>
    * { font-family: 'IBM Plex Mono', ui-monospace, monospace; font-size: 1rem; }
  </style>
</head>
<body class="bg-stone-50 text-stone-950 dark:bg-stone-950 dark:text-stone-50">
  <!-- content -->
</body>
</html>
```

---

## Navigation

```html
<nav class="border-b border-stone-200 dark:border-stone-800">
  <div class="max-w-5xl mx-auto px-6 md:px-8 flex items-center justify-between h-14">
    <a href="/" class="font-medium">site name</a>
    <div class="flex items-center gap-8">
      <a href="/docs" class="opacity-60 hover:opacity-100 transition-opacity">docs</a>
      <a href="/about" class="opacity-60 hover:opacity-100 transition-opacity">about</a>
      <a href="/github" class="opacity-60 hover:opacity-100 transition-opacity">github</a>
    </div>
  </div>
</nav>
```

---

## Hero

```html
<section class="max-w-3xl mx-auto px-6 md:px-8 py-24">
  <h1 class="font-medium mb-4">Tool name</h1>
  <p class="opacity-60 mb-8">One or two sentences describing what this does and who it's for. Keep it factual.</p>
  <div class="flex items-center gap-4">
    <a href="/get-started" class="border border-stone-950 dark:border-stone-50 px-4 py-2 hover:bg-stone-950 hover:text-stone-50 dark:hover:bg-stone-50 dark:hover:text-stone-950 transition-colors">get started</a>
    <a href="/docs" class="opacity-60 hover:opacity-100 transition-opacity px-4 py-2">read the docs →</a>
  </div>
</section>
```

---

## Section heading

```html
<section class="max-w-3xl mx-auto px-6 md:px-8 py-16">
  <h2 class="font-medium mb-2">Section title</h2>
  <p class="opacity-60 mb-8">Supporting description for this section.</p>
  <!-- content -->
</section>
```

---

## Buttons

```html
<!-- Primary: filled -->
<button class="bg-stone-950 text-stone-50 dark:bg-stone-50 dark:text-stone-950 px-4 py-2 hover:opacity-80 transition-opacity">
  primary action
</button>

<!-- Secondary: outlined -->
<button class="border border-stone-950 dark:border-stone-50 px-4 py-2 hover:bg-stone-950 hover:text-stone-50 dark:hover:bg-stone-50 dark:hover:text-stone-950 transition-colors">
  secondary action
</button>

<!-- Ghost: no border -->
<button class="opacity-60 hover:opacity-100 transition-opacity px-4 py-2">
  ghost action
</button>

<!-- Destructive: uses red — exception to monochrome rule -->
<button class="text-red-600 dark:text-red-400 opacity-80 hover:opacity-100 transition-opacity px-4 py-2">
  delete
</button>
```

---

## Cards

```html
<!-- Basic card -->
<div class="border border-stone-200 dark:border-stone-800 p-6">
  <p class="font-medium mb-1">Card title</p>
  <p class="opacity-60">Card description or body content goes here.</p>
</div>

<!-- Card with top border accent (use sparingly) -->
<div class="border border-stone-200 dark:border-stone-800 border-t-stone-950 dark:border-t-stone-50 border-t-2 p-6">
  <p class="font-medium mb-1">Accented card</p>
  <p class="opacity-60">Use the top border accent only for featured or active items.</p>
</div>

<!-- Card grid -->
<div class="grid grid-cols-1 md:grid-cols-3 gap-4">
  <div class="border border-stone-200 dark:border-stone-800 p-6">
    <p class="font-medium mb-1">Feature one</p>
    <p class="opacity-60">Description of the feature.</p>
  </div>
  <div class="border border-stone-200 dark:border-stone-800 p-6">
    <p class="font-medium mb-1">Feature two</p>
    <p class="opacity-60">Description of the feature.</p>
  </div>
  <div class="border border-stone-200 dark:border-stone-800 p-6">
    <p class="font-medium mb-1">Feature three</p>
    <p class="opacity-60">Description of the feature.</p>
  </div>
</div>
```

---

## Prose / body text

```html
<article class="max-w-3xl mx-auto px-6 md:px-8 py-16 space-y-6">
  <h1 class="font-medium">Document title</h1>

  <p>
    Body text at full opacity is primary. Write in short paragraphs.
    Keep line length comfortable with <code>max-w-3xl</code>.
  </p>

  <p class="opacity-60">
    Secondary paragraphs — context, caveats, or supplementary info — use opacity-60.
  </p>

  <h2 class="font-medium pt-4">Section heading</h2>

  <p>Content continues here.</p>

  <p class="italic opacity-60">
    Italics for asides, attributions, and annotations.
  </p>
</article>
```

---

## Code block

```html
<pre class="bg-stone-100 dark:bg-stone-900 border border-stone-200 dark:border-stone-800 p-4 overflow-x-auto"><code>const result = await fetch('/api/data')
const json = await result.json()
console.log(json)</code></pre>
```

Inline code:
```html
<code class="bg-stone-100 dark:bg-stone-900 px-1">inline code</code>
```

---

## Table

```html
<div class="overflow-x-auto">
  <table class="w-full border-collapse">
    <thead>
      <tr class="border-b border-stone-200 dark:border-stone-800">
        <th class="text-left font-medium py-3 pr-8">Column</th>
        <th class="text-left font-medium py-3 pr-8">Type</th>
        <th class="text-left font-medium py-3">Description</th>
      </tr>
    </thead>
    <tbody class="divide-y divide-stone-200 dark:divide-stone-800">
      <tr>
        <td class="py-3 pr-8">name</td>
        <td class="py-3 pr-8 opacity-60">string</td>
        <td class="py-3 opacity-60">The display name of the item</td>
      </tr>
      <tr>
        <td class="py-3 pr-8">value</td>
        <td class="py-3 pr-8 opacity-60">number</td>
        <td class="py-3 opacity-60">Numeric value, must be positive</td>
      </tr>
      <tr>
        <td class="py-3 pr-8">active</td>
        <td class="py-3 pr-8 opacity-60">boolean</td>
        <td class="py-3 opacity-60">Whether the item is currently active</td>
      </tr>
    </tbody>
  </table>
</div>
```

---

## Form

```html
<form class="max-w-3xl space-y-6">
  <!-- Text input -->
  <div class="space-y-1">
    <label class="font-medium">Label</label>
    <input
      type="text"
      placeholder="placeholder"
      class="w-full border border-stone-300 dark:border-stone-700 bg-transparent px-3 py-2 focus:outline-none focus:border-stone-950 dark:focus:border-stone-50 transition-colors placeholder:opacity-35"
    >
    <p class="opacity-60">Optional helper text below the input.</p>
  </div>

  <!-- Textarea -->
  <div class="space-y-1">
    <label class="font-medium">Message</label>
    <textarea
      rows="4"
      placeholder="write something..."
      class="w-full border border-stone-300 dark:border-stone-700 bg-transparent px-3 py-2 focus:outline-none focus:border-stone-950 dark:focus:border-stone-50 transition-colors placeholder:opacity-35 resize-none"
    ></textarea>
  </div>

  <!-- Select -->
  <div class="space-y-1">
    <label class="font-medium">Option</label>
    <select class="w-full border border-stone-300 dark:border-stone-700 bg-stone-50 dark:bg-stone-950 px-3 py-2 focus:outline-none focus:border-stone-950 dark:focus:border-stone-50 transition-colors">
      <option value="">choose one</option>
      <option value="a">option a</option>
      <option value="b">option b</option>
    </select>
  </div>

  <!-- Checkbox -->
  <div class="flex items-start gap-3">
    <input type="checkbox" id="agree" class="mt-1 accent-stone-950 dark:accent-stone-50">
    <label for="agree" class="opacity-60">I agree to the terms and conditions</label>
  </div>

  <!-- Submit -->
  <button type="submit" class="border border-stone-950 dark:border-stone-50 px-4 py-2 hover:bg-stone-950 hover:text-stone-50 dark:hover:bg-stone-50 dark:hover:text-stone-950 transition-colors">
    submit
  </button>
</form>
```

---

## Key/value list

```html
<dl class="space-y-3">
  <div class="flex gap-8">
    <dt class="opacity-60 w-32 shrink-0">version</dt>
    <dd>1.4.2</dd>
  </div>
  <div class="flex gap-8">
    <dt class="opacity-60 w-32 shrink-0">license</dt>
    <dd>MIT</dd>
  </div>
  <div class="flex gap-8">
    <dt class="opacity-60 w-32 shrink-0">updated</dt>
    <dd>2025-06-25</dd>
  </div>
</dl>
```

---

## Badge / tag

```html
<!-- Neutral badge -->
<span class="border border-stone-300 dark:border-stone-700 px-2 py-0.5 opacity-60">label</span>

<!-- Active / selected badge -->
<span class="bg-stone-950 text-stone-50 dark:bg-stone-50 dark:text-stone-950 px-2 py-0.5">active</span>
```

---

## Divider

```html
<!-- Horizontal rule -->
<hr class="border-stone-200 dark:border-stone-800">

<!-- Section break with label -->
<div class="flex items-center gap-4">
  <hr class="flex-1 border-stone-200 dark:border-stone-800">
  <span class="opacity-35">or</span>
  <hr class="flex-1 border-stone-200 dark:border-stone-800">
</div>
```

---

## Alert / callout

```html
<!-- Info -->
<div class="border-l-2 border-stone-950 dark:border-stone-50 pl-4 py-1">
  <p class="font-medium mb-1">Note</p>
  <p class="opacity-60">This is an informational callout. Use border-l-2 to distinguish without color.</p>
</div>

<!-- Warning (one exception: amber) -->
<div class="border-l-2 border-amber-500 pl-4 py-1">
  <p class="font-medium mb-1 text-amber-700 dark:text-amber-400">Warning</p>
  <p class="opacity-60">Warnings may use amber as the single accent exception.</p>
</div>
```

---

## Footer

```html
<footer class="border-t border-stone-200 dark:border-stone-800 mt-24">
  <div class="max-w-5xl mx-auto px-6 md:px-8 py-8 flex items-center justify-between">
    <p class="opacity-60">© 2025 Your Name</p>
    <div class="flex items-center gap-6">
      <a href="/privacy" class="opacity-60 hover:opacity-100 transition-opacity">privacy</a>
      <a href="/terms" class="opacity-60 hover:opacity-100 transition-opacity">terms</a>
      <a href="https://github.com" class="opacity-60 hover:opacity-100 transition-opacity">github</a>
    </div>
  </div>
</footer>
```
