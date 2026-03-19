# get_mapped_doc

Map one source document into another target document.

## Basic mapping

```python
from frappe.model.mapper import get_mapped_doc

doc = get_mapped_doc(
    "Sales Order",
    source_name,
    {
        "Sales Order": {"doctype": "Sales Invoice", "validation": {"docstatus": ["=", 1]}},
        "Sales Order Item": {"doctype": "Sales Invoice Item"},
    },
)
```

## Rules

- Validate source docstatus and business state before mapping.
- Use `field_map` or `field_no_map` when defaults are not enough.
- Keep mapping logic close to the target creation flow.
