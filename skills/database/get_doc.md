Load full document (with children) or create new. Use `for_update=True` when locking.

```python
doc = frappe.get_doc("Sales Invoice", "SINV-2024-00001")
new_doc = frappe.get_doc({"doctype": "Task", "subject": "New Task"})
```
