# print_format

Jinja print template: doc fields and child table loop.

```html
<div class="print-format">
  <h3>{{ doc.name }}</h3>
  <p>{{ doc.get_formatted("posting_date") }} {{ doc.get_formatted("grand_total") }}</p>
  {% for row in doc.items %}
  <tr><td>{{ row.item_code }}</td><td>{{ row.qty }}</td></tr>
  {% endfor %}
</div>
```

Use `doc.get_formatted()` for currency/date. Keep templates presentation-only.
