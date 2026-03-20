# BuyingController / SellingController

Use when extending purchase or sales transactional DocTypes and needing the
built-in tax, pricing, and order-flow helpers.

## BuyingController

```python
from erpnext.controllers.buying_controller import BuyingController

class MyPurchaseDoc(BuyingController):
    def validate(self):
        super().validate()
        self.validate_supplier_currency()

    def validate_supplier_currency(self):
        if self.currency != frappe.db.get_value("Supplier", self.supplier, "default_currency"):
            frappe.msgprint("Supplier default currency mismatch", alert=True)
```

## SellingController

```python
from erpnext.controllers.selling_controller import SellingController

class MyQuotation(SellingController):
    def validate(self):
        super().validate()
        self.validate_selling_price()

    def validate_selling_price(self):
        for row in self.items:
            if row.rate < row.valuation_rate:
                frappe.throw(f"Row {row.idx}: selling rate below valuation rate")
```

## Useful BuyingController helpers

```python
self.set_missing_item_details()     # fill item defaults (uom, rate, expense_account)
self.validate_for_subcontracting()
self.update_ordered_qty_in_so()
```

## Useful SellingController helpers

```python
self.set_missing_item_details()
self.calculate_commission()
self.validate_max_discount()
```

## TaxesAndTotals mixin (available in both)

```python
self.calculate_taxes_and_totals()   # recalc net_total, total_taxes, grand_total
self.set_taxes()                     # apply taxes from tax template
```

## Rules

- Both inherit from `AccountsController`; GL entry logic is already in the chain.
- Call `super().validate()` before custom validation.
- `set_missing_item_details()` is safe to call multiple times; it is idempotent.

## Pick the right file

- Use `accounts_controller.md` for GL posting patterns.
- Use `base_controllers.md` for the full hierarchy diagram.
