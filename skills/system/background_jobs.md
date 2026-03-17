# background_jobs

Design background jobs so they are safe, small, and retry-friendly.

## Good job shape

```python
def rebuild_cache(customer):
    if not customer:
        return

    frappe.logger().info("Rebuilding cache for %s", customer)
    frappe.cache().delete_value(f"customer:{customer}")
```

## Trigger from request flow

```python
frappe.enqueue("my_app.tasks.rebuild_cache", customer=doc.customer, queue="short")
```

## Rules

- Keep jobs idempotent.
- Pass small serializable arguments.
- Re-load documents inside the job instead of passing big objects.
- Log start/failure points for debugging.

## Do not use for

- Tiny synchronous operations that finish inside the request
- Complex transaction chains that depend on in-memory document state

Use `enqueue.md` for the actual enqueue API patterns.
