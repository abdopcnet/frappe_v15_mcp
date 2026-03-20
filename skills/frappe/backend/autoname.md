# autoname

Control how a DocType generates its `name` field.

## autoname hook options

```python
# In DocType JSON
{
    "autoname": "naming_series:"    # uses Naming Series field
    "autoname": "field:email"       # copies the value of a field
    "autoname": "format:{country}-{customer_name}"  # template
    "autoname": "hash"              # random hash
    "autoname": "Prompt"            # user types the name manually
}
```

## autoname() controller method

Override `autoname()` for custom logic that cannot be expressed as a pattern.

```python
class Project(Document):
    def autoname(self):
        self.name = f"{self.company_code}-{self.project_type}-{frappe.generate_hash(length=6).upper()}"
```

## Autoname from a combination of fields

```python
class Address(Document):
    def autoname(self):
        parts = [self.city, self.country]
        base = "-".join(p for p in parts if p)
        self.name = frappe.model.naming.append_number_if_name_exists(
            "Address", base
        )
```

## Use append_number_if_name_exists to avoid duplicates

```python
import frappe.model.naming as naming

unique_name = naming.append_number_if_name_exists("Customer", "Acme Corp")
# → "Acme Corp" or "Acme Corp-1", "Acme Corp-2", ...
```

## Rules

- `autoname()` runs before `before_insert`.
- Set `self.name` directly inside the method.
- Never call `frappe.db.set_value` inside `autoname()`.
- Use `append_number_if_name_exists` when the generated name might collide.

## Do not use for

- Naming series increments; use `naming_series.md`
- Changing the name after document is saved; name is immutable after insert
