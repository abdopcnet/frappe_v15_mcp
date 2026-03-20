# AccountsController

Use this when creating a custom DocType that needs GL entries, currency handling,
taxes, or payment terms — the patterns from ERPNext's AccountsController.

## Inherit AccountsController

```python
from erpnext.controllers.accounts_controller import AccountsController

class MyBillingDoc(AccountsController):
    def validate(self):
        super().validate()
        self.validate_mandatory_fields()

    def on_submit(self):
        self.make_gl_entries()

    def on_cancel(self):
        self.ignore_linked_doctypes = ("GL Entry", "Stock Ledger Entry")
        make_reverse_gl_entries(voucher_type=self.doctype, voucher_no=self.name)

    def make_gl_entries(self, cancel=False):
        from erpnext.accounts.general_ledger import make_gl_entries

        gl_entries = self.get_gl_entries()
        make_gl_entries(gl_entries, cancel=cancel)

    def get_gl_entries(self):
        return [
            self.get_gl_dict(
                {
                    "account": self.debit_account,
                    "debit": self.total_amount,
                    "credit": 0,
                    "debit_in_account_currency": self.total_amount,
                    "credit_in_account_currency": 0,
                    "party_type": "Customer",
                    "party": self.customer,
                }
            ),
            self.get_gl_dict(
                {
                    "account": self.credit_account,
                    "debit": 0,
                    "credit": self.total_amount,
                    "debit_in_account_currency": 0,
                    "credit_in_account_currency": self.total_amount,
                }
            ),
        ]
```

## Useful AccountsController methods

```python
self.set_missing_values()               # posting_date, currency, exchange_rate
self.validate_currency()                # ensure accounts match doc currency
self.validate_payment_terms_amount()    # payment terms vs grand_total
self.calculate_taxes_and_totals()       # calls TaxesAndTotals mixin
self.get_gl_dict(fields, account_currency=None, item=None)
```

## ignore_linked_doctypes on cancel

```python
def on_cancel(self):
    self.ignore_linked_doctypes = ("GL Entry",)
    make_reverse_gl_entries(voucher_type=self.doctype, voucher_no=self.name)
```

Without `ignore_linked_doctypes`, Frappe will block cancellation if GL entries exist.

## Rules

- Call `super().validate()` unless you are certain you want to skip base checks.
- Always balance debits and credits within one voucher.
- Use `get_gl_dict()` to auto-fill `posting_date`, `voucher_type`, `voucher_no`, `company`.
- On cancel, use `make_reverse_gl_entries` — never manually delete GL entries.

## Pick the right file

- Use `gl_entry.md` for the dict shape and raw `make_gl_entries` usage.
- Use `base_controllers.md` for the full ERPNext controller hierarchy.
- Use `journal_entry.md` for creating Journal Entry documents.
