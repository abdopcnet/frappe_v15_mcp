# document_sharing

Share one document with a user beyond normal role access.

## Add or remove a share

```python
from frappe.share import add_docshare, remove_docshare

add_docshare("Task", "TASK-0001", "user@example.com", read=1, write=1, share=0, notify=1)
remove_docshare("Task", "TASK-0001", "user@example.com")
```

## Inspect existing shares

```python
rows = frappe.get_all(
    "DocShare",
    filters={"share_doctype": "Task", "share_name": "TASK-0001"},
    fields=["user", "read", "write", "share"],
)
```

## Rules

- Share documents deliberately; do not use sharing as a replacement for permission design.
- Remove stale shares when access should end.
- Notify users only when the share is meaningful.
