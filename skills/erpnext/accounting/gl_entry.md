# GL Entry

Use this when the question is about posting or reading accounting ledger entries.

## Required dict shape

```python
{
    "doctype": "GL Entry",
    "posting_date": doc.posting_date,
    "account": "Debtors - TC",          # account name with company abbreviation
    "party_type": "Customer",           # Customer | Supplier | Employee | None
    "party": doc.customer,
    "debit": doc.grand_total,
    "credit": 0,
    "debit_in_account_currency": doc.grand_total,
    "credit_in_account_currency": 0,
    "voucher_type": doc.doctype,
    "voucher_no": doc.name,
    "cost_center": doc.cost_center,
    "company": doc.company,
    "is_opening": "No",
    "project": doc.get("project"),
    "remarks": doc.get("remarks") or "No Remarks",
}
```

## Post entries via make_gl_entries

```python
from erpnext.accounts.general_ledger import make_gl_entries

def make_gl_entries(self):
    gl_entries = [
        self.get_gl_dict(
            {
                "account": self.debit_to,
                "party_type": "Customer",
                "party": self.customer,
                "debit": self.grand_total,
                "credit": 0,
                "debit_in_account_currency": self.grand_total,
                "credit_in_account_currency": 0,
            },
            self.party_account_currency,
        ),
        self.get_gl_dict(
            {
                "account": self.income_account,
                "debit": 0,
                "credit": self.net_total,
                "debit_in_account_currency": 0,
                "credit_in_account_currency": self.net_total,
            }
        ),
    ]
    make_gl_entries(gl_entries, cancel=self.docstatus == 2)
```

## get_gl_dict helper (preferred)

`get_gl_dict()` is available on `AccountsController` and automatically fills
`posting_date`, `voucher_type`, `voucher_no`, `company`, `remarks`.

```python
# Inside an AccountsController subclass:
gl = self.get_gl_dict(
    {
        "account": self.account,
        "debit": self.amount,
        "credit": 0,
        "debit_in_account_currency": self.amount,
        "credit_in_account_currency": 0,
    },
    item=self,  # optional, for cost centre / project from item row
)
```

## Reverse entries on cancel

```python
from erpnext.accounts.general_ledger import make_reverse_gl_entries

def on_cancel(self):
    make_reverse_gl_entries(voucher_type=self.doctype, voucher_no=self.name)
```

## Read GL entries

```python
rows = frappe.get_all(
    "GL Entry",
    filters={"voucher_no": doc.name, "is_cancelled": 0},
    fields=["account", "party", "debit", "credit", "posting_date"],
    order_by="creation asc",
)
```

## Rules

- Debit and credit in the same entry must be in the correct account currency.
- Always include both `debit/credit` and `debit_in_account_currency/credit_in_account_currency`.
- Use `make_reverse_gl_entries` on cancel instead of manual cancel logic.
- Every entry pair in a voucher must balance (total debit == total credit).

## Pick the right file

- Use `accounts_controller.md` for the full AccountsController GL flow.
- Use `journal_entry.md` for creating Journal Entry documents.
- Use `stock_ledger.md` for inventory movement.
