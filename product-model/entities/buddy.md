---
references:
- kind: code
  role: implementation
  target: server/router/buddy-router.go
- kind: code
  role: implementation
  target: server/service/buddy-service.go
---

# Buddy

A colleague a User marked as their buddy, so that the floor plan and search show where the colleague sits. Buddies exist while the Organization shows bookers' names and has not switched buddies off.

## Information kept

- **Colleague** — the other User of the Organization the buddy stands for
