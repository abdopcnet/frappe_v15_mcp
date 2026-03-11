# wkhtmltopdf_print_format

Set PDF margins via `.print-format`; engine overrides `@page`.
Use simple CSS (tables). Avoid flex/grid/position fixed.

```html
<style>
    @page { size: A4 portrait; margin: 0mm; }
    .print-format {
        margin-top: 2mm;
        margin-bottom: 2mm;
        margin-left: 2mm;
        margin-right: 2mm;
        page-size: A4;
        orientation: Portrait;
        header-spacing: 5mm;
    }
</style>

<div class="print-format">
    <!-- Template content: tables preferred -->
</div>
```

Only direct `.print-format` properties are read for PDF options.
After changes: clear cache and hard refresh.

```bash
bench --site yoursite.local clear-cache
```
