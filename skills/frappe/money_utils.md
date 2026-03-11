Format and parse numbers: flt, cint, fmt_money.

```python
from frappe.utils import flt, cint
amount = flt(doc.grand_total, 2)
qty = cint(doc.qty)
```
