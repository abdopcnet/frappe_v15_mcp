# scheduler_events

Define scheduled tasks in `hooks.py`.

```python
scheduler_events = {
	"daily": ["my_app.tasks.daily_cleanup"]
}
```

## Notes

- Keep jobs idempotent and retry-safe
- Prefer small focused task methods
- Use cron entries only when needed
