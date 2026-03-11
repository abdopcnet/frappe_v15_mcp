# How to use with Cursor, VSCode, GitMCP (v15)

## 1) GitMCP (via GitHub)

- [GitMCP](https://gitmcp.io/) provides remote MCP for any GitHub repo.
- Push this folder to GitHub, then in Cursor or VSCode add MCP server URL: `https://gitmcp.io/OWNER/REPO`
- Same path as GitHub, but domain `gitmcp.io` instead of `github.com`.

## 2) Local in Cursor

- Include `frappe_v15_mcp` in your workspace.
- In Agent rules or a RULE file, reference `rules/AGENTS_RULES.md` and `llms.txt`.
- Each file under `skills/` has one short instruction.

## 3) VSCode

- Same: either use GitMCP after push, or open this folder in workspace and reference the files.
- If using an MCP extension, set the GitMCP URL as in (1).

## Version

- **Frappe/ERPNext v15**.
