Fetch one or few fields; use for light queries. Single DocType: pass `filters=None`.

```python
last_login = frappe.db.get_value("User", "user@example.com", "last_login")
name, owner = frappe.db.get_value("Task", {"status": "Open"}, ["name", "owner"])
```
