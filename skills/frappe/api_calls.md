Call server from client with frappe.call or frappe.xcall; handle callback or Promise.

```javascript
frappe.call({ method: "my_app.api.get_data", args: { name: frm.doc.name } }).then(r => { });
const value = await frappe.xcall("my_app.api.get_data", { name: frm.doc.name });
```
