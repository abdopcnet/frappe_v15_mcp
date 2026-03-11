Build or read Excel with frappe.utils.xlsxutils.

```python
from frappe.utils.xlsxutils import make_xlsx
data = [["Name", "Status"], ["TASK-001", "Open"]]
xlsx = make_xlsx(data, "Report")
frappe.response.filename = "report.xlsx"
frappe.response.filecontent = xlsx.getvalue()
frappe.response.type = "download"
```
