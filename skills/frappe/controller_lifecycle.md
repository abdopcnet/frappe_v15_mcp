Override before_save, validate, on_submit, on_cancel; respect hook order.

```python
def validate(self):
    if self.amount <= 0:
        frappe.throw("Amount must be positive")
def on_submit(self):
    self.make_gl_entries()
```
