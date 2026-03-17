# Add User

Use this when you need to create a Desk user quickly from bench console.

## Example

```bash
bench --site site.local console
frappe.get_doc({
    "doctype": "User",
    "email": "user@example.com",
    "first_name": "Desk",
    "send_welcome_email": 0,
}).insert(ignore_permissions=True)
frappe.db.commit()
```
