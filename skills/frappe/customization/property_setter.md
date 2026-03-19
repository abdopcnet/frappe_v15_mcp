# property_setter

Use Property Setter when you need to change DocType or field properties without editing core metadata.

## Create with code

```python
frappe.make_property_setter("Item", "item_code", "reqd", 1, "Check")
```

## Common property types

```python
frappe.make_property_setter("Sales Order", "delivery_date", "hidden", 1, "Check")
frappe.make_property_setter("Item", "item_group", "label", "Product Group", "Data")
```

## UI path

```text
Customize Form -> select DocType or field -> change property -> Save
```

## Rules

- Use Property Setter for metadata changes that must survive upgrades.
- Prefer Customize Form for quick admin changes.
- Prefer app fixtures or migration steps when the change belongs in deployment workflow.

## Do not use for

- Runtime UI toggles; use frontend field APIs instead
- Replacing proper DocType design in your own app
