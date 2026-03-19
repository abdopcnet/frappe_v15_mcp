# Remove From Installed Apps

Use this when bench metadata must be corrected before or after uninstall troubleshooting.

## Example

```bash
bench --site site.local console
apps = frappe.get_installed_apps()
apps.remove("my_app")
frappe.db.set_single_value("Installed Applications", "installed_apps", "\n".join(apps))
frappe.db.commit()
```

## Note

Prefer `uninstall-app` when possible. Manual removal is a repair path.
