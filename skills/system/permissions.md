Check permission before write/delete; use has_permission with doc= for row-level.

```python
frappe.has_permission("Task", "read")
frappe.has_permission("Task", "write", doc=doc)
```
