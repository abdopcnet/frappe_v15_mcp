# Webhooks

Use this when Frappe should notify another system after document events.

## Create a webhook

```python
if not frappe.db.exists("Webhook", "Customer Sync"):
    frappe.get_doc({
        "doctype": "Webhook",
        "name": "Customer Sync",
        "webhook_doctype": "Customer",
        "webhook_docevent": "after_insert",
        "request_url": "https://api.example.com/customers",
        "webhook_json": 1,
        "enable_security": 1,
        "is_enabled": 1,
    }).insert()
```

## Common payload pattern

```python
payload = {
    "name": doc.name,
    "customer_name": doc.customer_name,
    "territory": doc.territory,
}
```

## Pick the right file

- Use this file for outbound event delivery through Webhook records.
- Use `doc_events.md` or `hooks_doc_events.md` for the internal trigger side.
- Use `rest_api.md` when another system calls Frappe instead.
