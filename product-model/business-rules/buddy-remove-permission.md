---
appliesTo:
- type: entity
  id: buddy
  effect: removes
permits:
- related:
  - verb: keeps
    entity: user
  when:
  - entity: organization
    fact: Show bookers' names
    is: 'On'
  - entity: organization
    fact: Disable buddies
    is: 'Off'
references:
- kind: code
  role: implementation
  target: server/router/buddy-router.go#delete
---

# Only the person removes their buddies

A User removes their own buddies, while buddies are on.
