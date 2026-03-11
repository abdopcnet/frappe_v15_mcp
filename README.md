# ERPNext / Frappe MCP Context — v15

Use this folder as Frappe/ERPNext v15 reference in Cursor or VSCode.

## Add this MCP

**MCP Server URL:** `https://gitmcp.io/abdopcnet/frappe_v15_mcp.git`

**Cursor** — update `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "frappe_v15_mcp.git Docs": {
      "url": "https://gitmcp.io/abdopcnet/frappe_v15_mcp.git"
    }
  }
}
```

**Claude Desktop** — update your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "frappe_v15_mcp.git Docs": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://gitmcp.io/abdopcnet/frappe_v15_mcp.git"
      ]
    }
  }
}
```

**Windsurf** — update `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "frappe_v15_mcp.git Docs": {
      "serverUrl": "https://gitmcp.io/abdopcnet/frappe_v15_mcp.git"
    }
  }
}
```

**VSCode** — update `.vscode/mcp.json`:

```json
{
  "servers": {
    "frappe_v15_mcp.git Docs": {
      "type": "sse",
      "url": "https://gitmcp.io/abdopcnet/frappe_v15_mcp.git"
    }
  }
}
```

**Cline** — update `~/Library/Application Support/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "frappe_v15_mcp.git Docs": {
      "url": "https://gitmcp.io/abdopcnet/frappe_v15_mcp.git",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## GitMCP (remote)

- Push this repo to GitHub, then add the MCP using the configs above with URL: `https://gitmcp.io/abdopcnet/frappe_v15_mcp.git`

## Local (Cursor)

- Add this folder to your project or use the `*.md` files as references.
- Or reference `AGENTS.md` for rules and full skills index.

## Structure

- `AGENTS.md` — Rules + full skills index (single reference).
- `skills/` — One short instruction per file (Frontend, Backend, DB, API, Bench, etc.).

## Version

- Frappe/ERPNext **v15**. Do not modify `frappe`, `erpnext`, `hrms`.
