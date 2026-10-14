---
appliesTo:
- type: capability
  id: create-role
- type: capability
  id: edit-role
- type: capability
  id: delete-role
- type: capability
  id: add-user-roles
- type: capability
  id: remove-user-roles
- type: capability
  id: add-provider-mapping
references:
- kind: code
  role: implementation
  target: server/router/permissions.go#CanGrantPermissions
- kind: code
  role: implementation
  target: server/router/user-router.go#setRoles
- kind: spec
  role: intent
  target: specs/custom-roles.md
---

# Nobody gives or defines a Role granting more than they hold

Creating, changing or deleting a Role, giving or taking a Role, and mapping a provider group to a Role each require the acting User to hold at least every level the Role grants. Nobody changes their own Roles or gives up their own Roles access.
