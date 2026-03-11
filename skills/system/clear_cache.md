Invalidate cache after metadata or config changes. Prefer scoped clear when possible.

```python
frappe.clear_cache()
frappe.clear_cache(doctype="Sales Order")
```
