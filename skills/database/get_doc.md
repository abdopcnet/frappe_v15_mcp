# get_doc

Use one `frappe.get_doc` call to load a full document object.

```python
doc = frappe.get_doc("Sales Invoice", "ACC-SINV-2026-00001")
```

- Use when child tables are needed
- Handle missing docs with exceptions
- Use `for_update=True` when locking is required
