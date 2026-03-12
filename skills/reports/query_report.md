# query_report

SQL-based report: set report_type "Query Report" and set `query` to one SQL string.

```json
"query": "SELECT name, customer, grand_total FROM `tabSales Invoice` WHERE docstatus = 1 AND customer = %(customer)s"
```

Use `%(filter_name)s` for report filters. Optional JS: `frappe.query_reports["Report Name"] = { formatter: function(...) {} }`. No write operations in query.
