# WebSocket and PWA fix steps

Use when realtime (socket.io), WebSocket, or PWA is broken or slow: wrong app loaded, stale gunicorn code, nginx/redis/Cloudflare misconfiguration.

## 1. apps.txt order (override app not loaded)

**Problem:** Frappe loads a module from the wrong app (e.g. `hrms` instead of `hrms_custom`).
**Cause:** Override app is listed **before** the base app in `apps.txt`; Frappe resolves in reversed order.

**Fix:** In `sites/apps.txt`, put the **override app after** the base app:
```
...
hrms
hrms_custom    # must be after hrms
...
```

---

## 2. Gunicorn stale module in memory

**Problem:** Web serves old code (e.g. bug still present after code change).
**Cause:** Gunicorn `--preload` loads code once at startup; workers do not reload.

**Fix:** Restart web via supervisor (replace with your bench and process names):
```bash
sudo supervisorctl restart frappe-bench-15-web:frappe-bench-15-frappe-web
```

---

## 3. nginx upstream keepalive

**Problem:** Every request opens a new TCP connection to gunicorn (slow).

**Fix:** In nginx conf (e.g. `/etc/nginx/conf.d/frappe-bench-15.conf`), add `keepalive N` to the upstream:
```nginx
upstream frappe-bench-15-frappe {
    keepalive 16;
    server 127.0.0.1:8000 fail_timeout=0;
}
```
Then `sudo nginx -s reload`.

---

## 4. redis_socketio shared with redis_cache

**Problem:** Socket.io and cache share the same Redis (port) — pub/sub conflict or failures.

**Fix:** In `sites/common_site_config.json`, set `redis_socketio` to a **different** Redis port than `redis_cache`:
```json
"redis_socketio": "redis://127.0.0.1:11000"
```
Then restart socketio:
```bash
sudo supervisorctl restart frappe-bench-15-web:frappe-bench-15-node-socketio
```

---

## 5. nginx WebSocket headers

**Problem:** WebSocket upgrade fails behind proxy (e.g. Cloudflare); nginx sends static `Connection: upgrade` instead of mapping `$http_upgrade`.

**Fix:** In nginx config:
- Add a `map` for upgrade:
```nginx
map $http_upgrade $connection_upgrade {
    default upgrade;
    ''      close;
}
```
- In `location /socket.io`, use the mapped variable and set timeouts:
```nginx
location /socket.io {
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection $connection_upgrade;
    proxy_set_header X-Forwarded-For $remote_addr;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Frappe-Site-Name YOUR_<site>;
    proxy_set_header Origin $scheme://$http_host;
    proxy_set_header Host $host;
    proxy_read_timeout 600;
    proxy_send_timeout 600;
    proxy_pass http://YOUR_BENCH-socketio-server;
}
```
Then `sudo nginx -s reload`.

---

## 6. Cloudflare (manual)

If the site is behind Cloudflare:

| Setting    | Where              | Value        |
|-----------|--------------------|-------------|
| WebSockets| Network            | **ON**      |
| SSL Mode  | SSL/TLS → Overview | **Full** (not Flexible) |

---

## 7. Latency (geography)

If server and users are far apart (e.g. server in Europe, users in Gulf), RTT adds 200–500 ms per request. The only structural fix is moving the server closer (e.g. region migration).
