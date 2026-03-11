# mariadb-query

Run a SQL query through bench using MariaDB.

```bash
bench --site <site> mariadb -e 'SELECT name, dt, enabled FROM `tabClient Script` WHERE dt IN ("Stock Entry", "Stock Entry Detail") ORDER BY enabled DESC, name;'
```

## Notes

- Use backticks for table names that contain spaces (e.g. `` `tabClient Script` ``).
- Use single quotes around the `-e` argument when the query contains double-quoted strings (e.g. `"Stock Entry"`).
- Prefer read-only queries; use backups before destructive SQL.
