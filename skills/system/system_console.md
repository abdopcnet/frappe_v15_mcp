# system_console

Run Python in site: **System Console** (safe_exec, restricted) vs **bench execute** (full API).

```bash
bench --site SITENAME execute app.module.script.run
```

System Console: Developer Tools → System Console; limited builtins. Use bench execute for scripts that need full frappe (e.g. make_property_setter, commit). Avoid destructive ops in console.

---

## System Console snippet: Item Groups + Items (sweets_group1..6, food_group1..6)

Paste in System Console (Python), then check **Commit** and run.

```python
# Names (same as seed_item_groups_and_items / test_item_group / test_item pattern)
PARENT = "All Item Groups"
UOM = "Nos"
RATE = 25.0
sweets_groups = ["sweets_group" + str(i) for i in range(1, 7)]
food_groups = ["food_group" + str(i) for i in range(1, 7)]
per_group = 5

# Ensure root exists
if not frappe.db.exists("Item Group", PARENT):
    d = frappe.new_doc("Item Group")
    d.item_group_name = PARENT
    d.is_group = 1
    d.insert()
    log("Item Group: " + PARENT)

# Item groups (leaf: is_group=0)
for name in sweets_groups + food_groups:
    if frappe.db.exists("Item Group", name):
        continue
    d = frappe.new_doc("Item Group")
    d.item_group_name = name
    d.parent_item_group = PARENT
    d.is_group = 0
    d.insert()
    log("Item Group: " + name)

# Items per group (item_code, item_name, item_group, stock_uom, standard_rate, is_stock_item=0)
for group in sweets_groups + food_groups:
    for i in range(1, per_group + 1):
        code = group + "_item" + str(i)
        if frappe.db.exists("Item", code):
            continue
        d = frappe.new_doc("Item")
        d.item_code = code
        d.item_name = code.replace("_", " ").title()
        d.item_group = group
        d.stock_uom = UOM
        d.standard_rate = RATE
        d.is_stock_item = 0
        d.insert()
        log("Item: " + code)

log("Done. Check Commit and run to persist.")
```
