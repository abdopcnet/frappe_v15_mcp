# server_script

DocType Event Server Script from UI: pick DocType, Event (e.g. Before Save), write Python.

```python
if doc.grand_total <= 0:
    frappe.throw("Grand Total must be greater than zero")
```

Keep logic small. Use app code for complex logic.
