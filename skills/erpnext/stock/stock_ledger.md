# Stock Ledger

Use this when the task is about inventory movement history, stock balance, or valuation traces.

## Read stock ledger entries

```python
entries = frappe.get_all(
    "Stock Ledger Entry",
    filters={
        "item_code": item_code,
        "warehouse": warehouse,
        "is_cancelled": 0,
    },
    fields=[
        "posting_date",
        "posting_time",
        "voucher_type",
        "voucher_no",
        "actual_qty",
        "qty_after_transaction",
        "valuation_rate",
        "stock_value_difference",
    ],
    order_by="posting_date desc, posting_time desc",
)
```

## Get current stock balance

```python
from erpnext.stock.utils import get_stock_balance

balance = get_stock_balance(
    item_code="ITEM-001",
    warehouse="Stores - TC",
    posting_date=frappe.utils.today(),
)
```

## Post SLE entries via make_sl_entries

```python
from erpnext.stock.stock_ledger import make_sl_entries

sl_entries = [
    {
        "doctype": "Stock Ledger Entry",
        "item_code": row.item_code,
        "warehouse": row.warehouse,
        "posting_date": self.posting_date,
        "posting_time": self.posting_time,
        "voucher_type": self.doctype,
        "voucher_no": self.name,
        "voucher_detail_no": row.name,
        "actual_qty": row.qty,      # positive for in, negative for out
        "company": self.company,
        "stock_uom": row.stock_uom,
        "incoming_rate": row.valuation_rate or 0,
        "is_cancelled": 0,
    }
]

make_sl_entries(sl_entries, cancel=self.docstatus == 2)
```

## Rules

- Always filter `is_cancelled=0` when reading current stock state.
- Use `get_stock_balance` for point-in-time balance; it handles FIFO/Moving Average.
- `actual_qty` is positive for stock in, negative for stock out.
- On cancel, pass `cancel=True` to `make_sl_entries`.

## Pick the right file

- Use `stock_entry.md` for creating Stock Entry documents.
- Use `gl_entry.md` for accounting postings.
- Use `frappe/data/get_all.md` for general query patterns.
