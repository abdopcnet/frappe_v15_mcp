# Web Page

Use this when the route is backed by a Python context builder.

## Build page context

```python
import frappe

def get_context(context):
    context.no_cache = 1
    context.orders = frappe.get_all(
        "Sales Order",
        filters={"customer": frappe.session.user},
        fields=["name", "transaction_date", "grand_total"],
        order_by="transaction_date desc",
    )
```

## Pick the right file

- Use this file for route-specific Python context.
- Use `web_template.md` for reusable website building blocks.
