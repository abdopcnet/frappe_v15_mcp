Create a new document from another with field and child table mapping.

```python
from frappe.model.mapper import get_mapped_doc
target = get_mapped_doc("Sales Order", so_name, {"Sales Order": {"doctype": "Delivery Note"}}, postprocess=postprocess)
target.insert()
```
