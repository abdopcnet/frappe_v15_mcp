Accounting: create GL entries in on_submit; cancel in on_cancel. Use make_gl_entries pattern.

```python
# In AccountsController: self.make_gl_entries() in on_submit, self.make_gl_entries(cancel=True) in on_cancel
# GL Entry doctype; link to voucher_type, voucher_no, account, debit, credit.
```
