# Transform Database

Use this when the task is a schema or data transformation executed through a patch or migration script.

## Preferred path

```bash
bench --site site.local migrate
```

## Note

Do not treat raw database transformation as an ad-hoc bench habit. Put repeatable changes in patches.
