# websocket_pwa_fix

Quick checklist for realtime, Socket.IO, or PWA issues in production.

## Check app load order

```text
sites/apps.txt
base_app
override_app
```

Put the overriding app after the base app.

## Restart stale web or socket workers

```bash
sudo supervisorctl restart frappe-bench-web:frappe-bench-frappe-web
sudo supervisorctl restart frappe-bench-web:frappe-bench-node-socketio
```

## Separate Redis roles

```json
{
  "redis_cache": "redis://127.0.0.1:13000",
  "redis_socketio": "redis://127.0.0.1:11000"
}
```

## Nginx websocket headers

```nginx
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection $connection_upgrade;
proxy_read_timeout 600;
```

## Rules

- Restart services after config changes.
- Keep `redis_socketio` separate from cache Redis.
- Verify proxy upgrade headers before debugging application code.
