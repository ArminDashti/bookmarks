## Learned User Preferences

- When adding bookmark URLs, skip any link that already exists anywhere in the repo; do not insert duplicates.
- Requests like "add these" or "make sure these exist" mean ensure the URLs are bookmarked in the matching topical markdown files (not only that remotes are live).
- Place each new bookmark in the appropriate category file under topic folders rather than dumping unrelated links into one file.
- Update `metadata.json` `last-modified` whenever bookmark content changes.

## Learned Workspace Facts

- This repo is a curated personal bookmarks collection of markdown tables under topic folders such as `ai/`, `tech/`, `news/`, `companies/`, and `learning/`.
- Bookmark tables use columns Logo, App, Description, Owner, Links, and Website, typically with Google favicon image tags for the logo.
- MCP-related bookmarks live mainly in `ai/mcps/`; agent skills packs in `ai/tools/skills.md`; broader AI tools and agents in `ai/tools/` (for example `all.md`, `agents.md`).
- Companion public GitHub repos `aipedia-api` (Golang/Gin + PostgreSQL) and `aipedia-webui` (Vue.js + shadcn) were created for a public, SEO-oriented site related to this bookmarks content.
