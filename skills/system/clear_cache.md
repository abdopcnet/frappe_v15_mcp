# Cache

Use one cache clear call to invalidate stale values.

```python
frappe.clear_cache()
```

- Use after configuration or permission changes
- Clear specific scope when possible (`user`, `doctype`)
- Avoid unnecessary global cache clears
