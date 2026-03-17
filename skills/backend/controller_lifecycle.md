# controller_lifecycle

Canonical lifecycle hook snippets for DocType controller classes.

## Execution order

```text
Insert: autoname -> before_insert -> before_validate -> validate -> before_save -> after_insert -> on_update
Update: before_validate -> validate -> before_save -> on_update
Submit: validate -> before_submit -> on_submit
Cancel: before_cancel -> on_cancel
Delete: on_trash -> after_delete
Load: onload
```

## Minimal controller skeleton

```python
from frappe.model.document import Document
import frappe

class ExpenseClaim(Document):
    def before_insert(self):
        if not self.status:
            self.status = "Draft"

    def validate(self):
        if not self.employee:
            frappe.throw("Employee is required")

    def before_save(self):
        self.title = f"{self.employee} - {self.posting_date}"

    def on_update(self):
        self.update_related_totals()
```

## Submit and cancel hooks

```python
class ExpenseClaim(Document):
    def before_submit(self):
        if self.status != "Approved":
            frappe.throw("Only approved documents can be submitted")

    def on_submit(self):
        self.status = "Submitted"
        self.make_gl_entries()

    def before_cancel(self):
        if self.has_linked_payment_entry():
            frappe.throw("Cancel linked payments first")

    def on_cancel(self):
        self.reverse_gl_entries()
        self.status = "Cancelled"
```

## onload for frontend-only data

```python
def onload(self):
    self.set_onload("can_approve", frappe.has_permission(self.doctype, "submit", self))
    self.set_onload("dashboard_total", sum(row.amount for row in self.items))
```

## Safe hook boundaries

- `validate()` owns correctness checks.
- `before_save()` owns last-minute field normalization.
- `on_update()` owns side effects after insert/update.
- `before_submit()` and `on_submit()` own submittable business flow.
- `on_trash()` owns cleanup before delete.

## Do not use for

- Long validation catalogs; use `validation_patterns.md`
- Persistence API comparisons; use `save.md`
- hooks.py doc_events wiring; keep that in system skills
