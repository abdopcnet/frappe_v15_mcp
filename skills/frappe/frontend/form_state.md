# form_state

Check document state, dirty state, and `docstatus` before acting in the UI.

## New vs saved

```javascript
frappe.ui.form.on("Task", {
  refresh(frm) {
    if (frm.is_new()) {
      frm.set_intro(__("Fill the form and save first"), "blue");
    }

    if (!frm.is_new()) {
      frm.add_custom_button(__("Duplicate"), () => frm.copy_doc());
    }
  },
});
```

## Dirty state

```javascript
if (frm.is_dirty()) {
  frappe.show_alert({ message: __("You have unsaved changes"), indicator: "orange" });
}

frm.dirty();
```

## docstatus gates

```javascript
if (frm.doc.docstatus === 0) {
  // draft
}

if (frm.doc.docstatus === 1) {
  // submitted
}

if (frm.doc.docstatus === 2) {
  // cancelled
}
```

## Permission-aware state

```javascript
if (!frm.perm[0].write) {
  frm.set_intro(__("You have read-only access"), "blue");
}
```

## Rules

- Check state before adding actions or changing UI.
- Use `is_new()` and `docstatus` as the first branch points.
- Use `dirty()` only when script-driven changes should force a save prompt.

## Do not use for

- Field mutation details; use `set_value.md`
- Lifecycle event descriptions; use `form_events.md`
