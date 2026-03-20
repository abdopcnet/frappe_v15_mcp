# Analyze database tables and processlist

Use to troubleshoot schema/performance issues and to find what blocks `bench migrate` (e.g. metadata lock on a table).

## Analyzing tables and columns

- **Table/column existence:** Use `information_schema` to list tables or columns for a table.
- **Describe a DocType table:** `bench --site SITENAME describe-database-table --doctype "DocType Name"`.
- **Check columns for a table (MariaDB):**
  ```sql
  SELECT COLUMN_NAME, DATA_TYPE, CHARACTER_MAXIMUM_LENGTH
  FROM information_schema.COLUMNS
  WHERE TABLE_SCHEMA = DATABASE() AND TABLE_NAME = 'tabTable Name'
  ORDER BY ORDINAL_POSITION;
  ```

Use this to verify schema matches DocType JSON, plan migrations, or debug missing/wrong columns.

## Who is blocking migrate (metadata lock)

When migrate hangs with "Waiting for table metadata lock" on an `ALTER TABLE`, another session is holding the table. Find and release it.

### 1. List all sessions (include Sleep)

Run in MariaDB (not in shell):

```sql
SELECT id, user, host, db, command, time, state, LEFT(info, 100) AS info
FROM information_schema.processlist
ORDER BY time DESC;
```

- **id:** connection id (use for `KILL`).
- **command:** `Query` = active query; `Sleep` = idle (may still hold locks).
- **time:** seconds the session has been in that state. Long `Sleep` (e.g. thousands of seconds) often holds metadata lock.
- **info:** current or last query; empty for Sleep.

The row with `state = 'Waiting for table metadata lock'` and `info` containing `ALTER TABLE` is the **blocked** migrate. The **blocker** is usually a long-lived `Sleep` (same `db`, high `time`).

### 2. Release the blocking session and re-run migrate

Run these in order. **Do not run `KILL` in the OS shell** — run it inside the MariaDB client.

```bash
bench --site SITENAME mariadb
```

Inside MariaDB:

```sql
KILL <blocking_id>;
exit
```

Then in shell:

```bash
bench --site SITENAME migrate
```

Replace `<blocking_id>` with the `id` of the likely blocker (e.g. the long `Sleep` session). Do not kill the session that shows the `ALTER TABLE` (that is the migrate you want to succeed).

### 3. If migrate already failed

If migrate timed out or was cancelled, run the same steps: open MariaDB, `KILL` the long Sleep connection(s), `exit`, then run `bench --site SITENAME migrate` again.

## Optimization notes

- Use `information_schema.COLUMNS` and `TABLES` to compare schema with DocType definitions.
- Use processlist to spot long-running queries or idle connections holding locks before running DDL (e.g. migrate). Prefer running migrate when the site is idle or in maintenance mode.
