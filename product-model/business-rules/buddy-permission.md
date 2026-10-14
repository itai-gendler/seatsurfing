---
appliesTo:
- type: entity
  id: buddy
  effect: creates
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
  target: server/router/buddy-router.go#create
- kind: code
  role: implementation
  target: server/service/buddy-service.go#IsEnabled
---

# Only the person keeps their buddies, while buddies are on

A User adds and removes their own buddies, while the Organization shows bookers' names and has not switched buddies off.
