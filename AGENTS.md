# Skills Navigation Guide

This file is the top-level index for documentation under:
`/home/frappe/frappe-bench/apps/frappe_v15_mcp/skills/`

## How to use this index

- Start with the narrowest question you have.
- Pick by category folder (problem area) under `skills/`.
- Treat the category folders under `skills/` as the primary navigation (no index files are required).
- If two skills seem similar, open the narrower one first, then use the `Pick the right file` section inside the skill.

## Category Map (quick guidance)

### Frappe patterns

- `skills/frappe/api/` - whitelisted methods and HTTP exposure patterns.
- `skills/frappe/auth/` - authentication and session handling patterns.
- `skills/frappe/backend/` - controller lifecycle, save hooks, and validation flow.
- `skills/frappe/customization/` - custom fields, scripts, layout, property setters.
- `skills/frappe/data/` - ORM/SQL/query builder/transactions patterns.
- `skills/frappe/email/` - email account setup and sendmail usage.
- `skills/frappe/files/` - uploads and common file handling (pdf/xlsx/etc.).
- `skills/frappe/frontend/` - Desk form and list behavior.
- `skills/frappe/integrations/` - REST/webhook/OAuth integration patterns.
- `skills/frappe/logging/` - frontend + backend logging practices.
- `skills/frappe/mapping/` - document mapping/transformation.
- `skills/frappe/migrations/` - patches/fixtures and migration approach.
- `skills/frappe/naming/` - naming series and numbering behavior.
- `skills/frappe/notifications/` - queues, templates, and notification configuration.
- `skills/frappe/print/` - print formats and wkhtmltopdf notes.
- `skills/frappe/realtime/` - socket events and progress publishing patterns.
- `skills/frappe/reports/` - query/script report patterns.
- `skills/frappe/security/` - safe execution, permissions boundaries, and sharing rules.
- `skills/frappe/system/` - hooks, jobs, cache, permissions, scheduler tasks.
- `skills/frappe/testing/` - Frappe/unit test patterns and best practices.
- `skills/frappe/translations/` - translation usage and maintenance.
- `skills/frappe/utils/` - small helpers (date/money/string utilities).
- `skills/frappe/web/` - portal/web forms/pages/templates.
- `skills/frappe/workflow/` - workflow states, transitions, and related hooks.

### ERPNext patterns

- `skills/erpnext/controllers/` - base controller patterns.
- `skills/erpnext/accounting/` - GL entry patterns.
- `skills/erpnext/stock/` - stock ledger patterns.

### Ops

- `skills/ops/bench/` - bench CLI commands and site operations.
- `skills/ops/github/` - GitHub issue/report template guidance.

## Path format

- Use paths relative to the repository root, for example: `skills/frappe/data/get_doc.md`.

## Maintenance Notes

- If a skill file is added/removed/renamed, update this file to match the new structure.
- Prefer category paths over listing exact filenames here unless the name matters.
