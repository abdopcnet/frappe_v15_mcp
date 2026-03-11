# Rules

- **Investigate before coding** — understand and analyze first.
- **When following this rule** — end your reply with ✅.
- **Frappe/ERPNext** — follow their standards; English-only short comments above code.
- **Never modify** — `frappe`, `erpnext`, `hrms`.

## Naming Conventions

- Python: `snake_case` for functions, variables
- JavaScript: `camelCase` for variables, `PascalCase` for classes
- DocType: Title Case with spaces
- Files: `snake_case.py`, `snake_case.js`

## Logging

- Frontend: `skills/logging/frontend_logging.md`
- Backend: `skills/logging/log_error.md`

---

# Frontend (JavaScript)

- `skills/frontend/set_value.md` - Get/set form values
- `skills/frontend/field_properties.md` - Hide, enable, require, options
- `skills/frontend/refresh_field.md` - Refresh field(s)
- `skills/frontend/custom_buttons.md` - Add/remove buttons, primary action
- `skills/frontend/set_intro.md` - Intro message, dashboard indicator
- `skills/frontend/form_state.md` - is_new, is_dirty
- `skills/frontend/form_events.md` - Lifecycle and field handlers
- `skills/frontend/child_table.md` - Child table add/clear/events
- `skills/frontend/set_query.md` - Link field filters
- `skills/frontend/api_calls.md` - frappe.call, frappe.xcall
- `skills/frontend/dialogs.md` - msgprint, show_alert, confirm; HTML use frappe.utils.escape_html
- `skills/frontend/utilities.md` - flt, cint, datetime, format_currency

---

# Backend (Python)

- `skills/backend/controller_lifecycle.md` - Document lifecycle methods
- `skills/backend/save.md` - doc.save()
- `skills/backend/validation_patterns.md` - Validation patterns

---

# Database

- `skills/database/get_doc.md` - Get/create/delete documents
- `skills/database/get_value.md` - Get field values
- `skills/database/get_all.md` - Query multiple documents
- `skills/database/query_builder.md` - Advanced queries
- `skills/database/raw_sql.md` - Raw SQL queries
- `skills/database/db_transaction.md` - commit, rollback
- `skills/database/analyze_tables_and_processlist.md` - Tables/processlist; migrate blockers, KILL, re-run migrate

---

# API

- `skills/api/whitelist_basic.md` - Basic @frappe.whitelist()
- `skills/api/whitelist_advanced.md` - Advanced API patterns
- `skills/api/rest_resource.md` - GET/POST /api/resource/{DocType} CRUD

---

# System

- `skills/system/doc_events.md` - doc_events hook
- `skills/system/scheduler_events.md` - scheduler_events hook
- `skills/system/has_permission.md` - frappe.has_permission()
- `skills/system/permissions.md` - Permission checks before write/delete
- `skills/system/permission_query_conditions.md` - Row-level list filters in hooks
- `skills/system/clear_cache.md` - frappe.clear_cache()
- `skills/system/cache.md` - Cache invalidation scope
- `skills/system/enqueue.md` - frappe.enqueue()
- `skills/system/background_jobs.md` - Job patterns, idempotency
- `skills/system/fixtures_hook.md` - fixtures in hooks.py
- `skills/system/developer_mode.md` - set-config developer_mode, debug
- `skills/system/system_console.md` - System Console (safe_exec) vs bench execute
- `skills/system/websocket_pwa_fix.md` - WebSocket/PWA: apps.txt, gunicorn, nginx, redis_socketio

---

# Utils

- `skills/utils/date_utils.md` - getdate, add_days, formatdate
- `skills/utils/money_utils.md` - fmt_money, flt, cint
- `skills/utils/string_utils.md` - scrub, comma_or, get_link_to_form

---

# Naming & Mapping

- `skills/naming/naming_series.md` - Auto-generate document names
- `skills/mapping/get_mapped_doc.md` - Create document from another

---

# Email & Files

- `skills/email/send_email.md` - Send emails with attachments
- `skills/files/file_upload.md` - File upload and attachment
- `skills/files/pdf_generation.md` - Generate PDFs from HTML
- `skills/files/excel_utils.md` - Create and read Excel files

---

# Print & Reports

- `skills/print/print_format.md` - Jinja print formats
- `skills/print/wkhtmltopdf_print_format.md` - PDF margins, .print-format CSS
- `skills/reports/script_report.md` - Python-based reports
- `skills/reports/query_report.md` - SQL-based reports

---

# Web & Portal

- `skills/web/web_page.md` - Public web pages
- `skills/web/web_form.md` - Public forms

---

# Customization

- `skills/custom/create_custom_field.md` - create_custom_field()
- `skills/custom/client_script.md` - JavaScript via UI
- `skills/custom/server_script.md` - Python via UI
- `skills/custom/property_setter.md` - Property Setter (Customize Form)

---

# Migrations & Testing

- `skills/migrations/patch.md` - Database migrations
- `skills/migrations/export_fixtures.md` - bench export-fixtures
- `skills/testing/frappe_test_case.md` - FrappeTestCase
- `skills/testing/unit_test.md` - Unit tests, isolation

---

# ERPNext Specific

- `skills/erpnext/stock_ledger.md` - Stock ledger entries
- `skills/erpnext/gl_entry.md` - Accounting GL entries
- `skills/erpnext/base_controllers.md` - AccountsController, StockController, etc.

---

# Bench

- `skills/bench/new_site.md` - bench new-site
- `skills/bench/migrate.md` - bench migrate
- `skills/bench/backup.md` - bench backup
- `skills/bench/restore.md` - bench restore
- `skills/bench/run_tests.md` - bench run-tests

For more bench commands (use, install_app, doctor, mariadb, etc.) see `apps/skills/bench/` in the main project.
