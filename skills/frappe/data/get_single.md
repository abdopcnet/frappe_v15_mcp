# get_single

Work with Single DocTypes such as site-wide settings and global defaults.

## Load the full Single DocType

```python
system_settings = frappe.get_single("System Settings")
print(system_settings.language)

system_settings.language = "ar"
system_settings.save(ignore_permissions=True)
```

## Read one field quickly

```python
language = frappe.db.get_single_value("System Settings", "language")
company = frappe.db.get_single_value("Global Defaults", "default_company")
```

## Write one field directly

```python
frappe.db.set_single_value("System Settings", "language", "ar")
```

## When full doc matters

```python
print_settings = frappe.get_single("Print Settings")

for row in print_settings.print_style:
    print(row.name)
```

## Rules

- Use `get_single()` when you need multiple fields, child tables, or `save()`.
- Use `get_single_value()` for fast single-field reads.
- Use `set_single_value()` only when bypassing full document save is acceptable.

## Do not use for

- Regular DocTypes with multiple rows
- Validation-sensitive writes that should go through full document save

Single DocTypes are configuration records, not normal transactional documents.
