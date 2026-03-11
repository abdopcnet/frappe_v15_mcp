# Patch

Use one patch function to run controlled schema or data migration logic.

```python
def execute():
    if not frappe.db.exists("Custom Field", "Item-brand_code"):
        frappe.reload_doc("custom", "doctype", "custom_field")
```

- Make patches idempotent
- Keep patches short and deterministic
- Add patches to `patches.txt` in order
