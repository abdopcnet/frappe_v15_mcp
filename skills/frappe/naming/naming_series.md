# naming_series

Use naming series when document names should follow predictable prefixes and counters.

## Configure on DocType

```text
autoname = naming_series:
options = SINV-.YYYY.-
```

## Set in code before naming

```python
doc.naming_series = "SAL-.YYYY.-"
doc.set_new_name()
```

## Rules

- Use naming series for transactional DocTypes with human-readable identifiers.
- Set the correct series before insert.
- Keep prefixes stable once documents exist in production.
