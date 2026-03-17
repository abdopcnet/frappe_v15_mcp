# Restore

Use this when restoring a full site database backup.

## Example

```bash
bench --site site.local restore /backups/site.local-database.sql.gz
```

## With files afterward

```bash
bench --site site.local restore /backups/site.local-database.sql.gz --with-public-files /backups/public-files.tar --with-private-files /backups/private-files.tar
```
