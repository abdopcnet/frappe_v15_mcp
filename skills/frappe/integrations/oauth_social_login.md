# OAuth And Social Login

Use this when the question is about OAuth client setup or login providers.

## Create an OAuth Client

```python
client = frappe.get_doc({
    "doctype": "OAuth Client",
    "app_name": "My Integration",
    "redirect_uris": "https://app.example.com/callback",
    "scopes": "all openid",
    "grant_type": "Authorization Code",
    "response_type": "Code",
})
client.insert(ignore_permissions=True)
```

## Add a social login provider

```python
provider = frappe.get_doc({
    "doctype": "Social Login Key",
    "provider_name": "GitHub",
    "client_id": frappe.get_conf().github_client_id,
    "client_secret": frappe.get_conf().github_client_secret,
    "base_url": "https://github.com/login/oauth",
    "authorize_url": "/authorize",
    "access_token_url": "/access_token",
    "user_info_url": "https://api.github.com/user",
    "enabled": 1,
})
provider.insert(ignore_permissions=True)
```

## Pick the right file

- Use this file for OAuth client and social login configuration.
- Use `rest_api.md` for calling Frappe over HTTP.
- Use `authentication.md` for login/session behavior inside Frappe.
