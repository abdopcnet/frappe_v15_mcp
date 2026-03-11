# string_utils

Normalize and format strings.

```python
from frappe.utils import scrub, unscrub, get_link_to_form, comma_or
fieldname = scrub("Item Code")  # item_code
link = get_link_to_form("Customer", doc.customer)
text = comma_or(["A", "B"])  # "A or B"
```

Use scrub for keys; get_link_to_form for doc links.
