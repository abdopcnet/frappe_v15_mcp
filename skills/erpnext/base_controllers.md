# ERPNext Base Controllers

Use this when extending ERPNext transactional DocTypes that already rely on base controller logic.

## Inherit from an ERPNext controller

```python
from erpnext.controllers.selling_controller import SellingController

class CustomSalesOrder(SellingController):
    def validate(self):
        super().validate()
        self.custom_total_qty = sum(row.qty for row in self.items)
```

## Pick the right file

- Use this file for ERPNext controller inheritance patterns.
- Use `controller_lifecycle.md` for generic Frappe document hooks.
