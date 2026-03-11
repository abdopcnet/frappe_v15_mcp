# client_script

JavaScript via UI: Form script or List script. One DocType, one script type.

```javascript
// Form: DocType + Form, use frappe.ui.form.on("DocType", { refresh(frm){}, field_name(frm){} })
frappe.ui.form.on("Sales Invoice", { refresh(frm) { frm.add_custom_button(__("Action"), () => {}); } });
// List: Script Type List, use frappe.listview_settings["DocType"] = { get_indicator(doc) { return [__("Paid"), "green", "status,=,Paid"]; } }
```

Use server calls for trusted ops. Check frm.is_new() before buttons.
