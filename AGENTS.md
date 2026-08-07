# AGENTS.md

## Cursor Cloud specific instructions

### What this repo is
This is a **static Markdown "bookmarks" knowledge base** — a curated collection of
Markdown files that catalog links to AI tools, companies, developer tooling, and tech
resources. It is **content, not an application**: there is no source code, build system,
test suite, package manifest, or runnable service.

- Metadata lives in `metadata.json` (`name: bookmarks`).
- Content is organized by topic directories (`ai/`, `tech/`, `companies/`, `learning/`,
  `news/`, `logs/`). Empty topic dirs are kept with `.gitkeep`.
- Most content files are Markdown tables with the columns:
  `| Logo | App | Description | Owner | Links | Website |`, where `Logo` is an inline
  `<img>` favicon (`https://www.google.com/s2/favicons?domain=...`).
- The repo is maintained by an external automation (`github-commit-push-all-repos`, see
  the `.gitignore` header) that appends entries and commits them.

### Development workflow
- There is **nothing to build, lint, test, or run**. "Development" = editing Markdown
  tables and committing via git.
- To validate a change, confirm the Markdown table syntax is valid and the entry renders
  correctly in any Markdown previewer or on GitHub. Favicon images require internet access
  to load (they point at `google.com/s2/favicons`).
- No dependency install is required; the environment only needs git (Python 3 and Node are
  also available but not used by the repo).

### Ignore these stale rules
`.cursor/rules/database.mdc` (a "Pakhsh" VB.NET / SQL Server ERP project) and
`.cursor/rules/required-skills.mdc` do **not** correspond to this repository — the files
and skills they reference (e.g. `.cursor/skills/pakhsh-database/`) do not exist here. Treat
them as leftover global rules and disregard them when working in this repo.
