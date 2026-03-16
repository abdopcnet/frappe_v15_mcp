# form_events

Form lifecycle and field-change handlers.

```javascript
frappe.ui.form.on("DocType Name", {
  onload(frm) {
    // optional: light onload logic
  },

  refresh(frm) {
    // example: toggle a field
    if (frm.fields_dict.my_field) {
      frm.toggle_display("my_field", !!frm.doc.enable_flag);
    }

    // example: simple button with inline frappe.call
    frm.add_custom_button(__("Do Something"), function () {
      frappe.call({
        method: "my_app.my_module.my_method",
        args: { docname: frm.doc.name },
        freeze: true,
        freeze_message: __("Processing..."),
        callback: function (r) {
          if (r.exc) return;
          frappe.msgprint(__("Done"));
        },
      });
    });
  },

  validate(frm) {
    if (!frm.doc.field) frappe.throw(__("Required"));
  },

  after_save(frm) {},

  field_name(frm) {
    frm.set_value("other", frm.doc.field_name);
  },
});
```

Order: onload → refresh → field handlers → validate → before_save → after_save.
