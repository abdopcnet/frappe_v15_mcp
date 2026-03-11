# backup

Create site backup. Output goes to `sites/SITENAME/private/backups` unless overridden.

## Basic

```bash
bench --site SITENAME backup
```

## With files (public + private)

```bash
bench --site SITENAME backup --with-files
bench --site SITENAME backup --with-files --compress
```

`--with-files` includes public and private file archives. Use the same paths with `bench restore --with-public-files` / `--with-private-files` when restoring.

## Options (from site.py)

| Option | Description |
|--------|-------------|
| `--with-files` | Include public and private files in backup (flag). |
| `--compress` | Compress private and public file archives (e.g. .tgz). |
| `--include` / `--only` / `-i` | DocTypes to backup (comma-separated). |
| `--exclude` / `-e` | DocTypes to exclude (comma-separated). |
| `--backup-path` | Directory for all backup outputs. |
| `--backup-path-db` | Path for database file only. |
| `--backup-path-files` | Path for public files archive. |
| `--backup-path-private-files` | Path for private files archive. |
| `--backup-path-conf` | Path for config file. |
| `--ignore-backup-conf` | Ignore excludes/includes from site config. |
| `--verbose` | Verbose output. |
| `--old-backup-metadata` | Use older backup metadata format. |

## Examples (from tests)

```bash
# Backup without options (DB only)
bench --site SITENAME backup

# Backup with files
bench --site SITENAME backup --with-files

# Backup with files and compress
bench --site SITENAME backup --with-files --compress

# Backup ignoring backup config
bench --site SITENAME backup --ignore-backup-conf --with-files

# Backup to custom directory
bench --site SITENAME backup --backup-path /path/to/backups

# Backup only specific DocTypes (include)
bench --site SITENAME backup --include "ToDo,User"

# Backup excluding DocTypes
bench --site SITENAME backup --exclude "ToDo"
```

## Notes

- Run before destructive operations.
- If backup encryption is enabled, note the encryption key for restore.
- For partial backup (specific DocTypes), use `--include` or `--exclude`; restore partial backups with `bench partial-restore`, not `bench restore`.
