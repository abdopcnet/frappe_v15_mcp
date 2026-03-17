# Send Email

Use this when the question is how to send mail from Python code.

## Basic sendmail

```python
frappe.sendmail(
    recipients=[doc.owner],
    subject="Document submitted",
    message=f"{doc.doctype} {doc.name} was submitted.",
)
```

## Send rendered HTML

```python
html = frappe.render_template("""
    <p>Hello {{ full_name }},</p>
    <p>Your order <b>{{ order_name }}</b> is confirmed.</p>
""", {
    "full_name": customer_name,
    "order_name": sales_order.name,
})

frappe.sendmail(
    recipients=[customer_email],
    subject="Order confirmation",
    message=html,
)
```

## Attach a file

```python
frappe.sendmail(
    recipients=[customer_email],
    subject="Invoice",
    message="Attached invoice PDF.",
    attachments=[{
        "fname": "invoice.pdf",
        "fcontent": pdf_bytes,
    }],
)
```

## Pick the right file

- Use this file for direct mail sending.
- Use `email_template.md` when the message should come from an Email Template.
- Use `notification_config.md` when the mail should be declarative and event-driven.
