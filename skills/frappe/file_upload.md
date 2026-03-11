Attach file to document; get file URL or doc.

```python
file_doc = frappe.get_doc({
    "doctype": "File",
    "attached_to_doctype": doc.doctype,
    "attached_to_name": doc.name,
    "file_url": "/files/name.pdf",
}).insert()
```
