List fixtures in hooks to load on install (e.g. Custom Field, Role).

```python
# hooks.py
fixtures = [
    {"dt": "Custom Field", "filters": [{"name": ["like", "%-my_%"]}]},
]
```
