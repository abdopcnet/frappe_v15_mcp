# safe_execution

Use `safe_exec` for restricted execution of trusted user-configurable Python snippets.

## Execute restricted code

```python
from frappe.utils.safe_exec import safe_exec

_locals = {"email": "user@example.com"}

safe_exec(
    'result = frappe.db.get_value("User", email, "full_name")',
    _locals=_locals,
    restrict_commit_rollback=True,
)
```

## Rules

- Use safe execution only where Frappe already expects restricted scripting.
- Assume imports, shell access, and raw SQL are blocked.
- Keep execution snippets short and deterministic.
