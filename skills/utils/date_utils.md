# date_utils

Date helpers: get, add, format, diff.

```python
from frappe.utils import getdate, nowdate, today, add_days, add_months, formatdate
date = getdate(); date = today(); date = add_days(getdate(), 7)
formatted = formatdate(date)
```

Use getdate() for parsing; format only at output.
