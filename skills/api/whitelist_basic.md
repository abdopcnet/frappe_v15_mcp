# whitelist_basic

Minimal patterns for exposing a Python method through Frappe.

## When to use

- Logged-in client or API calls that need a small server entrypoint
- Read or write operations that need explicit validation
- Methods that return JSON-serializable data only

## Basic pattern

```python
import frappe

@frappe.whitelist()
def ping():
	return {"message": "ok"}
```

## Validate inputs early

```python
@frappe.whitelist()
def get_customer_balance(customer):
	if not customer:
		frappe.throw("Customer is required")

	balance = frappe.db.get_value("Customer", customer, "outstanding_amount")
	return {"customer": customer, "balance": balance}
```

## Access path

```text
/api/method/my_app.api.get_customer_balance
```

```javascript
frappe.call({
  method: "my_app.api.get_customer_balance",
  args: { customer: frm.doc.customer },
  callback: (r) => console.log(r.message),
});
```

## Rules

- Default access is logged-in users only.
- Return dict, list, string, number, or None.
- Validate required args yourself.
- Keep business rules in app code, not in giant endpoint wrappers.
- Use POST for mutations even if Frappe can route multiple verbs.

## Do not use for

- Pure internal backend calls between Python functions
- Full document loading when `frappe.db.get_value` or `get_list` is enough
- Guest/public endpoints with special security needs; use whitelist_advanced.md
