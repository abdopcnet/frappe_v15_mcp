# Manage Translations

Use this when the question is about maintaining translation records, not calling translation helpers in code.

## Create a translation record

```python
if not frappe.db.exists("Translation", {"source_text": "Submit", "language": "ar"}):
    frappe.get_doc({
        "doctype": "Translation",
        "source_text": "Submit",
        "translated_text": "إرسال",
        "language": "ar",
    }).insert()
```

## Export and import translations

```bash
bench --site site.local export-csv /tmp/translations.csv --doctype Translation
bench --site site.local import-csv /tmp/translations.csv
```

## Pick the right file

- Use this file for maintaining translation data.
- Use `translation_basics.md` for `_()`, `__()`, and template translation usage.
