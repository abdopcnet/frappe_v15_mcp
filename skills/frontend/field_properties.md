# field_properties

Change field metadata at runtime with Frappe form APIs.

## Toggle visibility, read-only, and required

```javascript
frm.toggle_display("completed_on", frm.doc.status === "Completed");
frm.toggle_enable("status", frm.doc.docstatus === 0);
frm.toggle_reqd("customer", frm.doc.is_billable);
```

## Set one property directly

```javascript
frm.set_df_property("priority", "read_only", 1);
frm.set_df_property("task_type", "options", "Bug\nFeature\nSupport");
```

## Rules

- Use toggle helpers for common visibility/editability changes.
- Use `set_df_property()` for less common metadata changes such as options or labels.
- Refresh the field if the UI does not repaint automatically.

## Do not use for

- Permanent metadata customization across sites; use Property Setter or Customize Form.
