Raise frappe.throw on validation failure with a clear message.

```python
if not self.get("customer"):
    frappe.throw("Customer is required")
if self.grand_total < 0:
    frappe.throw("Grand total cannot be negative")
```
