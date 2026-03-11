Persist document with doc.save(); avoid calling save inside hooks that can recurse.

```python
doc = frappe.get_doc("Task", "TASK-001")
doc.status = "Closed"
doc.save()
```
