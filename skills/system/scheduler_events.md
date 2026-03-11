Schedule background tasks: cron, hourly, daily, weekly in hooks.py.

```python
# hooks.py
scheduler_events = {
    "hourly": ["my_app.tasks.hourly_sync"],
    "daily": ["my_app.tasks.daily_report"],
}
```
