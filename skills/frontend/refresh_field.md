# refresh_field

Use `refresh_field()` only when the UI must re-render after manual or structural changes.

## Refresh one field

```javascript
frm.doc.custom_html = "<b>Updated</b>";
frm.refresh_field("custom_html");
```

## Refresh multiple fields

```javascript
frm.refresh_fields(["status", "priority", "exp_end_date"]);
```

## Refresh a child table after structural changes

```javascript
frm.clear_table("items");
frm.add_child("items", { item_code: "ITEM-001", qty: 1 });
frm.refresh_field("items");
```

## After property changes

```javascript
frm.set_df_property("completed_on", "hidden", frm.doc.status !== "Completed");
frm.refresh_field("completed_on");
```

## Rules

- `frm.set_value()` usually updates display already.
- Refresh manually after direct `frm.doc` mutation or child table restructuring.
- Use `refresh_fields()` when several fields need repainting together.

## Do not use for

- Setting values as the main operation; use `set_value.md`
- State decisions; use `form_state.md`
