# base_controllers

Inherit ERPNext controllers; call super() and keep overrides minimal.

```python
from erpnext.controllers.accounts_controller import AccountsController
class MyDoc(AccountsController):
    def validate(self): super().validate()
```
AccountsController: `get_gl_dict()`, `make_gl_entries()`. StockController: `update_stock_ledger()`, `get_sl_entries()`, `make_sl_entries()`.
