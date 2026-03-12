# clear-log-table

Delete old rows from a log DocType table.

```bash
bench --site <site> clear-log-table --doctype "Error Log" --days 30
```

## Notes

- Start with conservative `--days`
- Use only for log/maintenance doctypes
