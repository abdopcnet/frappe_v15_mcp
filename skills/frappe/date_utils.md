Use getdate, add_days, formatdate for date handling.

```python
from frappe.utils import getdate, add_days, formatdate
d = getdate("2024-01-15")
later = add_days(d, 7)
formatdate(d, "dd-MM-yyyy")
```
