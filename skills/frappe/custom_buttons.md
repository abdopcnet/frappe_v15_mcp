Add custom toolbar buttons or change primary action on the form.

```javascript
frm.add_custom_button(__("Create Invoice"), () => { /* ... */ });
frm.page.set_primary_action(__("Submit"), () => frm.save());
```
