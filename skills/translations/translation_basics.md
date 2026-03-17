# Translation Basics

Use this when the question is how to mark strings for translation.

## Translate in Python

```python
from frappe import _

frappe.msgprint(_("Customer created successfully"))
```

## Translate with formatting

```python
frappe.throw(_("Row {0} is missing item code").format(row.idx))
```

## Translate in Jinja

```html
<h3>{{ _("Delivery Note") }}</h3>
<p>{{ _("Customer") }}: {{ doc.customer }}</p>
```

## Pick the right file

- Use this file for string-marking helpers.
- Use `manage_translations.md` for adding or editing translated values.
