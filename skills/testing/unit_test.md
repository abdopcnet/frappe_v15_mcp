# unit_test

Write a unit test with FrappeTestCase.

```python
from frappe.tests.utils import FrappeTestCase
class TestTask(FrappeTestCase):
    def test_subject_required(self):
        self.assertRaises(frappe.ValidationError, frappe.get_doc, {"doctype": "Task"})
```

Keep tests isolated; one core behavior per test.
