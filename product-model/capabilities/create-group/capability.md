---
availability:
- place: web::administration
domain: groups
references:
- kind: code
  role: implementation
  target: server/router/group-router.go#create
- kind: code
  role: implementation
  target: ui/src/pages/admin/groups/[id].tsx
---

# Create group

Add a Group with a name unique in the Organization. It exists while the Organization's plan includes Groups.
