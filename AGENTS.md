# AGENTS.md

This repo contains the `minimalist-design` agent skill and a demo website.

## Project structure

```
minimalist-design/       the installable skill (copy this to your skills dir)
  SKILL.md               frontmatter + core principles
  references/            loaded on demand for deeper detail
    design-system.md     CSS tokens, color scale, opacity ladder
    components.md        paste-ready Tailwind HTML snippets
    tailwind-config.md   Tailwind v3/v4 configs, CDN setup
    prompting.md         audit checklist, common mistakes
website/                 demo site deployed to minimal.ziki.boo
  index.html             self-contained demo page
  wrangler.jsonc         Cloudflare Worker deployment config
  worker.js              Worker that serves index.html
```

## Conventions

- The installable skill lives at `minimalist-design/` — not the repo root.
- The demo site is a plain HTML file served by a minimal Cloudflare Worker.
- No build step, no npm dependencies in the skill itself.
- IBM Plex Mono loaded from Google Fonts; no self-hosted assets.

## Updating the skill

When editing `SKILL.md` or any `references/*.md`:
- Keep `SKILL.md` under 500 lines. Move detailed content to `references/`.
- The description field in SKILL.md frontmatter drives model routing — keep it keyword-rich.
- Update `prompting.md` if new anti-patterns or common mistakes are discovered.
- Update `components.md` if new component patterns prove useful in practice.

## Deploying the demo site

```sh
cd website
npx wrangler deploy
```

The site deploys to `minimal.ziki.workers.dev` and is routed to `minimal.ziki.boo`.

## Update this file

When you make meaningful changes to the project structure, conventions, or deployment, update this file so future agents have accurate context.
