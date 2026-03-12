# doc_events

Bind DocType event in hooks.py.

```python
doc_events = { "Sales Order": { "validate": "my_app.events.sales_order_validate" } }
```

Handler must be importable. Keep handlers small.
