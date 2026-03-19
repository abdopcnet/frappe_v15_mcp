# PDF Generation

Use this when HTML or a print format must become a PDF.

## Render HTML to PDF bytes

```python
from frappe.utils.pdf import get_pdf

html = frappe.render_template("""
    <h1>Invoice {{ doc.name }}</h1>
    <p>Customer: {{ doc.customer }}</p>
""", {"doc": doc})

pdf_bytes = get_pdf(html)
```

## Return PDF as response

```python
frappe.response.filename = f"{doc.name}.pdf"
frappe.response.filecontent = pdf_bytes
frappe.response.type = "pdf"
```

## Pick the right file

- Use this file for server-side PDF generation.
- Use `print_format.md` for the Jinja template side.
- Use `wkhtmltopdf_print_format.md` for wkhtmltopdf layout issues.
