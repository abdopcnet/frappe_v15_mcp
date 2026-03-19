# child_table

Work with child table rows through `frm.add_child()`, `frm.clear_table()`, and child-row events.

## Add a row

```javascript
const row = frm.add_child("items", {
  item_code: "ITEM-001",
  qty: 1,
  rate: 100,
});
frm.refresh_field("items");
```

## Clear a table

```javascript
frm.clear_table("items");
frm.refresh_field("items");
```

## Child row event

```javascript
frappe.ui.form.on("Sales Invoice Item", {
  qty(frm, cdt, cdn) {
    const row = locals[cdt][cdn];
    frappe.model.set_value(cdt, cdn, "amount", (row.qty || 0) * (row.rate || 0));
  },
});
```

## Loop current rows

```javascript
(frm.doc.items || []).forEach((row) => {
  console.log(row.item_code, row.qty);
});
```

## Rules

- Use `frm.add_child()` for new rows.
- Use `frappe.model.set_value()` inside child-row events.
- Refresh the table after structural changes.

## Do not use for

- General parent-field mutation; use `set_value.md`
- List view logic or non-grid UI behavior
