# restore

Restore a site database from a backup SQL file. Optionally restore public and private file archives.

## Basic (database only)

```bash
bench --site SITENAME restore path/to/database.sql.gz
bench --site SITENAME restore path/to/database.sql
```

If the path is not found, bench looks in `sites/SITENAME/private/backups` and `..`.

## With public and private files

```bash
bench --site SITENAME restore path/to/database.sql.gz \
  --with-public-files path/to/public_files.tar \
  --with-private-files path/to/private_files.tar
```

Use archives produced by `bench backup --with-files` (or `--compress` for .tgz). Encrypted archives use `--encryption-key` or the key from site config.

## Options (from site.py)

| Option | Description |
|--------|-------------|
| `sql-file-path` | (Argument) Path to backup SQL file (.sql or .sql.gz). |
| `--with-public-files` | Path to public files tar/tgz archive. |
| `--with-private-files` | Path to private files tar/tgz archive. |
| `--db-root-username` / `--mariadb-root-username` | DB root user (default: root). |
| `--db-root-password` / `--mariadb-root-password` | DB root password. |
| `--db-name` | Database name (e.g. for new site). |
| `--admin-password` | Administrator password for new site. |
| `--install-app` | Install app after restore (can be repeated). |
| `--force` | Ignore validations and downgrade warnings (not recommended). |
| `--encryption-key` | Key for encrypted backup (or site config). |

## Encrypted backup

If the SQL file is AES-encrypted, bench will use `--encryption-key` if provided, otherwise the key from site config. Same key is used for `--with-public-files` / `--with-private-files` if those are encrypted.

## Examples (from tests)

```bash
# Restore database only
bench --site SITENAME restore path/to/database.sql.gz

# Restore database + public and private files (from fetch_latest_backups)
bench --site SITENAME restore {database} --with-public-files {public} --with-private-files {private}

# Restore after extracting .gz
gunzip path/to/database.sql.gz
bench --site SITENAME restore path/to/database.sql
```

## partial-restore (partial backup)

For backups created with `--include` / `--only` (partial), use `partial-restore` on an **existing** site:

```bash
bench --site SITENAME partial-restore path/to/partial_backup.sql.gz
bench --site SITENAME partial-restore path/to/partial_backup.sql.gz --verbose
```

- Full backup → use `bench restore`.
- Partial backup → use `bench partial-restore` (same site must exist).

## Notes

- Use a maintenance window for production.
- Verify backup paths and site name before running.
- Restore uses a file lock (`site_restore`) so only one restore runs at a time.
- Temporary files created during file extraction are removed after restore.
