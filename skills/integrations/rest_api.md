# REST API

Use this when the question is about consuming or exposing Frappe HTTP endpoints.

## Read documents through REST

```bash
curl -X GET \
  https://site.local/api/resource/ToDo \
  -H "Authorization: token api_key:api_secret"
```

## Create a document through REST

```bash
curl -X POST \
  https://site.local/api/resource/ToDo \
  -H "Authorization: token api_key:api_secret" \
  -H "Content-Type: application/json" \
  -d '{"description":"Follow up customer","status":"Open"}'
```

## Call a whitelisted method

```bash
curl -X POST \
  https://site.local/api/method/my_app.api.make_invoice \
  -H "Authorization: token api_key:api_secret" \
  -H "Content-Type: application/json" \
  -d '{"sales_order":"SO-0001"}'
```

## Pick the right file

- Use this file for HTTP request patterns.
- Use `whitelist_basic.md` or `whitelist_advanced.md` for server-side method design.
- Use `webhooks.md` when Frappe should push events outward.
