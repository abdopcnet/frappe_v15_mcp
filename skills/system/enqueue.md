Run heavy work in background; pass small serializable args. Prefer short/default queue.

```python
frappe.enqueue("my_app.tasks.rebuild_report", queue="short", report_name="Sales")
```
