# hooks_doc_events

Choose `hooks.py` `doc_events` when you need cross-app wiring instead of editing the DocType controller.

## Prefer `doc_events` when

- You are extending a standard DocType from a custom app
- You cannot or should not override the controller class
- You need app-level wiring for audit, notifications, or integration hooks

## Example

```python
doc_events = {
    "Purchase Invoice": {
        "on_submit": "my_app.integrations.sync_purchase_invoice",
    }
}
```

```python
def sync_purchase_invoice(doc, method=None):
    enqueue_sync(doc.name)
```

## Boundary vs controller hooks

- `controller_lifecycle.md` owns in-class hooks such as `validate()` and `on_submit()`.
- `doc_events.md` owns the actual `hooks.py` mapping syntax.
- This file owns the decision rule: when to wire behavior through hooks instead of editing the controller.

## Do not use for

- Repeating the full lifecycle order
- Explaining frontend `frappe.ui.form.on` events
