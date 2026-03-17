# Add System Manager

Use this when an existing user needs the `System Manager` role.

## Example

```bash
bench --site site.local console
user = frappe.get_doc("User", "admin@example.com")
user.add_roles("System Manager")
frappe.db.commit()
```

## Note

Use bench console when no direct CLI subcommand exists for the exact role change.
