# Excel Utils

Use one utility call to build an XLSX payload for export workflows.

```python
from frappe.utils.xlsxutils import make_xlsx
content = make_xlsx([["Item", "Qty"], ["ITEM-001", 5]], "Items")
```

- Keep header row stable
- Use UTF-8 compatible text
- Attach the file after generation
