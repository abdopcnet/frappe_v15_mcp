Restrict list view rows by user/role via hooks; return SQL condition string.

```python
# hooks.py
permission_query_conditions = {
    "Task": "my_app.permissions.task_filter"
}
# my_app.permissions: return "`tabTask`.owner = {user}"  # or similar
```
