# set_value

Set form and child-table values through Frappe APIs instead of mutating the document directly.

## Set one field

```javascript
frm.set_value("status", "Open");
frm.set_value("exp_start_date", frappe.datetime.get_today());
```

## Set multiple fields

```javascript
frm.set_value({
  priority: "High",
  status: "Working",
});
```

## Set child row fields

```javascript
frappe.ui.form.on("Sales Invoice Item", {
  item_code(frm, cdt, cdn) {
    frappe.db.get_value("Item", locals[cdt][cdn].item_code, ["item_name", "standard_rate"]).then((r) => {
      frappe.model.set_value(cdt, cdn, "item_name", r.message.item_name);
      frappe.model.set_value(cdt, cdn, "rate", r.message.standard_rate);
    });
  },
});
```

## Add a child row then fill it

```javascript
const row = frm.add_child("items");
frappe.model.set_value(row.doctype, row.name, "item_code", "ITEM-001");
frappe.model.set_value(row.doctype, row.name, "qty", 1);
frm.refresh_field("items");
```

## Rules

- Prefer `frm.set_value()` for parent fields.
- Prefer `frappe.model.set_value()` for child rows.
- Avoid direct `frm.doc.field = ...` mutations unless you know you will refresh manually.

## Do not use for

- Explaining when refresh is required; use `refresh_field.md`
- Lifecycle event selection; use `form_events.md`
