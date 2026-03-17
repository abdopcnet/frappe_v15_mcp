# Print Format

Use this when the question is about the Jinja/HTML template used for printing.

## Basic print format body

```html
<div class="print-heading">
  <h2>{{ doc.doctype }} {{ doc.name }}</h2>
</div>

<div class="section-body">
  <p>Customer: {{ doc.customer }}</p>
  <p>Total: {{ doc.get_formatted("grand_total") }}</p>
</div>
```

## Render child table rows

```html
<table class="table table-bordered">
  <thead>
    <tr>
      <th>Item</th>
      <th>Qty</th>
      <th>Amount</th>
    </tr>
  </thead>
  <tbody>
    {% for row in doc.items %}
    <tr>
      <td>{{ row.item_name }}</td>
      <td>{{ row.qty }}</td>
      <td>{{ row.get_formatted("amount") }}</td>
    </tr>
    {% endfor %}
  </tbody>
</table>
```

## Pick the right file

- Use this file for print format HTML and Jinja.
- Use `wkhtmltopdf_print_format.md` for PDF engine layout quirks.
