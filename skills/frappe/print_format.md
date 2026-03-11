Print formats use Jinja; doc and filters available in template.

```html
<div class="print-format">
  <h1>{{ doc.name }}</h1>
  {% for row in doc.items %}
    <p>{{ row.item_code }}: {{ row.qty }}</p>
  {% endfor %}
</div>
```
