# minimalist-design-skill

An agent skill for building minimal, monospace interfaces. IBM Plex Mono throughout, stone palette, opacity-based hierarchy, dark and light mode.

## Install

```sh
npx skills add zeke/minimalist-design-skill
```

Or manually:

```sh
gh repo clone zeke/minimalist-design-skill /tmp/mds
cp -r /tmp/mds/minimalist-design ~/.config/opencode/skills/
```

Works with OpenCode, Claude Code, Cursor, GitHub Copilot, and any agent that supports the [Agent Skills](https://agentskills.io) spec.

## What it covers

Invoke this skill when the user asks for a minimal, minimalist, simple, clean, stark, or monospace design. Trigger phrases include "keep it simple", "nothing fancy", "just make it clean", "strip it back", "developer aesthetic", "text-first", or "no frills".

The skill provides:

- Core design principles (one font, one size, opacity hierarchy, no decoration)
- Google Fonts setup for IBM Plex Mono
- Tailwind v3 and v4 config
- CSS custom properties for use without Tailwind
- Paste-ready HTML components (nav, hero, buttons, cards, forms, tables, code blocks, callouts)
- Dark/light mode implementation via `prefers-color-scheme`
- Audit checklist for applying the system to existing pages

## Principles

1. One font, one size — IBM Plex Mono at 1rem everywhere
2. Opacity creates hierarchy — 100%, 60%, 35%
3. Stone palette by default — swappable for zinc, slate, neutral, or gray
4. No decoration — no shadows, gradients, or large rounded corners
5. System dark mode — `prefers-color-scheme`, no JavaScript

## Demo

[minimal.ziki.workers.dev](https://minimal.ziki.workers.dev)

## What's included

```
minimalist-design/
├── SKILL.md
└── references/
    ├── design-system.md    color tokens, opacity ladder, spacing scale
    ├── components.md       paste-ready Tailwind HTML snippets
    ├── tailwind-config.md  v3 config, v4 @theme block, CDN setup
    └── prompting.md        audit checklist, common mistakes
website/
├── index.html              demo page
└── wrangler.jsonc          Cloudflare Worker deployment config
```

## License

MIT
