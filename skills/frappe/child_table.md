Add/clear child rows; bind grid events via frm.fields_dict and grid.form.

```javascript
frm.add_child("items", { item_code: "ITEM-01", qty: 1 });
frm.clear_table("items");
frm.fields_dict["items"].grid.get_selected().forEach(row => { });
```
