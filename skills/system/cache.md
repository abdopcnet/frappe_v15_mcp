Clear cache after config or permission changes; use user/doctype scope when possible.

```python
frappe.cache().delete_value("my_key")
frappe.clear_cache(user="user@example.com")
```
