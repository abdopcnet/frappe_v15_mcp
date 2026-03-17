# dialogs

Use Frappe dialog APIs for messages, confirmations, and lightweight input.

## Message popup

```javascript
frappe.msgprint({
  title: __("Success"),
  message: __("Task updated"),
  indicator: "green",
});
```

## Toast alert

```javascript
frappe.show_alert({ message: __("Saved"), indicator: "green" }, 3);
```

## Confirmation dialog

```javascript
frappe.confirm(__("Delete this row?"), () => {
  frm.clear_table("items");
  frm.refresh_field("items");
});
```

## Prompt for input

```javascript
frappe.prompt(
  {
    label: "Reason",
    fieldname: "reason",
    fieldtype: "Small Text",
    reqd: 1,
  },
  (values) => {
    frm.set_value("cancellation_reason", values.reason);
  },
  __("Cancellation Reason"),
  __("Apply"),
);
```

## Rules

- Use `msgprint()` for blocking feedback.
- Use `show_alert()` for short non-blocking success/error notifications.
- Use `confirm()` before destructive actions.

## Do not use for

- Long custom workflows that deserve full pages or custom components
- Unsafe HTML from user input without sanitization
