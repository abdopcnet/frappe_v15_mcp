# trigger_scheduler_event

Run scheduler events manually.

```bash
bench --site SITENAME trigger-scheduler-event all
bench --site SITENAME trigger-scheduler-event hourly
bench --site SITENAME trigger-scheduler-event daily
```

Use for validation/debug. Events: hourly, daily, weekly, monthly, cron.
