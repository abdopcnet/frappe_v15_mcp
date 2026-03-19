# api_calls

Call whitelisted backend methods from client-side code using `frappe.call()` or `frappe.xcall()`.

## `frappe.call()`

```javascript
frappe.call({
  method: "my_app.api.process_task",
  args: { task: frm.doc.name },
  freeze: true,
  freeze_message: __("Processing..."),
  callback(r) {
    if (!r.exc) {
      frappe.show_alert({ message: __("Done"), indicator: "green" });
    }
  },
});
```

## `frappe.xcall()`

```javascript
const result = await frappe.xcall("my_app.api.get_task_details", {
  task: frm.doc.name,
});

frm.set_value("subject", result.subject);
```

## Error handling

```javascript
try {
  const result = await frappe.xcall("my_app.api.get_data", { name: frm.doc.name });
  console.log(result);
} catch (error) {
  frappe.msgprint(__("Request failed"));
}
```

## Rules

- Use `frappe.call()` when callback style is already in use.
- Use `frappe.xcall()` for async/await flows.
- Keep trusted writes on the server side.

## Do not use for

- Replacing server-side permission checks
- Huge chained workflows that should become background jobs
