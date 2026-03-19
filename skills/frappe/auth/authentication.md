# authentication

Core authentication patterns in Frappe.

## Check logged-in user

```python
if frappe.session.user != "Guest":
    pass
```

## Programmatic login

```python
from frappe.auth import LoginManager

login_manager = LoginManager()
login_manager.authenticate(user="user@example.com", pwd="password")
login_manager.post_login()
```

## Check password

```python
from frappe.utils.password import check_password

check_password("user@example.com", "password")
```

## API token auth

```text
Authorization: token api_key:api_secret
```

## Rules

- Prefer built-in auth flows over custom password logic.
- Treat API keys and secrets as credentials.
- Keep guest access explicit, never implicit.
