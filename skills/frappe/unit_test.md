One behavior per test; keep tests isolated; use FrappeTestCase.

```python
def test_status_update(self):
    doc = frappe.get_doc("Task", "TASK-001")
    doc.status = "Closed"
    doc.save()
    self.assertEqual(frappe.db.get_value("Task", "TASK-001", "status"), "Closed")
```
