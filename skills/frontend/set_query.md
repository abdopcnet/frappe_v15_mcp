# set_query

Filter Link field options.

```javascript
frm.set_query("customer", () => ({ filters: { disabled: 0 } }));
frm.set_query("item_code", () => ({ filters: { item_group: frm.doc.item_group } }));
```

Use in `refresh`. Return object with `filters` (and optional `query`).
