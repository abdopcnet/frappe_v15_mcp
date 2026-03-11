Register DocType event handlers in hooks.py. Handler path must be importable.

```python
# hooks.py
doc_events = {
    "Sales Order": {
        "validate": "my_app.events.validate_sales_order",
        "on_submit": "my_app.events.on_submit_so",
    }
}
```
