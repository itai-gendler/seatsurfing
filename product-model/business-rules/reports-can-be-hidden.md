---
appliesTo:
- type: capability
  id: view-statistics
- type: capability
  id: view-presence-report
references:
- kind: code
  role: implementation
  target: server/router/stats-router.go
- kind: code
  role: implementation
  target: server/router/booking-router.go#getPresenceReport
- kind: spec
  role: intent
  target: specs/custom-roles.md
---

# Statistics and the presence report can be withheld from everyone

While the Organization hides statistics or reports, nobody sees them, whatever their access; only a settings administrator turning the setting off brings them back.

## Rationale

Presence data is personal; the setting lets an Organization state that nobody evaluates it, which a permission alone cannot, since administrators can grant themselves permissions.
