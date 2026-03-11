Control allowed methods and permissions for whitelisted APIs.

```python
@frappe.whitelist(allow_guest=False)
def restricted_method():
    if not frappe.has_permission("DocType", "read"):
        frappe.throw("Not allowed")
```
