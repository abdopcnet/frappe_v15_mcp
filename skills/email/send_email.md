# send_email

Send email from server code.

```python
frappe.sendmail(
    recipients=["user@example.com"],
    subject="Subject",
    message="<p>Body</p>",
)
frappe.sendmail(recipients=[], template="template_name", args={"name": doc.name}, attachments=[{"fname": "file.pdf", "fcontent": pdf}])
```

Validate recipients. Use templates for repeated messages.
