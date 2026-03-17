# Clear Log Table

Use this when log tables have grown too large and you need targeted cleanup.

## Example

```bash
bench --site site.local console
frappe.db.delete("Error Log", {"modified": ("<", "2024-01-01")})
frappe.db.commit()
```

## Note

Delete old logs selectively. Avoid wiping useful recent diagnostics.
