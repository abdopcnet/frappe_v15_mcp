# Email Template

Use this when the question is about reusable email subject/message templates.

## Render a template manually

```python
template = frappe.get_doc("Email Template", "Order Confirmation")
args = {
    "customer_name": doc.customer_name,
    "order_name": doc.name,
}
subject = frappe.render_template(template.subject, args)
message = frappe.render_template(template.response_html, args)

frappe.sendmail(
    recipients=[doc.contact_email],
    subject=subject,
    message=message,
)
```

## Create a template by patch

```python
if not frappe.db.exists("Email Template", "Order Confirmation"):
    frappe.get_doc({
        "doctype": "Email Template",
        "name": "Order Confirmation",
        "subject": "Order {{ order_name }} confirmed",
        "response_html": "<p>Hello {{ customer_name }}, your order is confirmed.</p>",
    }).insert()
```

## Pick the right file

- Use this file for storing and rendering reusable email content.
- Use `send_email.md` for direct mail API usage.
- Use `notification_config.md` when the whole rule should live in Notification.
