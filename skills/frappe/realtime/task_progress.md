# Task Progress

Use this when a long-running task should report progress to the UI.

## Publish progress from Python

```python
for index, row in enumerate(rows, start=1):
    process_row(row)
    frappe.publish_progress(
        percent=index * 100 / len(rows),
        title="Importing rows",
        description=f"Processed {index} of {len(rows)}",
    )
```

## Progress inside a background job

```python
def import_customers(rows):
    total = len(rows)
    for index, row in enumerate(rows, start=1):
        create_customer(row)
        frappe.publish_progress(
            percent=index * 100 / total,
            title="Customer import",
            description=row.get("customer_name"),
        )
```

## Pick the right file

- Use this file for `frappe.publish_progress()`.
- Use `socketio_basics.md` for custom realtime events.
- Use `enqueue.md` when the task should run in the queue.
