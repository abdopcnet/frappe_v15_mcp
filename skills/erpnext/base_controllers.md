ERPNext base controllers: StockController, AccountsController; extend for stock/accounting docs.

```python
# Custom DocType: class MyStockDoc(StockController): ...
# Override validate, on_submit, on_cancel; call super() and then make_sl_entries / make_gl_entries.
```
