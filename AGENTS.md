# Rules

- Investigate before coding and do deep analysis first.
- Use short English comments above non-obvious code sections.
- Follow the Frappe framework conventions.
- Reply to me in should simple english only.
- End replies with ✅ when rules are followed.

## Naming Conventions

- Python: snake_case for functions and variables.
- JavaScript: camelCase for variables, PascalCase for classes.
- DocType: Title Case with spaces.
- Files: snake_case.py, snake_case.js.


## Logging

- Frontend: `skills/logging/frontend_logging.md`
- Backend: `skills/logging/log_error.md`

---

# Frontend (JavaScript)

- `skills/frontend/field_properties.md` - Hide, enable, require, options
- `skills/frontend/dialogs.md` - msgprint, show_alert, confirm; HTML in message use frappe.utils.escape_html

---

# Database

- `skills/database/analyze_tables_and_processlist.md` - Analyze tables/columns and processlist; find what blocks migrate, KILL blocker, re-run migrate

---

# System

- `skills/system/system_console.md` - System Console (safe_exec) vs bench execute
- `skills/system/websocket_pwa_fix.md` - WebSocket/PWA/realtime fix: apps.txt order, gunicorn restart, nginx keepalive/ws headers, redis_socketio, Cloudflare

---

# Print & Reports

- `skills/print/print_format.md` - Jinja print formats
- `skills/print/wkhtmltopdf_print_format.md` - wkhtmltopdf print formats

---

# GitHub

- `skills/github/bug_report_github_issue_template.md` - ERPNext bug report template for GitHub issues

---

# Bench

- `skills/bench/describe_database_table.md` - `bench describe-database-table`
- `skills/bench/mariadb_query.md` - `bench mariadb -e`
