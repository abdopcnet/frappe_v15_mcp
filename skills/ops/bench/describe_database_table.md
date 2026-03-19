# Describe Database Table

Use this when checking columns or indexes on a physical table.

## Example

```bash
bench --site site.local mariadb
DESCRIBE `tabSales Invoice`;
SHOW INDEX FROM `tabSales Invoice`;
```
