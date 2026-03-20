# app_hooks

Common `hooks.py` entries beyond `doc_events`.

## App identity

```python
app_name = "my_app"
app_title = "My App"
app_publisher = "My Company"
app_description = "Description"
app_version = "1.0.0"
```

## On login / logout

```python
on_login = "my_app.auth.on_login"
on_logout = "my_app.auth.on_logout"
```

```python
def on_login(login_manager):
    user = login_manager.user
    frappe.db.set_value("User", user, "last_login_ip", frappe.local.request_ip)
```

## Scheduler jobs

```python
scheduler_events = {
    "daily": ["my_app.tasks.sync_daily"],
    "hourly": ["my_app.tasks.refresh_cache"],
    "cron": {
        "0 9 * * 1-5": ["my_app.tasks.send_morning_report"],
    },
}
```

## Fixtures

```python
fixtures = [
    "Custom Field",
    "Property Setter",
    {"dt": "Role", "filters": [["role_name", "like", "My App%"]]},
]
```

## Override standard controllers

```python
override_doctype_class = {
    "Sales Order": "my_app.overrides.CustomSalesOrder",
}
```

## Jinja environment additions

```python
jinja = {
    "methods": ["my_app.utils.jinja_helpers.format_currency"],
    "filters": ["my_app.utils.jinja_helpers.to_arabic"],
}
```

## Website routing

```python
website_route_rules = [
    {"from_route": "/my-page/<path:name>", "to_route": "my-page"},
]
```

## Override whitelisted methods

```python
override_whitelisted_methods = {
    "frappe.desk.search.search_widget": "my_app.overrides.custom_search_widget",
}
```

## Permission query conditions (list/search filtering)

```python
permission_query_conditions = {
    "Sales Order": "my_app.permissions.sales_order_query_conditions",
}
```

## Rules

- Keep hooks.py as a registry only; put logic in imported modules.
- Use `doc_events.md` for event handler wiring.
- Use `scheduler_events.md` for job scheduling details.
