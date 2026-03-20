# ERPNext Base Controllers

Use this when extending ERPNext transactional DocTypes that rely on the built-in controller hierarchy.

## Controller hierarchy

```text
Document (frappe)
└── TransactionController
    ├── AccountsController
    │   ├── BuyingController
    │   │   └── PurchaseController  (Purchase Order, Purchase Invoice, ...)
    │   └── SellingController
    │       └── SalesController     (Sales Order, Sales Invoice, ...)
    └── StockController             (Delivery Note, Stock Entry, ...)
```

## Extend SellingController

```python
from erpnext.controllers.selling_controller import SellingController

class MyQuotation(SellingController):
    def validate(self):
        super().validate()          # runs taxes, totals, terms
        self.validate_items()

    def validate_items(self):
        for row in self.items:
            if row.qty <= 0:
                frappe.throw(f"Row {row.idx}: qty must be > 0")
```

## Extend BuyingController

```python
from erpnext.controllers.buying_controller import BuyingController

class MyPurchaseRequest(BuyingController):
    def validate(self):
        super().validate()
        self.set_missing_item_details()
```

## Extend AccountsController

```python
from erpnext.controllers.accounts_controller import AccountsController

class MyBillingDoc(AccountsController):
    def validate(self):
        super().validate()
        self.validate_currency()

    def on_submit(self):
        super().on_submit()
        self.make_gl_entries()
```

## Call super() rules

- Always call `super().validate()` first unless overriding is intentional.
- `super().on_submit()` triggers standard GL/SL posting for AccountsController.
- Do not call `super().on_cancel()` unless you understand its reversal logic.

## Useful AccountsController helpers

```python
self.set_missing_values()           # fill posting date, currency, etc.
self.validate_payment_terms_amount()
self.validate_currency()
self.calculate_taxes_and_totals()   # from TaxesAndTotals mixin
```

## Pick the right file

- Use `accounts_controller.md` for full AccountsController GL posting patterns.
- Use `buying_controller.md` for purchase-side tax and order helpers.
- Use `frappe/backend/controller_lifecycle.md` for generic Frappe document hooks.
