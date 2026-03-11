Write tests with FrappeTestCase; use setUp/tearDown for test data.

```python
from frappe.tests.utils import FrappeTestCase
class TestTask(FrappeTestCase):
    def test_validation(self):
        self.assertRaises(frappe.ValidationError, lambda: frappe.get_doc({"doctype": "Task"}).insert())
```
