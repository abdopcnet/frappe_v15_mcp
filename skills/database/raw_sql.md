# raw_sql

Use raw SQL only when ORM helpers or Query Builder are not sufficient.

## Safe parameter binding

```python
rows = frappe.db.sql(
    """
    SELECT name, subject
    FROM `tabTask`
    WHERE status = %(status)s
    """,
    {"status": "Open"},
    as_dict=True,
)
```

## Update statement

```python
frappe.db.sql(
    """
    UPDATE `tabTask`
    SET status = %s
    WHERE name = %s
    """,
    ("Completed", "TASK-0001"),
)
frappe.db.commit()
```

## Bulk `IN` clause

```python
names = ["TASK-0001", "TASK-0002"]
placeholders = ", ".join(["%s"] * len(names))

frappe.db.sql(
    f"UPDATE `tabTask` SET status = %s WHERE name IN ({placeholders})",
    ["Closed", *names],
)
```

## Rules

- Always bind parameters.
- Prefer Query Builder before raw SQL for maintainability.
- Commit only when you actually changed data.

## Do not use for

- String-formatted user input in SQL
- Standard document CRUD already covered by ORM methods
