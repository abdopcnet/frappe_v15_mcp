# delete_doc

Delete a document or a batch of documents.

## Delete a single document

```python
frappe.delete_doc("Task", "TASK-0001")
```

## Delete with permission bypass

```python
frappe.delete_doc("Task", "TASK-0001", ignore_permissions=True)
```

## Delete with missing check (no error if not found)

```python
frappe.delete_doc("Task", "TASK-0001", ignore_missing=True)
```

## Delete a Child document

```python
frappe.delete_doc("Sales Invoice Item", "some-row-name", ignore_permissions=True)
```

## Batch delete

```python
names = frappe.get_all("Task", filters={"status": "Cancelled"}, pluck="name")

for name in names:
    frappe.delete_doc("Task", name, ignore_permissions=True)
    frappe.db.commit()
```

## Delete via db.delete (no hooks, fastest)

```python
# Skips all hooks, field permissions, and cascades
frappe.db.delete("Task", {"status": "Cancelled", "modified": ["<", "2020-01-01"]})
```

## Rules

- `frappe.delete_doc()` fires `on_trash` and `after_delete` hooks.
- `frappe.db.delete()` skips all hooks — use only for admin cleanup or patches.
- Submittable documents must be cancelled before they can be deleted.
- Commit inside bulk loops to release locks on large datasets.

## Do not use for

- Cancelling submitted documents; use `doc.cancel()` first
- Removing child rows from a parent; use `doc.remove(row)` + `doc.save()`
