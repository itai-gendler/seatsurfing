---
actors:
- user
- visitor
- kiosk
access: public
entryPoints:
- web: /ui/login/
- web: /ui/book/
references:
- kind: code
  role: implementation
  target: server/router/unauthorized-routes.go
- kind: code
  role: implementation
  target: ui/src/pages/login/index.tsx
- kind: code
  role: implementation
  target: ui/src/pages/book/index.tsx
---

# Public pages

Pages reached without signing in: where Users sign in, reset their password or accept an invitation, where visitors request a Space and later look at or cancel their approved booking, and where a kiosk display shows a Space's status.
