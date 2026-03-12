# has_permission

Check user permission before sensitive operations.

```python
if not frappe.has_permission("Sales Order", "write", doc=doc):
	frappe.throw("Not permitted")
```

## Notes

- Check permissions before write/delete operations
- Use explicit `doc` when checking document-level rules
- Fail early with clear error messages
