# cache

Use cache for stable values that are expensive or noisy to fetch repeatedly.

## Read or build a cached value

```python
cache_key = f"customer_balance:{customer}"

balance = frappe.cache().get_value(
    cache_key,
    generator=lambda: frappe.db.get_value("Customer", customer, "outstanding_amount"),
)
```

## Store explicitly

```python
frappe.cache().set_value("my_app:settings", {"enabled": 1})
```

## Delete one cache entry

```python
frappe.cache().delete_value(f"customer_balance:{customer}")
```

## Rules

- Cache small stable values, not whole mutable document graphs.
- Use predictable keys with app-specific prefixes.
- Rebuild from source of truth when the key is missing.

## Do not use for

- Replacing database persistence
- Values that change every request
- Global invalidation strategy; use `clear_cache.md`
