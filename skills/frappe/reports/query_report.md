# Query Report

Use this when SQL alone is enough and you want a standard Query Report.

## Minimal query report SQL

```sql
SELECT
    name,
    customer,
    posting_date,
    grand_total
FROM `tabSales Invoice`
WHERE docstatus = 1
  AND posting_date BETWEEN %(from_date)s AND %(to_date)s
ORDER BY posting_date DESC
```

## Typical filter definition

```javascript
frappe.query_reports["Sales Register"] = {
  filters: [
    {
      fieldname: "from_date",
      label: "From Date",
      fieldtype: "Date",
      reqd: 1,
    },
    {
      fieldname: "to_date",
      label: "To Date",
      fieldtype: "Date",
      reqd: 1,
    },
  ],
};
```

## Pick the right file

- Use this file when the report logic can stay in SQL.
- Use `script_report.md` when you need Python logic, charts, or post-processing.
