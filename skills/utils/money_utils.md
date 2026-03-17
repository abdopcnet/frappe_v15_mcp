# Money Utils

Use this when formatting or normalizing numeric values in Frappe.

## Normalize numeric input

```python
from frappe.utils import cint, flt

qty = cint(doc.qty)
rate = flt(doc.rate, precision=2)
amount = qty * rate
```

## Format currency for display

```python
from frappe.utils import fmt_money

label = fmt_money(doc.grand_total, currency=doc.currency)
```

## Pick the right file

- Use this file for numeric and currency helpers.
- Use `date_utils.md` for dates.
