# analyze_tables_and_processlist

Use direct DB inspection when diagnosing locks, long queries, or blocked migrations.

## Show process list

```python
rows = frappe.db.sql("SHOW FULL PROCESSLIST", as_dict=True)
```

## Long-running queries

```python
rows = frappe.db.sql(
    """
    SELECT Id, Time, State, Info
    FROM information_schema.PROCESSLIST
    WHERE Command != 'Sleep'
      AND Time > %(seconds)s
    ORDER BY Time DESC
    """,
    {"seconds": 10},
    as_dict=True,
)
```

## Kill a blocking process

```python
frappe.db.sql("KILL 12345")
```

## Open table usage

```python
rows = frappe.db.sql("SHOW OPEN TABLES WHERE In_use > 0", as_dict=True)
```

## Rules

- Inspect first, kill later.
- Exclude your own connection when diagnosing blockers.
- Use this in ops/debugging workflows, not application logic.
