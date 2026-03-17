# Date Utils

Use this when the task is simple date arithmetic or formatting in Frappe.

## Common date helpers

```python
from frappe.utils import add_days, formatdate, getdate, nowdate, today

start_date = getdate(doc.transaction_date)
due_date = add_days(start_date, 30)
label = formatdate(due_date)
current_day = today()
```

## Compare with today's date

```python
if getdate(doc.due_date) < getdate(nowdate()):
    frappe.throw("Document is overdue")
```

## Pick the right file

- Use this file for date utilities.
- Use `money_utils.md` or `string_utils.md` for non-date helpers.
