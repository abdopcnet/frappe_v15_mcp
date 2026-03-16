# custom_buttons

Add or remove custom buttons on the form.

```javascript
frappe.ui.form.on("My DocType", {
  refresh(frm) {
    // Simple button with inline action
    frm.add_custom_button(__("Do Something"), function () {
      frappe.call({
        method: "my_app.my_module.my_method",
        args: { name: frm.doc.name },
        freeze: true,
        freeze_message: __("Processing..."),
        callback: function (r) {
          if (r.exc) return;
          frappe.msgprint(__("Done"));
        },
      });
    });

    // Example: primary button
    frm.add_custom_button(__("Primary Action"), function () {
      // direct action logic here
    }).addClass("btn-primary");
  },
});

// Remove button or set primary action when needed:
// frm.remove_custom_button(__("Label"));
// frm.page.set_primary_action(__("Save"), function () { frm.save(); });
```
