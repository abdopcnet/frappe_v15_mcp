# scheduler_events

Register recurring jobs in `hooks.py` using Frappe scheduler buckets or cron.

## Standard buckets

```python
scheduler_events = {
    "hourly": ["my_app.tasks.sync_hourly"],
    "daily": ["my_app.tasks.daily_cleanup"],
}
```

## Cron entry

```python
scheduler_events = {
    "cron": {
        "0 6 * * *": ["my_app.tasks.run_morning_jobs"],
    }
}
```

## Rules

- Jobs must be idempotent and retry-safe.
- Keep scheduled functions small and move heavy work into `frappe.enqueue()` if needed.
- Use cron only when built-in buckets are not enough.

## Do not use for

- Request-triggered background work; use `enqueue.md`
- Job design guidance; use `background_jobs.md`
