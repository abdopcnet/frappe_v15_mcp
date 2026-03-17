# enqueue

Queue work with `frappe.enqueue()` or `frappe.enqueue_doc()`.

## Queue a Python function

```python
frappe.enqueue(
    "my_app.tasks.rebuild_cache",
    queue="short",
    timeout=300,
    customer="CUST-0001",
)
```

## Queue a document method

```python
frappe.enqueue_doc(
    "Sales Invoice",
    "SINV-0001",
    "submit",
    queue="long",
    timeout=1500,
)
```

## Typical queues

- `short` for quick jobs
- `default` for normal work
- `long` for expensive jobs

## Rules

- Pass primitive args, not document objects.
- Set an explicit timeout for heavy work.
- Prefer `enqueue_doc()` when the logic is already a document method.

## Do not use for

- Scheduler configuration
- Job design guidance; use `background_jobs.md`
