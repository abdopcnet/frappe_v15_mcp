# Background Jobs

Use one enqueue call to move heavy work out of request/response flow.

```python
frappe.enqueue("my_app.tasks.rebuild_cache", queue="short")
```

- Keep jobs idempotent
- Pass small serializable arguments
- Log start and finish states
