# whitelist_advanced

Whitelist with role check and input validation.

```python
@frappe.whitelist()
def close_ticket(ticket):
    frappe.only_for("System Manager")
    if not ticket:
        frappe.throw("Ticket is required")
    frappe.db.set_value("Issue", ticket, "status", "Closed")
    return {"status": "ok"}
```

Validate input; enforce permissions; return small payloads.
