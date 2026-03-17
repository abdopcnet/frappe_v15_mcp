# Notification Config

Use this when the question is about Frappe Notification records, not handwritten mail code.

## Create a notification rule

```python
if not frappe.db.exists("Notification", "Overdue Invoice Alert"):
    frappe.get_doc({
        "doctype": "Notification",
        "name": "Overdue Invoice Alert",
        "document_type": "Sales Invoice",
        "event": "Days Before",
        "days_in_advance": 2,
        "date_changed": "due_date",
        "channel": "Email",
        "subject": "Invoice {{ doc.name }} is approaching due date",
        "message": "Invoice {{ doc.name }} for {{ doc.customer }} is due on {{ doc.due_date }}.",
        "recipients": [{"receiver_by_document_field": "contact_email"}],
    }).insert()
```

## Common recipient pattern

```python
notification.append("recipients", {
    "receiver_by_role": "Accounts Manager",
})
```

## Pick the right file

- Use this file for declarative Notification DocType rules.
- Use `email_template.md` for reusable template content.
- Use `send_email.md` for imperative Python email sending.
