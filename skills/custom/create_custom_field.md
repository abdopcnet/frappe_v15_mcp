# create_custom_field

Create Custom Field from code.

```python
from frappe.custom.doctype.custom_field.custom_field import create_custom_field
create_custom_field("Sales Invoice", {"fieldname": "custom_field", "fieldtype": "Data", "label": "Custom Field", "insert_after": "customer_name"})
```

Keep fieldname unique. Export as fixture for deploy.
