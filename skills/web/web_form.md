# Web Form

Use this when the question is about collecting website input into a DocType through Web Form.

## Create a Web Form record

```python
if not frappe.db.exists("Web Form", "Support Ticket"):
    frappe.get_doc({
        "doctype": "Web Form",
        "title": "Support Ticket",
        "route": "support-ticket",
        "doc_type": "Issue",
        "login_required": 1,
        "published": 1,
    }).insert()
```

## Pick the right file

- Use this file for Web Form configuration.
- Use `web_page.md` for custom route logic.
