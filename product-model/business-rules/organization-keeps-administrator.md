---
appliesTo:
- type: capability
  id: delete-user
- type: capability
  id: remove-user-roles
- type: capability
  id: sign-in
references:
- kind: code
  role: implementation
  target: server/router/permissions.go#OrgRetainsAdminWithout
- kind: code
  role: implementation
  target: server/router/permissions.go#ReconcileUserFromIdP
- kind: spec
  role: intent
  target: specs/custom-roles.md
---

# The Organization always keeps an administrator

At least one enabled person always holds the built-in Organization Administrator role: deleting that person, taking the role away from them, or an identity provider's mapping that would do so is refused or left undone.
