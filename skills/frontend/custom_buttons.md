# custom_buttons

Add or remove custom buttons on the form.

```javascript
frm.add_custom_button(__("Label"), function () { /* action */ }, __("Group"));
frm.remove_custom_button(__("Label"), __("Group"));
frm.page.set_primary_action(__("Save"), function () { frm.save(); });
```
