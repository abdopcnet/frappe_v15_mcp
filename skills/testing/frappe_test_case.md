# Frappe Test Case

Use this when writing database-aware tests in Frappe.

## Minimal test case

```python
from frappe.tests.utils import FrappeTestCase

class TestCustomer(FrappeTestCase):
    def test_customer_name_is_mandatory(self):
        doc = frappe.get_doc({"doctype": "Customer"})
        self.assertRaises(frappe.MandatoryError, doc.insert)
```

## Create records inside a test

```python
class TestSalesOrder(FrappeTestCase):
    def test_sales_order_insert(self):
        customer = frappe.get_doc({
            "doctype": "Customer",
            "customer_name": "Test Customer",
        }).insert()

        self.assertTrue(customer.name)
```

## Pick the right file

- Use this file for Frappe-specific integration-style tests.
- Use `unit_test.md` for lightweight pure-function style tests.
