# Stock Entry

Create Stock Entry documents to record material movements.

## Material Receipt (goods in)

```python
se = frappe.get_doc(
    {
        "doctype": "Stock Entry",
        "stock_entry_type": "Material Receipt",
        "company": "My Company",
        "posting_date": frappe.utils.today(),
        "items": [
            {
                "item_code": "ITEM-001",
                "t_warehouse": "Stores - TC",   # destination warehouse
                "qty": 10,
                "basic_rate": 500,
            }
        ],
    }
)
se.insert()
se.submit()
```

## Material Issue (goods out)

```python
se = frappe.get_doc(
    {
        "doctype": "Stock Entry",
        "stock_entry_type": "Material Issue",
        "company": "My Company",
        "items": [
            {
                "item_code": "ITEM-001",
                "s_warehouse": "Stores - TC",   # source warehouse
                "qty": 5,
            }
        ],
    }
)
se.insert()
se.submit()
```

## Material Transfer

```python
se = frappe.get_doc(
    {
        "doctype": "Stock Entry",
        "stock_entry_type": "Material Transfer",
        "items": [
            {
                "item_code": "ITEM-001",
                "s_warehouse": "Stores - TC",
                "t_warehouse": "Finished Goods - TC",
                "qty": 3,
            }
        ],
    }
)
```

## Common stock_entry_type values

```text
Material Receipt
Material Issue
Material Transfer
Material Transfer for Manufacture
Manufacture
Repack
Send to Subcontractor
```

## Validate before submit

```python
se.set_missing_values()         # fills expense_account, cost_center, etc.
se.calculate_rate_and_amount()  # computes basic_amount, valuation_rate
se.validate()
se.submit()
```

## Rules

- `s_warehouse` = source (required for Issue and Transfer).
- `t_warehouse` = target (required for Receipt and Transfer).
- `basic_rate` is required on Receipt; calculated from FIFO/Moving Average on Issue.
- Always call `set_missing_values()` before submit when building via code.

## Pick the right file

- Use `stock_ledger.md` to read SLE history after a Stock Entry is posted.
- Use `gl_entry.md` for the accounting side of stock valuation.
