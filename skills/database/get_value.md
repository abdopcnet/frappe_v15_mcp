# get_value

Use one `frappe.db.get_value` call to fetch a single field quickly.

```python
email = frappe.db.get_value("User", "Administrator", "email")
```

- Fast for single-value lookups
- Avoid full document load when unnecessary
- Use filters for dynamic lookups
