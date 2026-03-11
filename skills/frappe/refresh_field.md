Refresh dependent fields after value changes so formulas/fetches run.

```javascript
frm.refresh_field("amount");
frm.refresh_fields(["rate", "qty", "amount"]);
```
