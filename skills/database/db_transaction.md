Use commit/rollback only when managing transactions outside standard save.

```python
try:
    frappe.db.commit()
except Exception:
    frappe.db.rollback()
    raise
```
