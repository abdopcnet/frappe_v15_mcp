# system_console

Choose between System Console and `bench execute` based on execution scope.

## Use System Console when

- You need a quick site-scoped diagnostic snippet
- Restricted execution is acceptable
- You want to inspect data interactively from the UI

## Use bench execute when

- The code needs full app imports or unrestricted Frappe APIs
- You need repeatable command-line execution
- The task may call commits, property setters, or broader automation

## bench execute example

```bash
bench --site SITENAME execute my_app.scripts.rebuild_indexes
```

## Console-safe read example

```python
frappe.db.get_value("System Settings", None, "time_zone")
```

## Rules

- Prefer read-only inspection in System Console.
- Prefer `bench execute` for scripts you may need to re-run.
- Avoid destructive operations in ad-hoc console sessions.

## Do not use for

- Long data migrations
- Large repeatable admin tasks that should live in app code or bench commands
