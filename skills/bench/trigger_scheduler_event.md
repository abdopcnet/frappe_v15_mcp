# Trigger Scheduler Event

Use this when you need to test a scheduler job path manually.

## Example

```bash
bench --site site.local execute frappe.core.doctype.scheduled_job_type.scheduled_job_type.run_scheduled_job --kwargs '{"job_type": "all"}'
```

## Note

For general scheduler health, start with `bench doctor`.
