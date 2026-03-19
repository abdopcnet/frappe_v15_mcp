# Workflow Basics

Use this when the question is about reading workflow state, not applying transitions.

## Get the workflow definition

```python
from frappe.model.workflow import get_workflow_name

workflow_name = get_workflow_name("Sales Order")
workflow = frappe.get_doc("Workflow", workflow_name)
```

## Read the current workflow state field

```python
state_field = workflow.workflow_state_field
current_state = doc.get(state_field)
```

## Pick the right file

- Use this file for workflow structure and state lookup.
- Use `workflow_transitions.md` for applying or listing transitions.
