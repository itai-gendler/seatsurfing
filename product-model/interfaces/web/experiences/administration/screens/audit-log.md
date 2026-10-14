---
entities:
- entity: audit-entry
  shows:
  - Time
  - Email address
  - Method
  - Outcome
  - Device
  - Identity provider
entryPoints:
- web: /ui/admin/audit/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/audit/index.tsx
---

# Audit log

The Organization's sign-in attempts, filtered by period, person and outcome.
