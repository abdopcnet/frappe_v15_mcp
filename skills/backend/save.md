# save

Short reference for `insert()`, `save()`, `submit()`, `cancel()`, and `reload()`.

## Create a new document

```python
doc = frappe.get_doc({
    "doctype": "Task",
    "subject": "New Task",
    "status": "Open",
})
doc.insert()
```

## Update an existing document

```python
doc = frappe.get_doc("Task", "TASK-0001")
doc.status = "Completed"
doc.save()
```

## Save with flags

```python
doc.save(ignore_permissions=True, ignore_version=True)
doc.insert(ignore_permissions=True, ignore_links=True, ignore_mandatory=True)
```

## Submit and cancel

```python
invoice = frappe.get_doc("Sales Invoice", "SINV-0001")

if invoice.docstatus == 0:
    invoice.submit()

if invoice.docstatus == 1:
    invoice.cancel()
```

## Reload in-memory state

```python
doc = frappe.get_doc("Task", "TASK-0001")
frappe.db.set_value("Task", doc.name, "status", "Closed")
doc.reload()
```

## Child tables save with parent

```python
doc = frappe.get_doc("Sales Order", "SO-0001")
doc.append("items", {"item_code": "ITEM-001", "qty": 2, "rate": 100})
doc.save()
```

## Use db.set_value when hooks are not needed

```python
frappe.db.set_value("Task", "TASK-0001", "status", "Completed")
```

## Rules

- Use `insert()` for new docs and `save()` for loaded docs.
- Use `submit()` and `cancel()` only on submittable DocTypes.
- Use `reload()` after external DB changes.
- Prefer `db.set_value()` only for small direct updates that do not need hooks.

## Do not use for

- Hook timing; use `controller_lifecycle.md`
- Validation catalogs; use `validation_patterns.md`
- Bulk write optimization; keep that in database/system skills
