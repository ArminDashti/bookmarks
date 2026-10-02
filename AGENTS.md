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

## Learned User Preferences

- When adding bookmark URLs, skip any link that already exists anywhere in the repo; do not insert duplicates.
- Requests like "add these" or "make sure these exist" mean ensure the URLs are bookmarked in the matching topical markdown files (not only that remotes are live).
- Place each new bookmark in the appropriate category file under topic folders rather than dumping unrelated links into one file.
- Update `metadata.json` `last-modified` whenever bookmark content changes.

## Learned Workspace Facts

- This repo is a curated personal bookmarks collection of markdown tables under topic folders such as `ai/`, `tech/`, `news/`, `companies/`, and `learning/`.
- Bookmark tables use columns Logo, App, Description, Owner, Links, and Website, typically with Google favicon image tags for the logo.
- MCP-related bookmarks live under `ai/mcps/` (for example `code.md`, `database.md`, `registries.md`); agent skills under `ai/skills/` (for example `collections.md`, `design.md`); broader AI tools and agents in `ai/tools/` (for example `all.md`, `agents.md`).
- Companion public GitHub repos `aipedia-api` (Golang/Gin + PostgreSQL) and `aipedia-webui` (Vue.js + shadcn) were created for a public, SEO-oriented site related to this bookmarks content.

<!-- gitnexus:start -->
# GitNexus — Code Intelligence

This project is indexed by GitNexus as **bookmarks** (109 symbols, 99 relationships, 0 execution flows).

> Index stale? Run `node .gitnexus/run.cjs analyze --index-only` from the project root — it auto-selects an available runner. No `.gitnexus/run.cjs` yet? Bootstrap with `npx`, `bunx`, or `pnpm dlx` — e.g. `bunx gitnexus@latest analyze` (npm 11 npx crash; #1939).

## Always Do

- **MUST run impact before editing.** Use `impact({target: "symbolName", direction: "upstream"})` or `node .gitnexus/run.cjs impact "symbolName" --direction upstream --repo .`; report callers, processes, and risk. Never substitute grep for graph analysis.
- **MUST analyze graph changes before committing.** Use `detect_changes({scope: "all"})` (MCP) or `node .gitnexus/run.cjs detect-changes --scope all --repo .` (CLI fallback). `partial: true` or `truncated: true` is not a clean check — a zero means unseen, not unaffected; re-run it. For regression review: `detect_changes({scope: "compare", base_ref: "main"})` or `node .gitnexus/run.cjs detect-changes --scope compare --base-ref "main" --repo .`.
- MUST warn on HIGH/CRITICAL `risk` pre-edit; never use `riskSharedAxes` to waive a HIGH/CRITICAL `risk` warning. Compare File/symbol: MCP File omits axes; Graph-RAG expands File.
- **MUST treat `risk: UNKNOWN` as unresolved, not as low.** An empty caller set is not evidence the symbol is unused — it can also mean the callers are not resolvable by the index (plain-object property access, dynamic dispatch, cross-language calls). `impact` pairs `UNKNOWN` with a `riskNote` saying so. Confirm with a text search before treating the symbol as safe to change or delete; do not proceed on the strength of a zero.
- **MUST use `query({search_query: "concept"})` for concepts/flows, `context({name: "symbolName"})` for a named symbol, or `impact` for blast radius, on read-only callers, dependencies, imports, or execution flow.** Graph first; text search only for empty/`UNKNOWN`/literals.
- For security review, `explain({target: "fileOrSymbol"})` lists taint findings (source→sink flows; needs `analyze --pdg`).

## Never Do

- NEVER edit a function, class, or method before MCP/CLI impact analysis.
- NEVER ignore HIGH or CRITICAL risk warnings from impact analysis, and never read `UNKNOWN` as an all-clear — it means the walk could not answer, which is the one verdict that requires confirming by other means.
- NEVER rename symbols with find-and-replace — use `rename` which understands the call graph.
- NEVER commit before MCP/CLI graph change analysis.

## Resources

| Resource | Use for |
| --- | --- |
| `gitnexus://repo/bookmarks/context` | Codebase overview, check index freshness |
| `gitnexus://repo/bookmarks/clusters` | All functional areas |
| `gitnexus://repo/bookmarks/processes` | All execution flows |
| `gitnexus://repo/bookmarks/process/{name}` | Step-by-step execution trace |

## CLI

| Task | Read this skill file |
| --- | --- |
| Understand architecture / "How does X work?" | `.claude/skills/gitnexus-exploring/SKILL.md` |
| Blast radius / "What breaks if I change X?" | `.claude/skills/gitnexus-impact-analysis/SKILL.md` |
| Trace bugs / "Why is X failing?" | `.claude/skills/gitnexus-debugging/SKILL.md` |
| Rename / extract / split / refactor | `.claude/skills/gitnexus-refactoring/SKILL.md` |
| Tools, resources, schema reference | `.claude/skills/gitnexus-guide/SKILL.md` |
| Index, status, clean, wiki CLI commands | `.claude/skills/gitnexus-cli/SKILL.md` |

<!-- gitnexus:end -->

<!-- lean-ctx -->
## lean-ctx

lean-ctx is active — the MCP tools replace native equivalents.
Full rules: LEAN-CTX.md (open on demand — do not auto-load).
<!-- /lean-ctx -->
