# log_error

Log backend exceptions with `frappe.log_error`.

```python
frappe.log_error(f"[[filename.py]] method_name")
```

## Notes

- Include filename and method name
- Keep message short and searchable
- Do not log secrets
