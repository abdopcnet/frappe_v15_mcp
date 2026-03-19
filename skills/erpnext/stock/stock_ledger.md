# Stock Ledger

Use this when the task is about inventory movement history or stock valuation traces.

## Read stock ledger entries

```python
entries = frappe.get_all(
    "Stock Ledger Entry",
    filters={
        "item_code": item_code,
        "warehouse": warehouse,
    },
    fields=["posting_date", "actual_qty", "qty_after_transaction", "valuation_rate"],
    order_by="posting_date desc, posting_time desc",
)
```

## Pick the right file

- Use this file for stock movement queries.
- Use `gl_entry.md` for accounting postings.
