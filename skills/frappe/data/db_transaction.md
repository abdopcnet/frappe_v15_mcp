# db_transaction

Use manual transaction control only when the default request transaction is not enough.

## Commit or rollback

```python
try:
    frappe.db.set_value("Task", "TASK-0001", "status", "Completed")
    frappe.db.set_value("Task", "TASK-0002", "status", "Completed")
    frappe.db.commit()
except Exception:
    frappe.db.rollback()
    raise
```

## Savepoint

```python
frappe.db.savepoint("before_optional")

try:
    run_optional_step()
except Exception:
    frappe.db.rollback(savepoint="before_optional")
```

## Batch processing

```python
for batch in batches:
    try:
        process_batch(batch)
        frappe.db.commit()
    except Exception:
        frappe.db.rollback()
        raise
```

## Rules

- Normal request handlers already run inside a transaction.
- Use manual commit/rollback for jobs, scripts, and big batch operations.
- Keep transactions short to reduce lock contention.

## Do not use for

- Every small save flow by default
- Hooks that already run inside a managed request transaction
