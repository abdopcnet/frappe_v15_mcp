# form_events

Form lifecycle and field-change handlers.

```javascript
frappe.ui.form.on("DocType Name", {
  onload(frm) {},
  refresh(frm) {},
  validate(frm) { if (!frm.doc.field) frappe.throw(__("Required")); },
  after_save(frm) {},
  field_name(frm) { frm.set_value("other", frm.doc.field_name); },
});
```

Order: onload → refresh → field handlers → validate → before_save → after_save.
