# get_value

Fetch one row's field or a small field set without loading a full document.

Use this when `get_doc()` would be heavier than necessary.

## Single field

```python
status = frappe.db.get_value("Task", "TASK-0001", "status")
owner = frappe.db.get_value("Task", {"status": "Open"}, "owner")
```

## Multiple fields

```python
name, status = frappe.db.get_value("Task", "TASK-0001", ["name", "status"])

data = frappe.db.get_value(
    "Task",
    {"status": "Open"},
    ["name", "subject", "priority"],
    as_dict=True,
)
```

## Useful options

```python
latest_task = frappe.db.get_value(
    "Task",
    {"status": "Open"},
    "name",
    order_by="creation desc",
)

company = frappe.db.get_value(
    "Global Defaults",
    None,
    "default_company",
    cache=True,
)
```

## Lock a row in a transaction

```python
qty = frappe.db.get_value(
    "Bin",
    {"item_code": "ITEM-001", "warehouse": "Stores - TC"},
    "actual_qty",
    for_update=True,
)
```

## Rules

- Prefer `get_value()` for one document field or a very small field set.
- Use `as_dict=True` when field order is easy to confuse.
- Use `cache=True` only for stable configuration values.
- `get_value()` does not load child tables or document methods.

## Do not use for

- Full-document business logic
- Editing rows in memory
- Multi-row list queries

Use `get_doc.md` for full documents and `get_list.md` or `get_all.md` for lists.
