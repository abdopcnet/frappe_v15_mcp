# custom_buttons

Add form toolbar actions with `frm.add_custom_button()`.

## Simple button

```javascript
frappe.ui.form.on("Task", {
  refresh(frm) {
    frm.add_custom_button(__("Mark Complete"), () => {
      frm.set_value("status", "Completed");
      frm.save();
    });
  },
});
```

## Grouped button

```javascript
frm.add_custom_button(__("Payment Entry"), () => create_payment_entry(frm), __("Create"));
frm.add_custom_button(__("Delivery Note"), () => create_delivery_note(frm), __("Create"));
frm.page.set_inner_btn_group_as_primary(__("Create"));
```

## Conditional button

```javascript
if (frm.doc.docstatus === 1 && frm.perm[0].cancel) {
  frm.add_custom_button(__("Cancel"), () => frm.cancel()).addClass("btn-danger");
}
```

## Rules

- Add buttons from `refresh()` so they reappear correctly.
- Gate actions by `is_new()`, `docstatus`, and permissions.
- Use confirmation dialogs for destructive actions.

## Do not use for

- Primary save lifecycle documentation
- General dialog patterns; use `dialogs.md`
