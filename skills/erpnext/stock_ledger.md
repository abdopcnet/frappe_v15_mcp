Stock Ledger: make_gl_entries equivalent for inventory; use make_sl_entries for stock docs.

```python
# In StockController subclasses (e.g. Stock Entry): update stock via make_sl_entries
# Do not create Stock Ledger Entry directly; use standard APIs.
from erpnext.stock.stock_ledger import make_sl_entries
```
