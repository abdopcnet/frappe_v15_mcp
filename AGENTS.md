# Rules

- Investigate before coding and do deep analysis first.
- Use short English comments above non-obvious code sections.
- Follow the Frappe framework conventions.
- End replies with ✅ when rules are followed.

## Naming Conventions

- Python: snake_case for functions and variables.
- JavaScript: camelCase for variables, PascalCase for classes.
- DocType: Title Case with spaces.
- Files: snake_case.py, snake_case.js.

---

## Category Map

- `skills/api/` - API exposure and whitelisted methods `(2)`
- `skills/auth/` - authentication and session handling `(2)`
- `skills/backend/` - controller lifecycle, save, validation `(3)`
- `skills/bench/` - bench CLI and site operations `(41)`
- `skills/custom/` - custom fields, scripts, layout, property setter `(5)`
- `skills/database/` - ORM, SQL, query builder, transactions `(9)`
- `skills/email/` - email account setup and sendmail usage `(2)`
- `skills/erpnext/` - ERPNext controller and ledger patterns `(3)`
- `skills/files/` - upload, pdf, xlsx `(3)`
- `skills/frontend/` - Desk form and list behavior `(13)`
- `skills/github/` - GitHub issue/report template guidance `(1)`
- `skills/integrations/` - REST, webhook, OAuth patterns `(3)`
- `skills/logging/` - frontend and backend logging `(2)`
- `skills/mapping/` - document mapping `(1)`
- `skills/migrations/` - patches and fixtures `(2)`
- `skills/naming/` - naming series `(1)`
- `skills/notifications/` - queue, template, notification config `(3)`
- `skills/print/` - print formats and wkhtmltopdf notes `(2)`
- `skills/realtime/` - socket events and progress publishing `(2)`
- `skills/reports/` - query and script reports `(2)`
- `skills/security/` - safe execution and sharing `(2)`
- `skills/system/` - hooks, jobs, cache, permissions, scheduler `(11)`
- `skills/testing/` - Frappe and unit test patterns `(2)`
- `skills/translations/` - translation usage and maintenance `(2)`
- `skills/utils/` - date, money, string helpers `(3)`
- `skills/web/` - portal, web form, page, template `(4)`
- `skills/workflow/` - workflow states and transitions `(2)`

## Path Rules

- Use paths relative to the repository root, for example `skills/database/get_doc.md`.
- Treat `skills/README.md` and `skills/STRUCTURE.md` as indexes, not topic skills.
- When two files look related, read the `Pick the right file` section inside the skill before merging concepts.

## Maintenance Notes

- If a skill file is added, removed, or renamed, update this file and `skills/STRUCTURE.md` together.
- Keep counts in sync with the actual folder contents.
- Prefer category paths over listing every file here unless the exact filename matters.
