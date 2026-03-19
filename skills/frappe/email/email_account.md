# Email Account

Use this when the question is about configuring which outbound account sends mail.

## Configure an outgoing account

```python
account = frappe.get_doc({
    "doctype": "Email Account",
    "email_id": "support@example.com",
    "service": "Custom",
    "email_server": "smtp.example.com",
    "email_server_port": 587,
    "use_tls": 1,
    "login_id": "support@example.com",
    "password": frappe.get_conf().smtp_password,
    "enable_outgoing": 1,
    "default_outgoing": 1,
})
account.insert()
```

## Send from a specific account

```python
frappe.sendmail(
    recipients=["user@example.com"],
    subject="Welcome",
    message="Your account is ready.",
    email_account="support@example.com",
)
```

## Pick the right file

- Use this file for Email Account setup and sender selection.
- Use `send_email.md` for `frappe.sendmail()` patterns.
- Use `email_queue.md` for delivery troubleshooting after enqueue.
