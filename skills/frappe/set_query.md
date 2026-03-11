Filter Link field options; return filters dict or function that returns filters.

```javascript
frm.set_query("customer", () => ({ filters: { "customer_group": "Standard" } }));
frm.set_query("item", "items", () => ({ query: "my_app.queries.item_filter" }));
```
