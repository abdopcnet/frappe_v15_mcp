# server_script

Use Server Script for small server-side automation configured from the UI.

## DocType event script

```python
if doc.grand_total <= 0:
    frappe.throw("Grand Total must be greater than zero")
```

## API-type script

```python
frappe.response["message"] = {
    "user": frappe.session.user,
    "timestamp": frappe.utils.now(),
}
```

## Rules

- Keep Server Scripts short and site-specific.
- Use them for lightweight automation, not app architecture.
- Move complex or reusable logic into a real app module.

## Do not use for

- Long workflows spanning many modules
- Code that needs version-controlled testing and reuse across sites
