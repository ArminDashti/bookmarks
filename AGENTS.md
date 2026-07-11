# bookmarks

A static, curated collection of AI-related bookmarks stored as GitHub-flavored
Markdown tables under `ai/` (e.g. `ai/api/all.md`, `ai/chatbots/all.md`,
`ai/models/all.md`). There is no application code, package manifest, build
system, or automated test suite — the "product" is the rendered Markdown.

## Cursor Cloud specific instructions

- This repo is pure Markdown. There is nothing to compile, bundle, or unit-test.
  Development work = editing the bookmark tables and previewing how they render
  on GitHub.
- Preview (the closest thing to "running the app"): `grip` renders GFM exactly
  like GitHub. Serve the whole repo with `grip . 6419` and open
  `http://localhost:6419/` (README) or a page like
  `http://localhost:6419/ai/api/all.md`. `grip` is installed by the update
  script; if the `grip` command is not on PATH, use `python3 -m grip . 6419` or
  add `~/.local/bin` to PATH.
- `grip` calls GitHub's Markdown API to render, so it needs outbound network
  access. Without it, rendering fails; there is no offline fallback wired up.
- Lint: run `npx --yes markdownlint-cli2 "**/*.md"` (no config committed, so it
  uses defaults). It will report `MD033/no-inline-html` and
  `MD060/table-column-style` on the bookmark tables — these are expected and
  intentional: the tables embed `<img>` tags for logos/country flags and are not
  hand-aligned. Do not "fix" these by stripping the HTML; only treat genuinely
  new issues as actionable.
- The `.cursor/rules/database.mdc` (Pakhsh SQL Server) rule and the referenced
  `.cursor/skills/pakhsh-database/` scripts are not part of this repository's
  tree and are unrelated to previewing these bookmarks; ignore them for
  Markdown/preview work.
