# listview_customization

Customize Desk list view behavior with `frappe.listview_settings`.

## Basic list settings

```javascript
frappe.listview_settings["Task"] = {
  get_indicator(doc) {
    if (doc.status === "Completed") {
      return [__("Completed"), "green", "status,=,Completed"];
    }
  },
};
```

## Add bulk action button

```javascript
frappe.listview_settings["Task"] = {
  onload(listview) {
    listview.page.add_inner_button(__("Bulk Close"), () => {
      const rows = listview.get_checked_items();
      frappe.call({
        method: "my_app.api.bulk_close_tasks",
        args: { names: rows.map((row) => row.name) },
        callback: () => listview.refresh(),
      });
    });
  },
};
```

## Row button

```javascript
frappe.listview_settings["Task"] = {
  button: {
    show(doc) {
      return doc.status !== "Cancelled";
    },
    get_label() {
      return __("Process");
    },
    action(doc) {
      frappe.call({ method: "my_app.api.process_task", args: { task: doc.name } });
    },
  },
};
```

## Rules

- Keep list view logic fast; only the list data is available.
- Use indicators for status, not as a substitute for backend rules.
- Refresh the list after bulk actions.
