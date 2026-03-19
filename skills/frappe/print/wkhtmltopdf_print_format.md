# Wkhtmltopdf Print Format

Use this when a print format works in browser preview but breaks in PDF output.

## Page sizing CSS

```html
<style>
  @page {
    size: A4;
    margin: 12mm;
  }

  .print-format {
    font-size: 11px;
  }

  .page-break {
    page-break-before: always;
  }
</style>
```

## Safer layout pattern

```html
<table style="width: 100%; border-collapse: collapse;">
  <tr>
    <td style="width: 70%; vertical-align: top;">Left block</td>
    <td style="width: 30%; vertical-align: top; text-align: right;">Right block</td>
  </tr>
</table>
```

## Pick the right file

- Use this file for wkhtmltopdf spacing, page breaks, and layout compatibility.
- Use `print_format.md` for the actual print template structure.
