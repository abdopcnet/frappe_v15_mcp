# Publish Realtime From Bench

Use this when you want to trigger a realtime event manually through bench console.

## Example

```bash
bench --site site.local console
frappe.publish_realtime("custom_event", {"status": "ok"}, user="Administrator")
```

## Note

Use app code for repeatable realtime behavior. Bench console is for debugging.
