Use msgprint, show_alert, confirm for messages; escape HTML in user content.

```javascript
frappe.msgprint("Saved.");
frappe.show_alert({ message: __("Done"), indicator: "green" });
frappe.utils.escape_html(user_input);
```
