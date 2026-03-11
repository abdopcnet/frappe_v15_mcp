# utilities

Type conversion and date/format helpers in client scripts.

```javascript
flt(value); flt(value, 2); cint(value); cstr(value);
frappe.datetime.get_today();
frappe.datetime.add_days(date, 5);
frappe.datetime.str_to_obj(date_string);
frappe.datetime.obj_to_str(date_obj);
format_currency(amount, currency, decimals);
```

Normalize input before calculations.
