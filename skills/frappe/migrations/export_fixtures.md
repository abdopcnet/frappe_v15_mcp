# export_fixtures

Export configured fixture records from a site into app JSON files.

## Command

```bash
bench --site SITENAME export-fixtures --app my_app
```

## Rules

- Define fixture filters in `hooks.py`.
- Export only what should ship with the app.
- Commit the generated JSON files to version control.
