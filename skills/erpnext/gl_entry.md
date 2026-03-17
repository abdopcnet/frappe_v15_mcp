# GL Entry

Use this when the question is about posting or reading accounting ledger entries.

## Create GL map and post entries

```python
from erpnext.accounts.general_ledger import make_gl_entries

gl_entries = [
    {
        "account": "Debtors - TC",
        "party_type": "Customer",
        "party": doc.customer,
        "debit": doc.grand_total,
        "credit": 0,
    },
    {
        "account": "Sales - TC",
        "debit": 0,
        "credit": doc.net_total,
    },
]

make_gl_entries(gl_entries, cancel=0, adv_adj=0)
```

## Read GL entries

```python
rows = frappe.get_all(
    "GL Entry",
    filters={"voucher_no": doc.name},
    fields=["account", "debit", "credit"],
)
```

## Pick the right file

- Use this file for accounting ledger patterns.
- Use `stock_ledger.md` for inventory movement.
