# file_upload

Save and attach files to documents.

```python
from frappe.utils.file_manager import save_file, get_file
file_doc = save_file(fname="doc.pdf", content=content, dt="DocType", dn=doc.name, is_private=1)
path, f = get_file(file_doc.file_url)
```

Attach via File doctype: `attached_to_doctype`, `attached_to_name`. Validate size and type.
