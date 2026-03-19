# permissions

Define where permission rules belong in Frappe.

## Custom permission handler in hooks

```python
has_permission = {
    "Sales Order": "my_app.permissions.sales_order_has_permission"
}
```

```python
def sales_order_has_permission(doc, user=None, permission_type=None):
    user = user or frappe.session.user

    if permission_type == "read" and doc.owner == user:
        return True

    return None
```

## Row-level filtering

```python
permission_query_conditions = {
    "Sales Order": "my_app.permissions.sales_order_query_conditions"
}
```

```python
def sales_order_query_conditions(user):
    return "`tabSales Order`.owner = {0}".format(frappe.db.escape(user))
```

## Rules

- `has_permission` decides access to one document.
- `permission_query_conditions` filters list/query visibility.
- Return `None` when custom logic does not decide the outcome.

## Do not use for

- One-off runtime checks inside business code; use `has_permission.md`
- Frontend hide/show logic as a substitute for backend permissions
