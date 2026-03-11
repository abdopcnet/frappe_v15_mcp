Use is_new and is_dirty before logic that depends on form state.

```javascript
if (frm.is_new()) { /* set defaults */ }
if (frm.is_dirty()) { /* warn before navigate */ }
```
