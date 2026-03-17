# has_permission

Use `frappe.has_permission()` to check access before sensitive actions.

## Check DocType permission

```python
if not frappe.has_permission("Sales Order", "write"):
    frappe.throw("Not permitted")
```

## Check document-level permission

```python
doc = frappe.get_doc("Sales Order", "SO-0001")

if not frappe.has_permission(doc=doc, ptype="submit"):
    frappe.throw("You cannot submit this Sales Order")
```

## Use in whitelisted methods

```python
@frappe.whitelist()
def close_issue(name):
    doc = frappe.get_doc("Issue", name)
    if not frappe.has_permission(doc=doc, ptype="write"):
        frappe.throw("Not permitted")
    doc.status = "Closed"
    doc.save()
```

## Rules

- Check permissions before writes, deletes, or submits.
- Pass `doc=...` when document-level logic matters.
- Fail early with a clear permission error.

## Do not use for

- Defining permission rules for a DocType
- Row-level query filtering

Use `permissions.md` for permission design and custom handlers.
