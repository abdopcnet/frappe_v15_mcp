# client_script

Use Client Script when you need UI behavior without shipping app code files.

## Form script pattern

```javascript
frappe.ui.form.on("Sales Invoice", {
  refresh(frm) {
    if (!frm.is_new()) {
      frm.add_custom_button(__("Recalculate"), () => frm.trigger("recalculate_totals"));
    }
  },

  recalculate_totals(frm) {
    let total = 0;
    (frm.doc.items || []).forEach((row) => (total += row.amount || 0));
    frm.set_value("rounded_total", total);
  },
});
```

## List script pattern

```javascript
frappe.listview_settings["Sales Invoice"] = {
  get_indicator(doc) {
    if (doc.status === "Paid") {
      return [__("Paid"), "green", "status,=,Paid"];
    }
  },
};
```

## Rules

- Use Client Script for UI behavior, not trusted backend business rules.
- Keep logic small and call whitelisted/server methods for sensitive operations.
- Use one script per DocType and script type.

## Do not use for

- Permission enforcement
- Heavy business logic shared across apps

Move stable, reusable logic into app code when it outgrows the UI layer.
