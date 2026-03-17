# doc_events

Bind DocType events in `hooks.py` when logic should live outside the controller class.

## Basic mapping

```python
doc_events = {
    "Sales Order": {
        "validate": "my_app.events.sales_order_validate",
        "on_submit": "my_app.events.sales_order_on_submit",
    }
}
```

## Wildcard mapping

```python
doc_events = {
    "*": {
        "on_update": "my_app.audit.log_doc_update",
    }
}
```

## Handler signature

```python
def sales_order_validate(doc, method=None):
    if not doc.customer:
        frappe.throw("Customer is required")
```

## Rules

- Use importable dotted paths only.
- Keep handlers small and delegate to service functions when needed.
- Use this when the behavior belongs to the app layer, not the DocType class itself.

## Do not use for

- Controller-local business rules that belong inside the DocType class
- Frontend form events
