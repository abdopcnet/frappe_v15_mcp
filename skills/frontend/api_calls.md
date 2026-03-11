# api_calls

Call whitelisted backend methods from the client.

```javascript
frappe.call({
  method: "app.module.method_name",
  args: { key: "value" },
  freeze: true,
  callback(r) { if (r.message) frm.reload_doc(); },
});
let result = await frappe.xcall("app.module.method", { key: "value" });
```

Validate on server; handle missing response safely.
