Database migrations: add Python file in app/patches/; run once per site.

```python
# my_app/patches/v15_0/add_my_column.py
import frappe
def execute():
    frappe.db.commit()
    # frappe.db.sql("ALTER TABLE tabTask ADD COLUMN my_col VARCHAR(140)")
```
