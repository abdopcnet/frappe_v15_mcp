PDF: set margins via .print-format; use simple CSS (tables). Avoid flex/grid.

```html
<style>
  @page { size: A4; margin: 0; }
  .print-format { margin: 10mm; page-size: A4; }
</style>
<div class="print-format"><!-- content --></div>
```
