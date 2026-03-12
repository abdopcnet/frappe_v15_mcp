# frappe_test_case

Same as unit_test: use FrappeTestCase, one behavior per test.

```python
from frappe.tests.utils import FrappeTestCase
class TestTask(FrappeTestCase):
    def test_subject_required(self):
        self.assertRaises(frappe.ValidationError, frappe.get_doc, {"doctype": "Task"})
```
