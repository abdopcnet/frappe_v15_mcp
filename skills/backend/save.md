# save

Update and save an existing document.

```python
doc = frappe.get_doc("Task", "TASK-0001")
doc.status = "Completed"
doc.save()
```

## Notes

- Use `insert()` for new documents
- Use `reload()` after external updates
