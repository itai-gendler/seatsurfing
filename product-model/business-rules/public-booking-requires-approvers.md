---
appliesTo:
- type: capability
  id: edit-space
- type: capability
  id: create-space
- type: capability
  id: remove-space-approvers
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#update
- kind: code
  role: implementation
  target: server/router/space-router.go#validateApprovers
- kind: code
  role: implementation
  target: server/router/space-router.go#removeApprovers
---

# A Space is open to public booking only while it has an approver group

A Space is opened to public booking only once it has at least one approver group, and its last approver group cannot be removed while it stays open.
