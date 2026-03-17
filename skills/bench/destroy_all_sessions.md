# Destroy All Sessions

Use this when forcing all users to log in again.

## Example

```bash
bench --site site.local console
frappe.db.delete("Sessions")
frappe.cache.flushall()
frappe.db.commit()
```

## Note

This is disruptive. Use only for security or auth-reset cases.
