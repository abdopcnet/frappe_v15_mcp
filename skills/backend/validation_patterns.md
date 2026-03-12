# validation_patterns

Validate in `validate()`: required, value range, dates, child table, duplicates.

```python
def validate(self):
    if not self.field:
        frappe.throw(_("Field is required"))
    self.validate_value("amount", ">=", 0)
    self.validate_from_to_dates("start_date", "end_date")
    self.validate_table_has_rows("items")
    self.round_floats_in(self, ["amount", "rate"])
```

Use `self.has_value_changed("field")` and `self.get_doc_before_save()` when needed.
