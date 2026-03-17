# Workflow Transitions

Use this when the task is to list or apply workflow actions.

## List available transitions

```python
from frappe.model.workflow import get_transitions

transitions = get_transitions(doc)
```

## Apply a workflow action

```python
from frappe.model.workflow import apply_workflow

updated_doc = apply_workflow(doc, "Approve")
```

## Pick the right file

- Use this file for transition execution.
- Use `workflow_basics.md` for workflow metadata and state field lookup.
