# whitelist_advanced

Advanced whitelist patterns for role checks, guest access, and method boundaries.

## Role-gated method

```python
import frappe

@frappe.whitelist()
def close_ticket(ticket):
    frappe.only_for("System Manager")

    if not ticket:
        frappe.throw("Ticket is required")

    frappe.db.set_value("Issue", ticket, "status", "Closed")
    return {"status": "ok", "ticket": ticket}
```

## Multiple allowed roles

```python
@frappe.whitelist()
def approve_document(doctype, name):
    frappe.only_for(["Approver", "System Manager"])

    doc = frappe.get_doc(doctype, name)
    doc.status = "Approved"
    doc.save()
    return {"approved": True}
```

## Guest method

```python
@frappe.whitelist(allow_guest=True)
def get_public_info():
    return {
        "company": frappe.db.get_single_value("System Settings", "company"),
        "country": frappe.db.get_single_value("System Settings", "country"),
    }
```

## Guest method with manual sanitization

```python
@frappe.whitelist(allow_guest=True, xss_safe=True)
def submit_contact_form(name, email, message):
    doc = frappe.get_doc({
        "doctype": "Contact Form",
        "name": name,
        "email": email,
        "message": frappe.utils.sanitize_html(message),
    })
    doc.insert(ignore_permissions=True)
    return {"success": True}
```

## Restrict HTTP verbs

```python
@frappe.whitelist(methods=["POST"])
def delete_records(doctype, names):
    for name in names:
        frappe.delete_doc(doctype, name)
    return {"deleted": len(names)}
```

## Rules

- Use `frappe.only_for()` for role checks at the top of the method.
- Use `allow_guest=True` only for deliberately public endpoints.
- If guest input can contain HTML, sanitize it yourself.
- Prefer read-only GET endpoints and POST for mutations.
- Return the smallest safe payload possible.

## Do not use for

- Complex permission logic better handled inside DocType methods
- Public submission endpoints without rate limiting, validation, and sanitization
- Long transaction-heavy flows that should become background jobs
