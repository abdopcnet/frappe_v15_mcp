# File Upload

Use this when the question is about saving or reading files in Frappe.

## Save file content

```python
from frappe.utils.file_manager import save_file

file_doc = save_file(
    fname="customer-note.txt",
    content="Customer contacted and verified.",
    dt="Customer",
    dn=customer_name,
    is_private=1,
)
```

## Read file metadata

```python
file_doc = frappe.get_doc("File", file_name)
file_url = file_doc.file_url
```

## Read file content from disk/storage

```python
from frappe.utils.file_manager import get_file

file_path, content = get_file(file_url)
```

## Pick the right file

- Use this file for File DocType persistence.
- Use `pdf_generation.md` or `excel_utils.md` when generating content first.
