# Skills Navigation Guide

This file is the top-level index for documentation under:
`/home/frappe/frappe-bench-15/apps/frappe_v15_mcp/skills/`

## How to use this index

- Start with the narrowest question you have.
- Pick by category folder (problem area) under `skills/`.
- Treat `skills/README.md` and `skills/STRUCTURE.md` as indexes (navigation helpers), not topic skills.
- If two skills seem similar, open the narrower one first, then use the `Pick the right file` section inside the skill.

## Category Map (quick guidance)

- `skills/api/` - pick for whitelisted methods and HTTP exposure patterns.
- `skills/auth/` - pick for authentication and session handling patterns.
- `skills/backend/` - pick for controller lifecycle, save hooks, and validation flow.
- `skills/bench/` - pick for bench CLI commands and site operations.
- `skills/custom/` - pick for custom fields, scripts, layout, and property setter behavior.
- `skills/database/` - pick for ORM/SQL/query builder/transactions patterns.
- `skills/email/` - pick for email account setup and sendmail usage.
- `skills/erpnext/` - pick for ERPNext controller and ledger-related patterns.
- `skills/files/` - pick for uploads and common file handling (pdf/xlsx/etc.).
- `skills/frontend/` - pick for Desk form and list behavior.
- `skills/github/` - pick for GitHub issue/report template guidance.
- `skills/integrations/` - pick for REST/webhook/OAuth integration patterns.
- `skills/logging/` - pick for frontend + backend logging practices.
- `skills/mapping/` - pick for document mapping/transformation.
- `skills/migrations/` - pick for patches/fixtures and migration approach.
- `skills/naming/` - pick for naming series and numbering behavior.
- `skills/notifications/` - pick for queues, templates, and notification configuration.
- `skills/print/` - pick for print formats and wkhtmltopdf notes.
- `skills/realtime/` - pick for socket events and progress publishing patterns.
- `skills/reports/` - pick for query/script report patterns.
- `skills/security/` - pick for safe execution, permissions boundaries, and sharing rules.
- `skills/system/` - pick for hooks, jobs, cache, permissions, and scheduler tasks.
- `skills/testing/` - pick for Frappe/unit test patterns and best practices.
- `skills/translations/` - pick for translation usage and maintenance.
- `skills/utils/` - pick for small helpers (date/money/string utilities).
- `skills/web/` - pick for portal/web forms/pages/templates.
- `skills/workflow/` - pick for workflow states, transitions, and related hooks.

## Path format

- Use paths relative to the repository root, for example: `skills/database/get_doc.md`.

## Maintenance Notes

- If a skill file is added/removed/renamed, update this file and `skills/STRUCTURE.md` together.
- Prefer category paths over listing exact filenames here unless the name matters.
