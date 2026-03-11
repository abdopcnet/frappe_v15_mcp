# child_table

Add/clear child rows and handle child events.

```javascript
let row = frm.add_child("items", { item_code: "X", qty: 1 });
frm.refresh_field("items");
frm.clear_table("items");
frappe.ui.form.on("Child DocType", {
  item_code(frm, cdt, cdn) {
    frappe.model.set_value(cdt, cdn, "qty", 1);
  },
});
```

Refresh the table field after add/clear.
