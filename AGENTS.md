# Rules

- **Investigate before coding** — understand and deep analysis first.
- **Comments** — English-only short comments above code sections.
- **follow frappe framework** — `frappe`.
- **When you follow this rules** — end your reply with ✅.

## Naming Conventions

- Python: `snake_case` for functions, variables
- JavaScript: `camelCase` for variables, `PascalCase` for classes
- DocType: Title Case with spaces
- Files: `snake_case.py`, `snake_case.js`

## Logging

- `skills/logging/frontend_logging.md`
- `skills/logging/log_error.md`

---

# API

- `skills/api/whitelist_basic.md` — @frappe.whitelist()
- `skills/api/whitelist_advanced.md` — allow_guest, permissions

---

# Backend

- `skills/backend/controller_lifecycle.md` — validate, on_submit, on_cancel
- `skills/backend/save.md` — doc.save()
- `skills/backend/validation_patterns.md` — frappe.throw

---

# Bench

- `skills/bench/add_database_index.md`
- `skills/bench/add_system_manager.md`
- `skills/bench/add_to_hosts.md`
- `skills/bench/add_user.md`
- `skills/bench/backup.md`
- `skills/bench/browse.md`
- `skills/bench/clear_log_table.md`
- `skills/bench/db_console.md`
- `skills/bench/describe_database_table.md`
- `skills/bench/destroy_all_sessions.md`
- `skills/bench/disable_user.md`
- `skills/bench/doctor.md`
- `skills/bench/drop_site.md`
- `skills/bench/export_csv.md`
- `skills/bench/generate_pot_file.md`
- `skills/bench/get_app.md`
- `skills/bench/install_app.md`
- `skills/bench/list_apps.md`
- `skills/bench/mariadb.md`
- `skills/bench/mariadb_query.md`
- `skills/bench/migrate.md`
- `skills/bench/new_site.md`
- `skills/bench/partial_restore.md`
- `skills/bench/postgres.md`
- `skills/bench/publish_realtime.md`
- `skills/bench/ready_for_migration.md`
- `skills/bench/reinstall.md`
- `skills/bench/remove_from_installed_apps.md`
- `skills/bench/restore.md`
- `skills/bench/run_tests.md`
- `skills/bench/set_admin_password.md`
- `skills/bench/set_last_active_for_user.md`
- `skills/bench/set_maintenance_mode.md`
- `skills/bench/set_password.md`
- `skills/bench/transform_database.md`
- `skills/bench/trigger_scheduler_event.md`
- `skills/bench/trim_database.md`
- `skills/bench/trim_tables.md`
- `skills/bench/uninstall_app.md`
- `skills/bench/use.md`
- `skills/bench/version.md`

---

# Custom

- `skills/custom/client_script.md` — Client Script DocType
- `skills/custom/create_custom_field.md` — create_custom_fields
- `skills/custom/property_setter.md` — Customize Form
- `skills/custom/server_script.md` — Server Script DocType

---

# Database

- `skills/database/analyze_tables_and_processlist.md` — Migrate blockers, KILL
- `skills/database/db_transaction.md` — commit, rollback
- `skills/database/get_all.md` — Multiple documents, filters, fields
- `skills/database/get_doc.md` — Load/create document; for_update
- `skills/database/get_value.md` — One or few fields; light queries
- `skills/database/query_builder.md` — QB API for complex queries
- `skills/database/raw_sql.md` — Raw SQL with safe binding

---

# Email

- `skills/email/send_email.md` — Email with attachments

---

# ERPNext

- `skills/erpnext/base_controllers.md` — StockController, AccountsController
- `skills/erpnext/gl_entry.md` — GL entries, make_gl_entries
- `skills/erpnext/stock_ledger.md` — Stock Ledger, make_sl_entries

---

# Files

- `skills/files/excel_utils.md` — make_xlsx
- `skills/files/file_upload.md` — File attach
- `skills/files/pdf_generation.md` — get_pdf

---

# Frontend

- `skills/frontend/api_calls.md` — frappe.call, frappe.xcall
- `skills/frontend/child_table.md` — Child table add/clear/events
- `skills/frontend/custom_buttons.md` — Toolbar, primary action
- `skills/frontend/dialogs.md` — msgprint, show_alert, escape_html
- `skills/frontend/field_properties.md` — Hide, enable, require
- `skills/frontend/form_events.md` — onload, refresh, validate, field events
- `skills/frontend/form_state.md` — is_new, is_dirty
- `skills/frontend/refresh_field.md` — Refresh dependent fields
- `skills/frontend/set_intro.md` — Intro message
- `skills/frontend/set_query.md` — Link field filters
- `skills/frontend/set_value.md` — Form field values
- `skills/frontend/utilities.md` — flt, cint, datetime

---

# GitHub

- `skills/github/bug_report_github_issue_template.md`

---

# Logging

- `skills/logging/frontend_logging.md` — Client logging
- `skills/logging/log_error.md` — Error log

---

# Mapping

- `skills/mapping/get_mapped_doc.md` — Document from document

---

# Migrations

- `skills/migrations/export_fixtures.md` — export-fixtures
- `skills/migrations/patch.md` — DB migrations

---

# Naming

- `skills/naming/naming_series.md` — Auto naming

---

# Print

- `skills/print/print_format.md` — Jinja print
- `skills/print/wkhtmltopdf_print_format.md` — PDF CSS

---

# Reports

- `skills/reports/query_report.md` — SQL report
- `skills/reports/script_report.md` — Python report

---

# System

- `skills/system/background_jobs.md` — Job patterns
- `skills/system/cache.md` — Cache scope
- `skills/system/clear_cache.md` — frappe.clear_cache
- `skills/system/doc_events.md` — doc_events in hooks
- `skills/system/enqueue.md` — Background jobs
- `skills/system/has_permission.md` — Permission checks
- `skills/system/hooks_doc_events.md`
- `skills/system/permissions.md` — Row-level permission
- `skills/system/scheduler_events.md` — cron, hourly, daily
- `skills/system/system_console.md` — Safe console vs bench execute
- `skills/system/websocket_pwa_fix.md` — WebSocket/PWA troubleshooting

---

# Testing

- `skills/testing/frappe_test_case.md` — FrappeTestCase
- `skills/testing/unit_test.md` — Unit tests

---

# Utils

- `skills/utils/date_utils.md` — getdate, add_days, formatdate
- `skills/utils/money_utils.md` — flt, cint, fmt_money
- `skills/utils/string_utils.md` — scrub, get_link_to_form

---

# Web

- `skills/web/web_form.md` — Public form
- `skills/web/web_page.md` — Public page
