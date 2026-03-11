Set form field values; avoid mutating frm.doc directly. Refresh dependent fields after change.

```javascript
frm.set_value("customer", "CUST-001");
await frm.set_value("customer", "CUST-001");
frm.refresh_field("customer_name");
```
