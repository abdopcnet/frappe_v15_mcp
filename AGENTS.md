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

- `skills/frappe/api/` — `whitelist_basic.md`, `whitelist_advanced.md`
- `skills/frappe/auth/` — `authentication.md`, `session_management.md`
- `skills/frappe/backend/` — `controller_lifecycle.md`, `save.md`, `validation_patterns.md`, `autoname.md`
- `skills/frappe/customization/` — `create_custom_field.md`, `property_setter.md`, `client_script.md`, `server_script.md`, `doctype_layout.md`
- `skills/frappe/data/` — `get_doc.md`, `get_list.md`, `get_all.md`, `get_value.md`, `get_single.md`, `query_builder.md`, `raw_sql.md`, `db_transaction.md`, `delete_doc.md`, `analyze_tables_and_processlist.md`
- `skills/frappe/email/` — `send_email.md`, `email_account.md`
- `skills/frappe/files/` — `file_upload.md`, `pdf_generation.md`, `excel_utils.md`
- `skills/frappe/frontend/` — `form_events.md`, `set_value.md`, `set_query.md`, `refresh_field.md`, `field_properties.md`, `form_state.md`, `child_table.md`, `custom_buttons.md`, `dialogs.md`, `api_calls.md`, `listview_customization.md`, `set_intro.md`, `utilities.md`
- `skills/frappe/integrations/` — `rest_api.md`, `webhooks.md`, `oauth_social_login.md`
- `skills/frappe/logging/` — `log_error.md`, `frontend_logging.md`
- `skills/frappe/mapping/` — `get_mapped_doc.md`
- `skills/frappe/migrations/` — `patch.md`, `export_fixtures.md`
- `skills/frappe/naming/` — `naming_series.md`
- `skills/frappe/notifications/` — `notification_config.md`, `email_template.md`, `email_queue.md`
- `skills/frappe/print/` — `print_format.md`, `wkhtmltopdf_print_format.md`
- `skills/frappe/realtime/` — `socketio_basics.md`, `task_progress.md`
- `skills/frappe/reports/` — `script_report.md`, `query_report.md`
- `skills/frappe/security/` — `safe_execution.md`, `document_sharing.md`
- `skills/frappe/system/` — `app_hooks.md`, `doc_events.md`, `hooks_doc_events.md`, `scheduler_events.md`, `enqueue.md`, `background_jobs.md`, `permissions.md`, `has_permission.md`, `cache.md`, `clear_cache.md`, `system_console.md`, `websocket_pwa_fix.md`
- `skills/frappe/testing/` — `unit_test.md`, `frappe_test_case.md`
- `skills/frappe/translations/` — `translation_basics.md`, `manage_translations.md`
- `skills/frappe/utils/` — `date_utils.md`, `money_utils.md`, `string_utils.md`
- `skills/frappe/web/` — `web_page.md`, `web_form.md`, `web_template.md`, `portal.md`
- `skills/frappe/workflow/` — `workflow_basics.md`, `workflow_transitions.md`

### ERPNext patterns

- `skills/erpnext/controllers/` — `base_controllers.md`, `buying_controller.md`
- `skills/erpnext/accounting/` — `gl_entry.md`, `accounts_controller.md`, `journal_entry.md`, `payment_entry.md`
- `skills/erpnext/stock/` — `stock_ledger.md`, `stock_entry.md`

### Ops

- `skills/ops/bench/` - bench CLI commands and site operations (41 files).
- `skills/ops/github/` - GitHub issue/report template guidance.

## Path format

- Use paths relative to the repository root, for example: `skills/frappe/data/get_doc.md`.

## Maintenance Notes

- If a skill file is added/removed/renamed, update this file to match the new structure.
- Prefer category paths over listing exact filenames here unless the name matters.
