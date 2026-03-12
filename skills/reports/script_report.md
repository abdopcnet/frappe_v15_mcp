# Script Report

Use one `execute` function to return columns and rows from Python logic.

```python
def execute(filters=None):
    columns = [{"fieldname": "name", "label": "Name", "fieldtype": "Data"}]
    data = frappe.get_all("Task", fields=["name"], limit=20)
    return columns, data
```

- Keep output schema stable
- Use filters defensively
- Return only required rows
