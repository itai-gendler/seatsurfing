---
availability:
- place: web::booking-site
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#generateTotp
- kind: code
  role: implementation
  target: server/router/user-router.go#validateTotp
- kind: code
  role: implementation
  target: ui/src/components/TotpSetupModal.tsx
---

# Enable authenticator app

Add an authenticator app as one's second factor by scanning a code and confirming one of its codes. Where the Organization enforces a second factor, people without one are asked to set one up after signing in.
