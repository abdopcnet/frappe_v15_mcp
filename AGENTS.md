# Rules

- Investigate before coding and do deep analysis first.
- Use short English comments above non-obvious code sections.
- Follow the Frappe framework conventions.
- Reply to me in should simple english only.
- End replies with ✅ when rules are followed.

## Naming Conventions

- Python: snake_case for functions and variables.
- JavaScript: camelCase for variables, PascalCase for classes.
- DocType: Title Case with spaces.
- Files: snake_case.py, snake_case.js.

## Logging

# Example: log errors only in the frontend (no console.log/info/warn/debug).

```javascript
console.error("[filename.js] short_error_description");
```

# Example: log backend exceptions with frappe.log_error.

```python
frappe.log_error(f"[[filename.py]] method_name")
```

# Bench

# Example: inspect table/column mapping for a DocType.

```bash
bench --site <site> describe-database-table --doctype "Sales Invoice"
```

# Example: run a read-only SQL query through MariaDB.

```bash
bench --site <site> mariadb -e 'SELECT name, dt, enabled FROM `tabClient Script` WHERE dt IN ("Stock Entry", "Stock Entry Detail") ORDER BY enabled DESC, name;'
```

# Example: aggregate results (read-only).

```bash
bench --site <site> mariadb -e 'SELECT dt, COUNT(*) as total FROM `tabDocField` GROUP BY dt ORDER BY total DESC LIMIT 10;'
```
