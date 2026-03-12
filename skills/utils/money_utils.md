# money_utils

Numeric conversion and currency formatting.

```python
from frappe.utils import flt, cint, fmt_money
amount = flt(value, precision=2)
formatted = fmt_money(amount, currency=doc.currency)
```

Store numbers as numbers; format for display only.
