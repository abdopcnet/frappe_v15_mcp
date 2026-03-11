# get_all

Use one `frappe.get_all` query to fetch multiple records efficiently.

```python
rows = frappe.get_all("Customer", filters={"disabled": 0}, fields=["name", "customer_name"])
```

- Select only required fields
- Add filters to reduce scan cost
- Use pagination for large datasets
