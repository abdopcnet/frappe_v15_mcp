# Skill: GitHub ERPNext Bug Report Template

Use when reporting a bug on https://github.com/frappe/erpnext/issues/new
Choose: Bug Report

---

## Get versions first

```bash
cd /home/frappe/frappe-bench-15 && bench version
```

---

## Template – copy each section into the matching GitHub field

---

### 1 – Add a title

```
fix: <what should happen> but <what actually happens>
```

---

### 2 – Information about bug

```
**DocType:** <DocType name>

<One paragraph: what happens and why it is wrong>

**Error:**
<paste error message>

**Root cause:**
<file.py → function(): explain what line causes the issue>

```python
# paste the problematic code
```

**Why only certain users are affected (if applicable):**
<explain if role/permission specific>

**Steps to reproduce:**
1. <setup>
2. <action that triggers the bug>
3. <what you see>

**Expected:** <what should happen>
**Actual:** <what actually happens>

**Proposed fix:**
```python
# paste fix
```
```

---

### 3 – Module

```
accounts / stock / selling / buying / hr  ← pick one
```

---

### 4 – Version

```
Frappe version  - X.XX.X
ERPNext version - X.XX.X
```

---

### 5 – Installation method

```
Manual (bench)
```

---

### 6 – Relevant log output / Stack trace / Full Error Message

```
paste full traceback here
```

Get traceback from:
- Browser F12 → Network → failing POST → Response tab
- Or ERPNext Error Log: Settings → Error Log

---

## Tips

- Sections 1, 2, 3, 4 are required (marked * on GitHub).
- Include a proposed fix → issues with fixes get resolved faster.
- Check existing issues first: https://github.com/frappe/erpnext/issues
