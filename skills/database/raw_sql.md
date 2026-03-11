Use raw SQL only when needed; bind values to avoid injection.

```python
frappe.db.sql("SELECT name FROM tabTask WHERE status = %(status)s", {"status": "Open"})
frappe.db.sql("UPDATE tabTask SET status = %s WHERE name = %s", ("Closed", "TASK-001"))
```
