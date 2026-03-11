Create custom field programmatically (e.g. in patch or setup).

```python
from frappe.custom.doctype.custom_field.custom_field import create_custom_fields
create_custom_fields({"Task": [{"fieldname": "my_field", "label": "My Field", "fieldtype": "Data"}]})
```
