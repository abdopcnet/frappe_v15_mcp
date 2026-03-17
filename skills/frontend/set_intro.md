# set_intro

Show or clear short contextual guidance at the top of a form.

## Set intro

```javascript
frm.set_intro(__("Fill the required fields and save first"), "blue");
frm.set_intro(__("This document is overdue"), "red");
```

## Clear intro

```javascript
frm.set_intro();
```

## Dashboard indicator

```javascript
frm.dashboard.add_indicator(__("Approved"), "green");
```

## Rules

- Use intro text for one short context message, not a long guide.
- Use dashboard indicators for status summaries.
- Clear stale messages when the condition no longer applies.
