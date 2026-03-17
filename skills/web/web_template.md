# Web Template

Use this when the question is about reusable website blocks or template-driven sections.

## Minimal web template body

```html
<div class="hero-block">
  <h1>{{ title }}</h1>
  <p>{{ subtitle }}</p>
</div>
```

## Example context payload

```python
context.hero = {
    "title": "Fresh sweets delivered daily",
    "subtitle": "Order online and track delivery status.",
}
```

## Pick the right file

- Use this file for reusable website templates.
- Use `web_page.md` for route/controller logic.
