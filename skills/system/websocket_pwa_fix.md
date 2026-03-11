WebSocket/PWA issues: check apps.txt order, restart gunicorn, nginx keepalive/ws headers, redis_socketio.

```nginx
# nginx: proxy_http_version 1.1; proxy_set_header Upgrade $http_upgrade; proxy_set_header Connection "upgrade";
```
