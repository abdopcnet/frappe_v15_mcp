# query_builder

Use `frappe.qb` for structured SQL when ORM helpers are not enough but raw SQL is too loose.

## Basic select

```python
from frappe.query_builder import DocType

Task = DocType("Task")

rows = (
    frappe.qb.from_(Task)
    .select(Task.name, Task.subject, Task.status)
    .where(Task.status == "Open")
    .orderby(Task.creation, order=frappe.qb.desc)
    .limit(20)
).run(as_dict=True)
```

## Join

```python
User = DocType("User")

rows = (
    frappe.qb.from_(Task)
    .left_join(User).on(Task.assigned_to == User.name)
    .select(Task.name, User.full_name.as_("assigned_to_name"))
).run(as_dict=True)
```

## Aggregation

```python
from frappe.query_builder.functions import Count

rows = (
    frappe.qb.from_(Task)
    .select(Task.status, Count("*").as_("count"))
    .groupby(Task.status)
).run(as_dict=True)
```

## Rules

- Use Query Builder for joins, aggregation, and dynamic conditions.
- Prefer it before raw SQL when readability matters.
- Keep ORM helpers for simple CRUD.

## Do not use for

- Simple `get_list` or `get_value` reads
- Vendor-specific SQL features that Query Builder cannot express cleanly
