Use flt, cint, frappe.datetime, format_currency on the client.

```javascript
frappe.model.with_doctype("Item", () => { });
let n = cint(frm.doc.qty);
let d = frappe.datetime.str_to_obj(frm.doc.posting_date);
```
