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

- Frontend: `skills/frappe/frontend_logging.md`
- Backend: `skills/frappe/log_error.md`

---

# Database

- `skills/database/get_doc.md` - Load/create document; for_update
- `skills/database/get_value.md` - One or few fields; light queries
- `skills/database/get_all.md` - Multiple documents, filters, fields
- `skills/database/query_builder.md` - QB API for complex queries
- `skills/database/raw_sql.md` - Raw SQL with safe binding
- `skills/database/db_transaction.md` - commit, rollback
- `skills/database/analyze_tables_and_processlist.md` - Migrate blockers, KILL

---

# System

- `skills/system/doc_events.md` - doc_events in hooks
- `skills/system/scheduler_events.md` - cron, hourly, daily
- `skills/system/has_permission.md` - Permission checks
- `skills/system/permissions.md` - Row-level permission
- `skills/system/permission_query_conditions.md` - List filter in hooks
- `skills/system/clear_cache.md` - frappe.clear_cache
- `skills/system/cache.md` - Cache scope
- `skills/system/enqueue.md` - Background jobs
- `skills/system/background_jobs.md` - Job patterns
- `skills/system/fixtures_hook.md` - fixtures in hooks
- `skills/system/developer_mode.md` - set-config developer_mode
- `skills/system/system_console.md` - Safe console vs bench execute
- `skills/system/websocket_pwa_fix.md` - WebSocket/PWA troubleshooting

---

# Frappe

- `skills/frappe/set_value.md` - Form field values
- `skills/frappe/field_properties.md` - Hide, enable, require
- `skills/frappe/refresh_field.md` - Refresh dependent fields
- `skills/frappe/custom_buttons.md` - Toolbar, primary action
- `skills/frappe/set_intro.md` - Intro message
- `skills/frappe/form_state.md` - is_new, is_dirty
- `skills/frappe/form_events.md` - onload, refresh, validate, field events
- `skills/frappe/child_table.md` - Child table add/clear/events
- `skills/frappe/set_query.md` - Link field filters
- `skills/frappe/api_calls.md` - frappe.call, frappe.xcall
- `skills/frappe/dialogs.md` - msgprint, show_alert, escape_html
- `skills/frappe/utilities.md` - flt, cint, datetime
- `skills/frappe/controller_lifecycle.md` - validate, on_submit, on_cancel
- `skills/frappe/save.md` - doc.save()
- `skills/frappe/validation_patterns.md` - frappe.throw
- `skills/frappe/whitelist_basic.md` - @frappe.whitelist()
- `skills/frappe/whitelist_advanced.md` - allow_guest, permissions
- `skills/frappe/rest_resource.md` - /api/resource CRUD
- `skills/frappe/date_utils.md` - getdate, add_days, formatdate
- `skills/frappe/money_utils.md` - flt, cint, fmt_money
- `skills/frappe/string_utils.md` - scrub, get_link_to_form
- `skills/frappe/naming_series.md` - Auto naming
- `skills/frappe/get_mapped_doc.md` - Document from document
- `skills/frappe/send_email.md` - Email with attachments
- `skills/frappe/file_upload.md` - File attach
- `skills/frappe/pdf_generation.md` - get_pdf
- `skills/frappe/excel_utils.md` - make_xlsx
- `skills/frappe/print_format.md` - Jinja print
- `skills/frappe/wkhtmltopdf_print_format.md` - PDF CSS
- `skills/frappe/script_report.md` - Python report
- `skills/frappe/query_report.md` - SQL report
- `skills/frappe/web_page.md` - Public page
- `skills/frappe/web_form.md` - Public form
- `skills/frappe/create_custom_field.md` - create_custom_fields
- `skills/frappe/client_script.md` - Client Script DocType
- `skills/frappe/server_script.md` - Server Script DocType
- `skills/frappe/property_setter.md` - Customize Form
- `skills/frappe/patch.md` - DB migrations
- `skills/frappe/export_fixtures.md` - export-fixtures
- `skills/frappe/frappe_test_case.md` - FrappeTestCase
- `skills/frappe/unit_test.md` - Unit tests
- `skills/frappe/bench_commands.md` - new-site, migrate, backup, run-tests
- `skills/frappe/log_error.md` - Error log
- `skills/frappe/frontend_logging.md` - Client logging

---

# ERPNext

- `skills/erpnext/stock_ledger.md` - Stock Ledger, make_sl_entries
- `skills/erpnext/gl_entry.md` - GL entries, make_gl_entries
- `skills/erpnext/base_controllers.md` - StockController, AccountsController
