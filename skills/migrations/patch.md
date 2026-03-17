# patch

Write idempotent migration logic inside a patch `execute()` function.

## Basic patch

```python
def execute():
    if not frappe.db.exists("Custom Field", "Item-brand_code"):
        frappe.reload_doc("custom", "doctype", "custom_field")
```

## Rules

- Make every patch idempotent.
- Keep it deterministic and short.
- Add patches to `patches.txt` in execution order.
