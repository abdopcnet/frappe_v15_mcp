# session_management

Read and manage session state in Frappe.

## Read session values

```python
current_user = frappe.session.user
sid = frappe.session.sid
user_type = frappe.session.data.user_type
```

## Clear user sessions

```python
from frappe.sessions import clear_sessions

clear_sessions(user="user@example.com", force=True)
```

## Hook on session creation

```python
on_session_creation = "my_app.api.on_session_created"

def on_session_created(login_manager):
    frappe.logger().info("Login: %s", login_manager.user)
```

## Rules

- Use session data for current-user context, not durable storage.
- Clear sessions when revoking access or forcing re-login.
- Keep login hooks short.
