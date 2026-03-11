Expose server methods to the client with @frappe.whitelist().

```python
@frappe.whitelist()
def get_summary(doctype, name):
    doc = frappe.get_doc(doctype, name)
    return {"total": doc.grand_total}
```
