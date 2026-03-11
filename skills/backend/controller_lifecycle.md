# controller_lifecycle

Document lifecycle hooks. Use one hook per concern.

```python
class MyDocType(Document):
    def validate(self):
        if not self.field:
            frappe.throw(_("Field is required"))
```

Order: autoname → before_insert → after_insert → before_validate → validate → before_save → on_update → before_submit → on_submit → before_cancel → on_cancel → on_trash. Use `onload(self)` and `self.set_onload("key", value)` for load-only data.
