---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: server/router/kiosk-router.go
- kind: spec
  role: intent
  target: specs/kiosk-mode.md
---

# Kiosk display

A screen outside a room that shows one Space's current and next booking, presenting the Organization's kiosk secret. Kiosk displays exist while the Organization's plan includes kiosk mode and the Organization turns it on.
