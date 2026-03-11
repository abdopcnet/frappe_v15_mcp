Generate PDF from HTML (e.g. print format).

```python
from frappe.utils.pdf import get_pdf
html = frappe.get_print("Sales Invoice", name, print_format="Standard")
pdf = get_pdf(html)
```
