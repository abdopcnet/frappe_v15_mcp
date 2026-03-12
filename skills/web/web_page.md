# web_page

Public page: `get_context(context)` and Jinja template.

```python
def get_context(context):
    context.title = "Products"
    context.items = frappe.get_all("Item", filters={"disabled": 0}, fields=["name", "item_name"])
```
Template: extend `templates/web.html`, use `{{ title }}`, `{% for item in items %}`. Keep context small; sanitize output.
