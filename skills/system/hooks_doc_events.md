# hooks_doc_events

Same as doc_events: bind DocType event in hooks.py.

```python
doc_events = { "Sales Order": { "validate": "my_app.events.sales_order_validate" } }
```

Handler path must be importable. Keep handlers small.
