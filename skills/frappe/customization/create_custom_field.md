# create_custom_field

Create a Custom Field through code or `bench execute` when the change should be reproducible.

## Python pattern

```python
from frappe.custom.doctype.custom_field.custom_field import create_custom_field

create_custom_field(
    "Shift Type",
    {
        "fieldname": "overtime_grace_period",
        "fieldtype": "Int",
        "label": "Overtime Grace (Minutes)",
        "insert_after": "early_exit_grace_period",
        "default": "60",
    },
)
```

## bench execute pattern

```bash
bench --site SITENAME execute "frappe.custom.doctype.custom_field.custom_field.create_custom_field" --args '["Shift Type", {"fieldname": "overtime_grace_period", "fieldtype": "Int", "label": "Overtime Grace (Minutes)", "insert_after": "early_exit_grace_period"}]'
```

## Before creating the field

```bash
bench --site SITENAME describe-database-table --doctype "Shift Type"
```

## Rules

- Prefer reproducible creation through code, patch, or bench command.
- Pick `insert_after` carefully to avoid messy layouts.
- Export fixtures if the custom field should ship with the app.

## Do not use for

- One-off manual experiments you do not want to keep
- Complex layout restructuring; use Customize Form or DocType layout tools
