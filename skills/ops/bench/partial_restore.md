# Partial Restore

Use this when restoring only selected tables or data paths by manual database work.

## Example

```bash
bench --site site.local mariadb
SOURCE /path/to/partial_dump.sql;
```

## Note

Frappe has no universal safe partial-restore command. Treat this as advanced database work.
