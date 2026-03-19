# String Utils

Use this when the question is about common Frappe string helpers.

## Common helpers

```python
from frappe.utils import comma_and, get_link_to_form
from frappe.model.naming import make_autoname
from frappe.utils.data import scrub, unscrub

route_name = scrub("Sales Order Item")
label = unscrub("sales_order_item")
link = get_link_to_form("Customer", customer_name)
series_name = make_autoname("CUST-.YYYY.-.#####")
text = comma_and(["Email", "Phone", "Address"])
```

## Pick the right file

- Use this file for string transformation and link helpers.
- Use `naming_series.md` for naming-series behavior itself.
