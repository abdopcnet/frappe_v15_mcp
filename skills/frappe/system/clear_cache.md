# clear_cache

Invalidate Frappe caches after configuration, permission, or metadata changes.

## Clear all site caches

```python
frappe.clear_cache()
```

## Clear one user or one DocType scope

```python
frappe.clear_cache(user="user@example.com")
frappe.clear_cache(doctype="Sales Order")
```

## Typical use

```python
def after_permission_change(user):
    frappe.clear_cache(user=user)

def after_custom_field_change():
    frappe.clear_cache(doctype="Sales Order")
```

## Rules

- Clear the smallest possible scope first.
- Use full `frappe.clear_cache()` only when targeted invalidation is not enough.
- Prefer this after metadata, role, permission, or settings changes.

## Do not use for

- Per-request cleanup
- Replacing explicit `frappe.cache().delete_value()` for one known key

Use `cache.md` for cache key patterns and caching reads.
