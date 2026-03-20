# Journal Entry

Create Journal Entry documents programmatically for manual accounting adjustments.

## Basic Journal Entry

```python
je = frappe.get_doc(
    {
        "doctype": "Journal Entry",
        "voucher_type": "Journal Entry",
        "posting_date": frappe.utils.today(),
        "company": "My Company",
        "accounts": [
            {
                "account": "Cash - TC",
                "debit_in_account_currency": 1000,
                "credit_in_account_currency": 0,
            },
            {
                "account": "Sales - TC",
                "debit_in_account_currency": 0,
                "credit_in_account_currency": 1000,
            },
        ],
    }
)
je.insert(ignore_permissions=True)
je.submit()
```

## Journal Entry linked to a document

```python
je = frappe.get_doc(
    {
        "doctype": "Journal Entry",
        "voucher_type": "Credit Note",
        "posting_date": doc.posting_date,
        "company": doc.company,
        "remark": f"Credit against {doc.name}",
        "accounts": [
            {
                "account": doc.debit_to,
                "party_type": "Customer",
                "party": doc.customer,
                "debit_in_account_currency": 0,
                "credit_in_account_currency": doc.outstanding_amount,
                "reference_type": doc.doctype,
                "reference_name": doc.name,
            },
            {
                "account": "Write Off Account - TC",
                "debit_in_account_currency": doc.outstanding_amount,
                "credit_in_account_currency": 0,
            },
        ],
    }
)
je.insert(ignore_permissions=True)
je.submit()
```

## Common voucher_type values

```text
Journal Entry
Bank Entry
Cash Entry
Credit Note
Debit Note
Write Off Entry
Opening Entry
Depreciation Entry
```

## Rules

- Total debits must equal total credits across all account rows.
- `debit_in_account_currency` / `credit_in_account_currency` are the amounts in
  the account's currency; Frappe converts to base currency automatically.
- Linked references (`reference_type`, `reference_name`) mark outstanding entries
  for payment reconciliation.

## Pick the right file

- Use `gl_entry.md` for low-level `make_gl_entries` patterns.
- Use `payment_entry.md` for payment receipts and payments to parties.
