# Stock Ledger

Use one stock ledger query to review quantity movement for an item.

```python
sle = frappe.get_all("Stock Ledger Entry", filters={"item_code": item_code}, fields=["posting_date", "actual_qty"])
```

- Include warehouse filters when needed
- Check posting date ordering
- Use for stock reconciliation checks
