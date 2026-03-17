# log_error

Use `frappe.log_error()` for backend exceptions that need a searchable Error Log entry.

## Minimal pattern

Use only two arguments: file identifier and function name.

```python
try:
    run_sync()
except Exception:
    frappe.log_error("filename.*", "defname")
    raise
```

- First argument: module/file identifier (e.g. `"server_script.*"`, `"fixtures.*"`).
- Second argument: name of the function where the exception was caught (e.g. `"export_server_scripts_by_module"`, `"bulk_export_fixtures"`).

## Rules

- First arg: file identifier (e.g. `server_script.*`). Second arg: def name.
- Re-raise when the caller must still fail.
