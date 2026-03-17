# utilities

Common client-side helpers for type conversion, dates, and formatting.

## Type helpers

```javascript
const qty = flt(frm.doc.qty, 2);
const count = cint(frm.doc.item_count);
const text = cstr(frm.doc.subject);
```

## Date helpers

```javascript
const today = frappe.datetime.get_today();
const nextWeek = frappe.datetime.add_days(today, 7);
const jsDate = frappe.datetime.str_to_obj(frm.doc.posting_date);
```

## Formatting

```javascript
const total = format_currency(frm.doc.grand_total, frm.doc.currency);
```

## Rules

- Normalize input before calculations.
- Use Frappe date helpers instead of hand-building strings.
- Use formatters only for display, not business logic.
