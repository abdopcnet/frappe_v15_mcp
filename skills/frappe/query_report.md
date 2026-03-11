Report based on SQL: set ref_doctype and query in Report DocType or script.

```python
# In Report DocType: query = "SELECT name, subject FROM tabTask WHERE status = %(status)s"
# Or override get_report_summary, get_data in script.
```
