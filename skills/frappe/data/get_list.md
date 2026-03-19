# get_list

Query multiple rows with Frappe permission checks applied.

Use this in whitelisted methods, reports shown to users, and frontend-facing reads.

## Basic query

```python
tasks = frappe.get_list("Task")

tasks = frappe.get_list(
    "Task",
    fields=["name", "subject", "status"],
    filters={"status": "Open"},
)
```

## Filters and pagination

```python
tasks = frappe.get_list(
    "Task",
    filters=[["priority", "in", ["High", "Medium"]]],
    order_by="creation desc",
    limit_start=0,
    limit_page_length=20,
)

tasks = frappe.get_list(
    "Task",
    filters={"status": "Open"},
    or_filters=[["owner", "=", frappe.session.user]],
)
```

## Child table filter

```python
invoices = frappe.get_list(
    "Sales Invoice",
    filters=[["Sales Invoice Item", "item_code", "=", "ITEM-001"]],
    fields=["name", "customer", "grand_total"],
)
```

## Aggregation and distinct

```python
status_counts = frappe.get_list(
    "Task",
    fields=["status", "count(*) as count"],
    group_by="status",
)

statuses = frappe.get_list("Task", fields=["status"], distinct=True)
```

## Rules

- `get_list()` respects DocType permissions, user permissions, and If Owner rules.
- It is the default choice for user-visible lists.
- Administrator can still see everything.
- If permissions are irrelevant, use `get_all()` instead.

## Do not use for

- Scheduler jobs
- Internal admin cleanup
- Large backend operations where permission checks add unnecessary overhead

Use `get_all.md` for trusted backend list queries.
