# frontend_logging

Use browser logging sparingly and avoid noisy console output in shipped client scripts.

## Error-only pattern

```javascript
console.error("[task.js] failed to load task summary");
```

## Rules

- Log errors only.
- Keep messages short and searchable.
- Never log secrets or sensitive payloads.
