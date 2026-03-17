# form_events

Use `frappe.ui.form.on()` for form lifecycle and field-trigger events.

## Basic lifecycle

```javascript
frappe.ui.form.on("Task", {
  onload(frm) {
    if (frm.is_new()) {
      frm.set_value("status", "Open");
    }
  },

  refresh(frm) {
    if (!frm.is_new()) {
      frm.add_custom_button(__("Reload"), () => frm.reload_doc());
    }
  },

  validate(frm) {
    if (!frm.doc.subject) {
      frappe.msgprint(__("Subject is required"));
      frappe.validated = false;
    }
  },

  after_save(frm) {
    frappe.show_alert({ message: __("Saved"), indicator: "green" });
  },
});
```

## Field trigger

```javascript
frappe.ui.form.on("Task", {
  priority(frm) {
    if (frm.doc.priority === "High" && !frm.doc.exp_end_date) {
      frm.set_value("exp_end_date", frappe.datetime.add_days(frappe.datetime.get_today(), 1));
    }
  },
});
```

## Child row trigger

```javascript
frappe.ui.form.on("Sales Invoice Item", {
  qty(frm, cdt, cdn) {
    const row = locals[cdt][cdn];
    frappe.model.set_value(cdt, cdn, "amount", (row.qty || 0) * (row.rate || 0));
  },
});
```

## Rules

- `onload` is for one-time setup.
- `refresh` is for UI actions that must reappear every time.
- `validate` only blocks save from the client side; backend validation still matters.

## Do not use for

- Long state-management logic; use `form_state.md`
- Explaining field mutation APIs in depth; use `set_value.md`
- Display refresh semantics; use `refresh_field.md`
