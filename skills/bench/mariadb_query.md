# MariaDB Query

Use this when you need to run a one-off SQL statement against a MariaDB-backed site.

## Example

```bash
bench --site site.local mariadb
SELECT name, customer FROM `tabSales Invoice` ORDER BY modified DESC LIMIT 10;
```

## Note

Prefer read queries first. Use transactions carefully for writes.
