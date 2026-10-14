---
appliesTo:
- type: entity
  id: organization
  effect: changes
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Settings access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/settings-router.go#setAll
- kind: code
  role: implementation
  target: server/router/settings-router.go#setSetting
---

# Only settings administrators change the Organization's settings

Changing the Organization's settings takes Settings access Admin.
