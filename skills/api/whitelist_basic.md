# whitelist

Expose a server method with `@frappe.whitelist()`.

```python
import frappe


@frappe.whitelist()
def ping():
	return {"message": "ok"}
```

## Notes

- Keep methods stateless where possible
- Validate input and use `frappe.throw` on invalid data
- Keep method names explicit and stable for client calls
