# Excel Utils

Use this when the task is to return an XLSX file from Python.

## Build an XLSX file

```python
from frappe.utils.xlsxutils import make_xlsx

rows = [
    ["Customer", "Outstanding"],
    ["CUST-0001", 1500],
    ["CUST-0002", 2750],
]

xlsx_file = make_xlsx(rows, "Outstanding Customers")
```

## Send as a download response

```python
frappe.response.filename = "outstanding_customers.xlsx"
frappe.response.filecontent = xlsx_file.getvalue()
frappe.response.type = "binary"
```

## Pick the right file

- Use this file for XLSX creation.
- Use `file_upload.md` for saving files into File records.
