Query multiple documents with filters and field list.

```python
tasks = frappe.get_all("Task", filters={"status": "Open"}, fields=["name", "subject"], limit_page_length=20)
```
