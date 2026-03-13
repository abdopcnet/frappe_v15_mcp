# Rules

- **Investigate before coding** — understand and analyze first.
- **Frappe/ERPNext** — follow their standards; English-only short comments above code.
- Reply in English Only, end your response with ✅.


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
- `skills/frontend/dialogs.md` - msgprint, show_alert, confirm; HTML in message use frappe.utils.escape_html
- `skills/frontend/utilities.md` - flt, cint, datetime, format_currency

---

# Backend (Python)

- `skills/backend/controller_lifecycle.md` - Document lifecycle methods
- `skills/backend/save.md` - `doc.save()`
- `skills/backend/validation_patterns.md` - Validation patterns

---

# Database

- `skills/database/get_doc.md` - Get/create/delete documents
- `skills/database/get_value.md` - Get field values
- `skills/database/get_all.md` - Query multiple documents
- `skills/database/query_builder.md` - Advanced queries
- `skills/database/raw_sql.md` - Raw SQL queries
- `skills/database/analyze_tables_and_processlist.md` - Analyze tables/columns and processlist; find what blocks migrate, KILL blocker, re-run migrate

---

# API

- `skills/api/whitelist_basic.md` - Basic @frappe.whitelist()
- `skills/api/whitelist_advanced.md` - Advanced API patterns

---

# System

- `skills/system/doc_events.md` - `doc_events` hook
- `skills/system/scheduler_events.md` - `scheduler_events` hook
- `skills/system/has_permission.md` - `frappe.has_permission()`
- `skills/system/clear_cache.md` - `frappe.clear_cache()`
- `skills/system/enqueue.md` - `frappe.enqueue()`
- `skills/system/system_console.md` - System Console (safe_exec) vs bench execute
- `skills/system/websocket_pwa_fix.md` - WebSocket/PWA/realtime fix: apps.txt order, gunicorn restart, nginx keepalive/ws headers, redis_socketio, Cloudflare

---

# Utils

- `skills/utils/date_utils.md` - Date operations (getdate, add_days, formatdate)
- `skills/utils/money_utils.md` - Currency formatting (fmt_money, flt, cint)
- `skills/utils/string_utils.md` - String operations (scrub, comma_or, get_link_to_form)

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
- `skills/reports/script_report.md` - Python-based reports
- `skills/reports/query_report.md` - SQL-based reports

---

# Web & Portal

- `skills/web/web_page.md` - Public web pages
- `skills/web/web_form.md` - Public forms

---

# Customization

- `skills/custom/create_custom_field.md` - `create_custom_field()`
- `skills/custom/client_script.md` - JavaScript via UI
- `skills/custom/server_script.md` - Python via UI
- `skills/custom/property_setter.md` - Property Setter (Customize Form, document fields)

---

# Migrations & Testing

- `skills/migrations/patch.md` - Database migrations
- `skills/migrations/export_fixtures.md` - `bench export-fixtures`
- `skills/testing/frappe_test_case.md` - `FrappeTestCase`

---

# ERPNext Specific

- `skills/erpnext/stock_ledger.md` - Stock ledger entries
- `skills/erpnext/gl_entry.md` - Accounting GL entries
- `skills/erpnext/base_controllers.md` - AccountsController, StockController, etc.

---

# GitHub

- `skills/github/bug_report_github_issue_template.md` - ERPNext bug report template for GitHub issues

---

# Bench

- `skills/bench/new_site.md` - `bench new-site`
- `skills/bench/drop_site.md` - `bench drop-site`
- `skills/bench/use.md` - `bench use`
- `skills/bench/reinstall.md` - `bench reinstall`
- `skills/bench/install_app.md` - `bench install-app`
- `skills/bench/get_app.md` - `bench get-app`
- `skills/bench/uninstall_app.md` - `bench uninstall-app`
- `skills/bench/list_apps.md` - `bench list-apps`
- `skills/bench/remove_from_installed_apps.md` - `bench remove-from-installed-apps`
- `skills/bench/add_system_manager.md` - `bench add-system-manager`
- `skills/bench/add_user.md` - `bench add-user`
- `skills/bench/disable_user.md` - `bench disable-user`
- `skills/bench/set_password.md` - `bench set-password`
- `skills/bench/set_admin_password.md` - `bench set-admin-password`
- `skills/bench/set_last_active_for_user.md` - `bench set-last-active-for-user`
- `skills/bench/add_to_hosts.md` - `bench add-to-hosts`
- `skills/bench/browse.md` - `bench browse`
- `skills/bench/publish_realtime.md` - `bench publish-realtime`
- `skills/bench/set_maintenance_mode.md` - `bench set-maintenance-mode`
- `skills/bench/doctor.md` - `bench doctor`
- `skills/bench/ready_for_migration.md` - `bench ready-for-migration`
- `skills/bench/destroy_all_sessions.md` - `bench destroy-all-sessions`
- `skills/bench/backup.md` - `bench backup`
- `skills/bench/restore.md` - `bench restore`
- `skills/bench/partial_restore.md` - `bench partial-restore`
- `skills/bench/mariadb.md` - `bench mariadb`
- `skills/bench/postgres.md` - `bench postgres`
- `skills/bench/db_console.md` - `bench db-console`
- `skills/bench/add_database_index.md` - `bench add-database-index`
- `skills/bench/describe_database_table.md` - `bench describe-database-table`
- `skills/bench/transform_database.md` - `bench transform-database`
- `skills/bench/trim_database.md` - `bench trim-database`
- `skills/bench/trim_tables.md` - `bench trim-tables`
- `skills/bench/clear_log_table.md` - `bench clear-log-table`
- `skills/bench/migrate.md` - `bench migrate`
- `skills/bench/trigger_scheduler_event.md` - `bench trigger-scheduler-event`
- `skills/bench/run_tests.md` - `bench run-tests`
- `skills/bench/generate_pot_file.md` - `bench generate-pot-file`
- `skills/bench/export_csv.md` - `bench export-csv`
- `skills/bench/mariadb_query.md` - `bench mariadb -e`
- `skills/bench/version.md` - `bench version`
