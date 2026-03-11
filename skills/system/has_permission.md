Check permission before sensitive operations; pass doc for document-level rules.

```python
if not frappe.has_permission("Sales Order", "write", doc=doc):
    frappe.throw("Not permitted")
```
