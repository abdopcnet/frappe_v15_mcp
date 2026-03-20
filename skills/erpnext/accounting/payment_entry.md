# Payment Entry

Create Payment Entry documents to record incoming/outgoing payments.

## Receive payment from customer

```python
pe = frappe.get_doc(
    {
        "doctype": "Payment Entry",
        "payment_type": "Receive",
        "party_type": "Customer",
        "party": "Acme Corp",
        "company": "My Company",
        "paid_from": "Debtors - TC",
        "paid_to": "Cash - TC",
        "paid_amount": 5000,
        "received_amount": 5000,
        "posting_date": frappe.utils.today(),
    }
)
pe.insert(ignore_permissions=True)
pe.submit()
```

## Pay to supplier

```python
pe = frappe.get_doc(
    {
        "doctype": "Payment Entry",
        "payment_type": "Pay",
        "party_type": "Supplier",
        "party": "ABC Supplies",
        "company": "My Company",
        "paid_from": "Cash - TC",
        "paid_to": "Creditors - TC",
        "paid_amount": 3000,
        "received_amount": 3000,
        "posting_date": frappe.utils.today(),
    }
)
pe.insert(ignore_permissions=True)
pe.submit()
```

## Link to invoice (reconcile outstanding)

```python
pe.append(
    "references",
    {
        "reference_doctype": "Sales Invoice",
        "reference_name": "SINV-0001",
        "due_date": invoice.due_date,
        "total_amount": invoice.grand_total,
        "outstanding_amount": invoice.outstanding_amount,
        "allocated_amount": invoice.outstanding_amount,
    },
)
```

## Create via get_payment_entry helper

```python
from erpnext.accounts.doctype.payment_entry.payment_entry import get_payment_entry

pe = get_payment_entry("Sales Invoice", "SINV-0001")
pe.paid_to = "Cash - TC"
pe.paid_amount = pe.received_amount = pe.total_allocated_amount
pe.save()
pe.submit()
```

## payment_type values

```text
Receive   # customer pays you
Pay       # you pay supplier / employee
Internal Transfer
```

## Rules

- `paid_from` and `paid_to` must be actual account names (with company abbreviation).
- For multi-currency payments, set `source_exchange_rate` and `target_exchange_rate`.
- Use `get_payment_entry()` when reconciling against an existing invoice — it fills
  party, accounts, and reference details automatically.

## Pick the right file

- Use `journal_entry.md` for manual adjustments without a party.
- Use `gl_entry.md` for low-level GL entry patterns.
