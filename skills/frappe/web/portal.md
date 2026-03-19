# Portal

Use this when the question is about website access for logged-in portal users.

## Add a portal menu item

```python
portal_menu_items = [
    {"title": "My Orders", "route": "/orders", "reference_doctype": "Sales Order", "role": "Customer"}
]
```

## Restrict website access

```python
def has_website_permission(doc, ptype, user, verbose=False):
    return user == doc.owner or "Website Manager" in frappe.get_roles(user)
```

## Pick the right file

- Use this file for portal user access and website permission patterns.
- Use `web_page.md` for route-backed pages.
- Use `web_form.md` for public or portal-facing forms.
