Use Frappe query builder for complex queries instead of raw SQL when possible.

```python
from frappe.query_builder import DocType
Task = DocType("Task")
q = frappe.qb.from_(Task).select(Task.name, Task.subject).where(Task.status == "Open")
q.run(as_dict=True)
```
