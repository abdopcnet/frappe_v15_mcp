# Script Report

Use this when the report needs Python logic, computed columns, or chart data.

## Minimal execute function

```python
def execute(filters=None):
    columns = [
        {"label": "Invoice", "fieldname": "name", "fieldtype": "Link", "options": "Sales Invoice"},
        {"label": "Customer", "fieldname": "customer", "fieldtype": "Link", "options": "Customer"},
        {"label": "Outstanding", "fieldname": "outstanding_amount", "fieldtype": "Currency"},
    ]

    data = frappe.get_all(
        "Sales Invoice",
        filters={"docstatus": 1},
        fields=["name", "customer", "outstanding_amount"],
        order_by="modified desc",
    )

    return columns, data
```

## Return chart data

```python
return columns, data, None, {
    "data": {
        "labels": ["Paid", "Unpaid"],
        "datasets": [{"values": [paid_count, unpaid_count]}],
    },
    "type": "donut",
}
```

## Pick the right file

- Use this file for Python-backed reports.
- Use `query_report.md` when pure SQL is enough.
