# set_query

Filter Link field options with `frm.set_query()`.

## Parent field query

```javascript
frm.set_query("assigned_to", () => {
  return {
    filters: {
      enabled: 1,
      user_type: "System User",
    },
  };
});
```

## Dynamic query from another field

```javascript
frm.set_query("contact_person", () => {
  return {
    filters: {
      link_doctype: "Customer",
      link_name: frm.doc.customer,
    },
  };
});
```

## Child table query

```javascript
frm.set_query("item_code", "items", (doc, cdt, cdn) => {
  return {
    filters: {
      disabled: 0,
      is_sales_item: 1,
    },
  };
});
```

## Server-side custom query

```javascript
frm.set_query("item_code", () => {
  return {
    query: "my_app.api.get_available_items",
    filters: { customer: frm.doc.customer },
  };
});
```

## Rules

- Put query setup in `setup()` or `refresh()`.
- Use simple `filters` first; use `query` only when necessary.
- Keep custom search queries sanitized and permission-aware.
