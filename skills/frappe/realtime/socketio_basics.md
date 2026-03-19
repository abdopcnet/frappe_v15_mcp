# SocketIO Basics

Use this when the question is about pushing realtime events from Python to the Desk.

## Publish a custom event

```python
frappe.publish_realtime(
    event="invoice_status_updated",
    message={"name": doc.name, "status": doc.status},
    user=doc.owner,
)
```

## Listen from client script

```javascript
frappe.realtime.on("invoice_status_updated", (data) => {
  frappe.show_alert(`Invoice ${data.name} is now ${data.status}`);
});
```

## Publish to a document room

```python
frappe.publish_realtime(
    event="doc_update",
    message={"doctype": doc.doctype, "name": doc.name},
    doctype=doc.doctype,
    docname=doc.name,
)
```

## Pick the right file

- Use this file for generic realtime events.
- Use `task_progress.md` for progress bar helpers.
- Use `background_jobs.md` and `enqueue.md` for the worker side.
