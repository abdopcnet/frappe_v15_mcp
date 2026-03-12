# Query Builder

Use one query builder statement for safe composable SQL generation.

```python
User = frappe.qb.DocType("User")
rows = frappe.qb.from_(User).select(User.name).where(User.enabled == 1).run(as_dict=True)
```

- Prefer query builder over raw SQL
- Keep filters explicit and indexed
- Use `as_dict=True` for readability
