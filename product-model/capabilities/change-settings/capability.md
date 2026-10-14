---
availability:
- place: web::administration
domain: settings
references:
- kind: code
  role: implementation
  target: server/router/settings-router.go#setAll
- kind: code
  role: implementation
  target: server/router/settings-router.go#isValidSettingValue
- kind: code
  role: implementation
  target: ui/src/pages/admin/settings/index.tsx
---

# Change settings

Change the Organization's settings page, which holds its booking rules, second-factor enforcement, reports, kiosk mode, public booking and retention settings, saved together. The plan features shown there are not changed here.
