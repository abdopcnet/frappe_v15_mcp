# get_all

Query multiple rows without permission checks.

Use this in backend jobs, patches, admin logic, and trusted server-side code.

## Basic query

```python
tasks = frappe.get_all("Task")
tasks = frappe.get_all("Task", fields=["name", "subject", "status"])
```

## Filters

```python
tasks = frappe.get_all(
    "Task",
    filters={"status": "Open", "priority": "High"},
    fields=["name", "subject"],
)

tasks = frappe.get_all(
    "Task",
    filters=[["exp_end_date", ">=", frappe.utils.today()]],
    or_filters=[["owner", "=", frappe.session.user]],
)
```

## Order, limit, and pluck

```python
tasks = frappe.get_all("Task", order_by="creation desc", limit_page_length=20)
names = frappe.get_all("Task", filters={"status": "Open"}, pluck="name")
```

## Grouping and distinct

```python
counts = frappe.get_all(
    "Task",
    fields=["status", "count(*) as count"],
    group_by="status",
)

statuses = frappe.get_all("Task", fields=["status"], distinct=True)
```

## Rules

- `get_all()` bypasses permission checks.
- Default return is a list of dicts with `name` only.
- Use `pluck` when you need a single field list.
- Use this for trusted backend paths only.

## Do not use for

- User-facing APIs
- Frontend-driven queries
- Any place where row-level access must be respected

Use `get_list.md` for permission-aware list queries.
