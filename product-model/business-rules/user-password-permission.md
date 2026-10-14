---
appliesTo:
- type: entity
  id: user
  effect: changes
  facts:
  - Password
permits:
- self: true
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#setPassword
- kind: code
  role: implementation
  target: server/router/auth-router.go#completePasswordReset
---

# A person sets their own password; Users administrators reset it

A User sets their own password, from Preferences, a reset link, an invitation or at sign-in. A User with Users access Admin resets another person's sign-in in the user editor.
