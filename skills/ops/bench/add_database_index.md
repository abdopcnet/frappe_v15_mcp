# Add Database Index

Use this when you need a targeted SQL index during troubleshooting or a migration.

## Example

```bash
bench --site site.local mariadb
ALTER TABLE `tabSales Invoice` ADD INDEX idx_customer_posting_date (customer, posting_date);
```

## Note

Prefer adding permanent indexes through a patch, not manual production edits only.
