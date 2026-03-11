Keep jobs idempotent; pass small serializable args; log start/finish.

```python
def rebuild_cache():
    frappe.logger().info("Rebuild started")
    # ... work ...
    frappe.logger().info("Rebuild done")
frappe.enqueue("my_app.tasks.rebuild_cache", queue="short")
```
