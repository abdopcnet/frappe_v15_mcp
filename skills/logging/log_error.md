# log_error

Use `frappe.log_error()` for backend exceptions that need a searchable Error Log entry.

## Minimal pattern

```python
try:
    run_sync()
except Exception:
    frappe.log_error(title="task_sync failed", message=frappe.get_traceback())
    raise
```

## Rules

- Use a short searchable title.
- Log tracebacks or compact context, not secrets.
- Re-raise when the caller must still fail.
