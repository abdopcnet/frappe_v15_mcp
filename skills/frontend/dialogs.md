# dialogs

Show message, alert, or confirmation. Use Frappe APIs only; do not invent helpers.

## Simple message and alert

```javascript
frappe.msgprint(__("Message"));
frappe.show_alert({ message: __("Done"), indicator: "green" }, 5);
frappe.confirm(__("Proceed?"), () => frm.save(), () => {});
frappe.throw(__("Error"));
```

## msgprint with options (popup dialog)

Use the object form for title, HTML message, indicator, wide dialog:

```javascript
frappe.msgprint({
	title: __("Connection OK"),
	message: __("Login succeeded."),
	indicator: "green",
});
frappe.msgprint({
	title: __("Error"),
	message: err_message,
	indicator: "red",
});
// Wide dialog for tables / long content
frappe.msgprint({
	title: __("Results"),
	message: "<table class='table table-bordered'>...</table>",
	wide: true,
});
```

Optional: `primary_action: { label: __("OK"), action: function () {} }`.

## HTML in message and escaping

When building `message` from user or server data (e.g. table rows), escape that data so it is not interpreted as HTML. Use **`frappe.utils.escape_html(txt)`** (Frappe built-in in `frappe/public/js/frappe/utils/utils.js`). Do not use `frappe.escape_html` (no such API).

```javascript
var safe = frappe.utils.escape_html(user_input);
var html = "<tr><td>" + safe + "</td></tr>";
frappe.msgprint({ title: __("Detail"), message: html });
```

Confirm only destructive actions. Keep messages short.
