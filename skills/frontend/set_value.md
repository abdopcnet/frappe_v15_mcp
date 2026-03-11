# set_value

Get/set form field values.

```javascript
let value = frm.doc.field_name;
frm.set_value("field_name", "value");
await frm.set_value("field_name", "value");
```

Prefer `set_value` over direct mutation. Refresh dependent fields if needed.
