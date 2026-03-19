# validation_patterns

Short validation snippets for `validate()` and small helper methods.

This file owns concrete validation patterns only.
Hook order belongs in `controller_lifecycle.md`.

## Required and conditional fields

```python
def validate(self):
    if not self.customer:
        frappe.throw("Customer is required")

    if self.payment_type == "Cash" and not self.cash_account:
        frappe.throw("Cash Account is required for Cash payments")
```

## Built-in validators

```python
def validate(self):
    self.validate_value("amount", ">=", 0)
    self.validate_value("discount", "<=", 100)
    self.validate_from_to_dates("start_date", "end_date")
    self.validate_table_has_rows("items")
```

## Child table validation

```python
from frappe.utils import flt

def validate(self):
    seen = set()

    for row in self.items:
        if not row.item_code:
            frappe.throw(f"Row {row.idx}: Item Code is required")
        if flt(row.qty) <= 0:
            frappe.throw(f"Row {row.idx}: Qty must be greater than 0")
        if row.item_code in seen:
            frappe.throw(f"Row {row.idx}: Duplicate item {row.item_code}")
        seen.add(row.item_code)
```

## Compare with previous state

```python
def validate(self):
    if self.has_value_changed("status"):
        old_doc = self.get_doc_before_save()
        if old_doc and old_doc.status == "Closed":
            frappe.throw("Closed documents cannot change status")
```

## Cross-document checks

```python
def validate(self):
    if self.project:
        project = frappe.get_cached_value(
            "Project",
            self.project,
            ["status", "company"],
            as_dict=1,
        )
        if project.status == "Completed":
            frappe.throw("Cannot create Task for completed Project")
        if project.company != self.company:
            frappe.throw("Project company must match document company")
```

## Rules

- Keep orchestration in `validate()` and move repeated logic to helpers.
- Raise `frappe.throw()` as soon as the document becomes invalid.
- Prefer built-in validators before custom comparisons.
- Keep permission checks and status transitions explicit.

## Do not use for

- Hook order reference; use `controller_lifecycle.md`
- Save/submit/cancel behavior; use `save.md`
- Frontend form validation; use frontend form event skills
