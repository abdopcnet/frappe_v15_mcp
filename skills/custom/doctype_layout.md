# doctype_layout

Use DocType Layout to present alternative field arrangements without changing schema.

## Create a layout document

```python
layout = frappe.get_doc({
    "doctype": "DocType Layout",
    "name": "Task Manager View",
    "document_type": "Task",
    "route": "task-manager",
    "layout": [
        {
            "section": "Task Details",
            "columns": [
                {"fields": [{"fieldname": "subject"}, {"fieldname": "status"}]},
                {"fields": [{"fieldname": "assigned_to"}, {"fieldname": "exp_end_date"}]},
            ],
        }
    ],
})
layout.insert()
```

## Apply conditionally

```javascript
frappe.ui.form.on("Task", {
  onload(frm) {
    if (frappe.user.has_role("Task Manager")) {
      frappe.call({
        method: "frappe.client.get",
        args: { doctype: "DocType Layout", name: "Task Manager View" },
        callback: (r) => frm.apply_custom_layout(r.message),
      });
    }
  },
});
```

## Rules

- Use layouts to change arrangement, not database structure.
- Keep layout variants role- or route-driven.
- Use it when Customize Form is not enough for presentation differences.
