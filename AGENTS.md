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

# Self-learning (for AI coding agents)

This file makes any coding agent **self-improving**: recognize a hard-won
"golden path" during a task and persist it so the next session starts already
knowing it, instead of rediscovering how to reach the DB, where the creds live,
how to deploy, or how to verify a change live.

It works with any agent that reads a standing instructions file (Codex, Zed,
Aider, Gemini CLI, …). Richer, tool-native installs exist too — a Claude Code
**skill** (`skills/self-learning/SKILL.md`) and a **Cursor rule**
(`.cursor/rules/self-learning.mdc`); see the README. This file is the portable,
lowest-common-denominator version.

## The loop

**1. Recognize the moment.** Any one of these is a cue:
- a task only worked after several attempts, wrong turns, or a correction;
- you discovered project facts you didn't know up front — where creds/env vars
  live, a non-obvious command, a required sequence, a gotcha;
- an operational workflow likely to recur (reach the dev/prod DB, deploy, run
  migrations, seed data, verify live, tail the right logs);
- the user says "remember this" / "don't make me re-explain this next time".

Act on the cue immediately — **don't ask permission first**. Capture it, then
tell the user what you saved and where. They can always edit or delete it.

**2. Capture it where your tool auto-loads knowledge next session:**
- Claude Code / any Agent Skills client → a new `skills/<name>/SKILL.md`
- Cursor → a new `.cursor/rules/learned/<name>.mdc`
- Otherwise → append a dated entry under [Learned](#learned) below, or to your
  project's notes/memory file.

Capture the **procedure** (commands, paths, the required order, gotchas) — not a
one-off answer — and the **failures** too: the approaches you ruled out and why,
so next time skips the dead-ends.

**3. Reuse.** Next session the persisted entry loads automatically (by skill/rule
description, or because this file is always read) and you start from the golden
path.

## Promotion rule

A saved entry is authoritative — future sessions trust it without re-deriving it.
Only promote a session to a durable entry when **all three** hold:

1. **A passing check** — the path was actually verified (a test passed, the
   command exited clean, the repro reproduced, the build went green). Record it.
   "Seemed to work" doesn't count.
2. **A named failure pattern** — you can name the failure it avoids or diagnoses,
   not a vague "sometimes it breaks".
3. **At least one ruled-out dead-end** — a concrete approach you tried and
   eliminated, with the reason.

If any is missing, it isn't durable yet — leave a tentative note (marked
unverified) or skip it. This keeps confident guesses out.

## Rules

- **Never write secret values** — no tokens, passwords, connection strings, or
  API keys. Record only *where* a secret lives (env var name, config/selector,
  secret manager). Reproducing a secret into a shared file leaks it.
- **A one-line fact or correction** → put it in lightweight notes/memory, not a
  whole rule or skill.
- **A genuine one-off** unlikely to recur → skip it.
- **Capture procedures, not answers** — teach how to approach the class of
  problem, so it generalizes next time.

## Learned

<!-- When no richer mechanism is available, append dated golden-path entries here.
     Format: ### YYYY-MM-DD — <title>  /  **Goal**, **Steps**, **Gotchas**,
     **What didn't work**. Keep secrets out — point to where they live. -->
