# Email Queue

Use this when mail is enqueued but not delivered.

## Inspect recent queue entries

```python
rows = frappe.get_all(
    "Email Queue",
    fields=["name", "status", "sender", "priority", "creation"],
    order_by="creation desc",
    limit=20,
)
```

## Find failed emails

```python
failed = frappe.get_all(
    "Email Queue",
    filters={"status": "Error"},
    fields=["name", "sender", "message_id", "error"],
    order_by="modified desc",
)
```

## Retry a queued mail

```python
queue_doc = frappe.get_doc("Email Queue", queue_name)
queue_doc.retry_sending()
```

## Pick the right file

- Use this file for delivery state and retry patterns.
- Use `send_email.md` for creating mail.
- Use `email_account.md` for SMTP account configuration.
