Use onload, form_render, validate, and field change events.

```javascript
frappe.ui.form.on("Sales Order", {
    onload: (frm) => { },
    refresh: (frm) => { },
    customer: (frm) => { frm.set_value("customer_name", ""); }
});
```
