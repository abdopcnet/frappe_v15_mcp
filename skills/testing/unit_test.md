# Unit Test

Use this when the question is about testing small functions without much document setup.

## Test a helper function

```python
import unittest
from my_app.utils import normalize_phone

class TestNormalizePhone(unittest.TestCase):
    def test_keeps_country_code(self):
        self.assertEqual(normalize_phone("+966 555 000 111"), "+966555000111")
```

## Test a whitelisted helper through Frappe test case

```python
from frappe.tests.utils import FrappeTestCase
from my_app.api import build_summary

class TestBuildSummary(FrappeTestCase):
    def test_build_summary_returns_expected_keys(self):
        result = build_summary("CUST-0001")
        self.assertIn("customer", result)
        self.assertIn("balance", result)
```

## Pick the right file

- Use this file for small isolated test examples.
- Use `frappe_test_case.md` when the topic is document/database test structure.
