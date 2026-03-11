Log errors and traceback for debugging; creates Error Log doc.

```python
import traceback
frappe.log_error(title="Sync failed", message=traceback.format_exc())
```
