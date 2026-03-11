Use scrub, comma_or, get_link_to_form for strings and links.

```python
from frappe.utils import scrub, get_link_to_form
slug = scrub("My DocType")
link = get_link_to_form("Task", "TASK-001")
```
