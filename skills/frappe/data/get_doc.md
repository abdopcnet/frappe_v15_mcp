# get_doc

Load or create a full document object with fields, methods, and child tables.

Use this when you need document behavior, not just raw field values.

## Load an existing document

```python
doc = frappe.get_doc("Task", "TASK-0001")
invoice = frappe.get_doc("Sales Invoice", "SINV-0001")
```

## Create a new document in memory

```python
doc = frappe.get_doc({
    "doctype": "Task",
    "subject": "New Task",
    "status": "Open",
})
```

## Child tables are loaded with the document

```python
so = frappe.get_doc("Sales Order", "SO-0001")

for row in so.items:
    print(row.item_code, row.qty)

so.append("items", {"item_code": "ITEM-001", "qty": 2, "rate": 100})
```

## Lock a row for update

```python
doc = frappe.get_doc("Task", "TASK-0001", for_update=True)
```

## Copy an existing document

```python
original = frappe.get_doc("Task", "TASK-0001")
clone = frappe.copy_doc(original)
clone.subject = f"Copy of {clone.subject}"
```

## Rules

- `get_doc()` loads full document state and methods.
- Use it when you need child tables, validation, save, submit, or custom methods.
- Use `for_update=True` only inside transaction-sensitive flows.

## Do not use for

- Single field reads
- Lightweight lookups in hot paths
- Bulk list queries

Use `get_value.md` for small reads and `get_list.md` or `get_all.md` for lists.
