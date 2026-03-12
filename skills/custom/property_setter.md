# property_setter

Change field/DocType property via Customize Form (UI) or code.

```python
frappe.make_property_setter("Item", "item_code", "reqd", 1, "Check")
```

UI: Setup → Customize Form → select DocType/field → set property. From code use bench execute (System Console has no make_property_setter). property_type: Check, Data, Int, Select, Text.
