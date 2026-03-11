Python report: define get_columns, get_data; return list of dicts or rows.

```python
def get_columns(): return [{"label": "Name", "fieldname": "name", "width": 120}]
def get_data(filters): return frappe.get_all("Task", fields=["name"], filters=filters)
```
