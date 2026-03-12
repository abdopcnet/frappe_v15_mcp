# Raw SQL

Use one raw SQL query only when ORM or query builder cannot cover the case.

```python
rows = frappe.db.sql("SELECT name FROM `tabItem` WHERE disabled = 0 LIMIT 20", as_dict=True)
```

- Parameterize dynamic values
- Keep queries read-only when possible
- Document why raw SQL is required
