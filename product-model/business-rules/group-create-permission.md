---
appliesTo:
- type: entity
  id: group
  effect: creates
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Groups access
    is: Admin
  - entity: organization
    fact: Groups feature
    is: 'On'
references:
- kind: code
  role: implementation
  target: server/router/group-router.go#create
---

# Only Groups administrators create a Group, while the plan includes Groups

Creating a Group takes Groups access Admin and an Organization whose plan includes Groups.
