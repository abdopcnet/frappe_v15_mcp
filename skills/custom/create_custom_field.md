# create-custom-field

Create a Custom Field with a **direct command** (no Python file). Uses Frappe’s `create_custom_field` and `bench execute`.

## 1. (Optional) Query custom fields and inspect target DocType

**List custom fields (e.g. by doctype, or with is_system_generated):**

```bash
bench --site <site> mariadb -e "SELECT dt, fieldname, is_system_generated FROM \`tabCustom Field\` WHERE is_system_generated = 1 AND dt IN ('Salary Slip', 'Payroll Settings', 'Salary Component') ORDER BY dt, fieldname;"
```

Adjust the `WHERE` clause (e.g. remove `is_system_generated` or change `dt IN (...)`) as needed. Use backticks around table name if it contains spaces.

To choose where to insert the new field (`insert_after`):

```bash
bench --site <site> describe-database-table --doctype "Custom Field"
```

To see the target DocType’s fields (e.g. to pick `insert_after`):

```bash
bench --site <site> describe-database-table --doctype "Shift Type"
```

(Or open the form in the UI and note the field after which you want the new one.)

## 2. Create the field with one command

**Direct command (no .py file):**

```bash
bench --site <site> execute "frappe.custom.doctype.custom_field.custom_field.create_custom_field" --args '["<DocType>", {"fieldname": "<fieldname>", "fieldtype": "<Field Type>", "label": "<Label>", "insert_after": "<insert_after>"}]'
```

**Example — add “Overtime Grace (Minutes)” to Shift Type:**

```bash
bench --site normarch execute "frappe.custom.doctype.custom_field.custom_field.create_custom_field" --args '["Shift Type", {"fieldname": "overtime_grace_period", "fieldtype": "Int", "label": "Overtime Grace (Minutes)", "insert_after": "early_exit_grace_period", "default": "60"}]'
```

Replace `<site>`, `<DocType>`, `fieldname`, `fieldtype`, `label`, `insert_after` (and optional `default`, `description`, etc.) as needed. No Python file is used; the callable is `create_custom_field(doctype, df)` from `frappe.custom.doctype.custom_field.custom_field`.

**Example — one more field on Payroll Settings:**

```bash
bench --site normarch execute "frappe.custom.doctype.custom_field.custom_field.create_custom_field" --args '["Payroll Settings", {"fieldname": "default_overtime_grace_period", "fieldtype": "Int", "label": "Default Overtime Grace (Minutes)", "insert_after": "default_work_on_holiday_component", "default": "60"}]'
```

## 3. Alternative: UI (no command)

If the DocType allows Customize: **Customize Form** → select DocType → add field → set Label, Fieldname, Field Type, Insert After, Default → Save.

## 4. Schema reference

Custom Field table columns:

```bash
bench --site <site> describe-database-table --doctype "Custom Field"
```

Common properties: `dt`, `fieldname`, `label`, `fieldtype`, `insert_after`, `default`, `description`, `reqd`, `read_only`.
