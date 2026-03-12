# get_mapped_doc

Create a document from another (e.g. Sales Order → Sales Invoice).

```python
from frappe.model.mapper import get_mapped_doc
doc = get_mapped_doc("Sales Order", source_name, {
    "Sales Order": {"doctype": "Sales Invoice", "validation": {"docstatus": ["=", 1]}},
    "Sales Order Item": {"doctype": "Sales Invoice Item"}
})
```

Use `field_map` and `field_no_map` when needed. Validate permissions.
