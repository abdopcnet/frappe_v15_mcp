# gl_entry

Create or query GL entries. Debit and credit must balance.

```python
from erpnext.accounts.general_ledger import make_gl_entries
gl_entries = [{"account": "Debtors - C", "debit": 1000, "credit": 0, "against": "Sales - C", "voucher_type": "Sales Invoice", "voucher_no": doc.name, "posting_date": doc.posting_date, "company": doc.company}, ...]
make_gl_entries(gl_entries)
frappe.get_all("GL Entry", filters={"voucher_no": doc.name}, fields=["account", "debit", "credit"])
```
