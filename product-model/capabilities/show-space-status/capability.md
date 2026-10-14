---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: server/router/kiosk-router.go#getKiosk
- kind: code
  role: implementation
  target: ui/src/pages/kiosk/[id].tsx
- kind: spec
  role: intent
  target: specs/kiosk-mode.md
---

# Show space status

Show one Space's status on a kiosk display beside it: free or occupied, the current and the next booking, refreshed regularly. It exists while the Organization's plan includes kiosk mode, the Organization turns it on and the Space shows on a kiosk display.
