# frontend_logging

Log errors only; keep messages short.

```javascript
console.error("[filename.js] short_error_description");
```

Do not use console.log/info/warn/debug. No sensitive data. Remove noisy logs before release.
