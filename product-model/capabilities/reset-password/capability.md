---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#initPasswordReset
- kind: code
  role: implementation
  target: server/router/auth-router.go#completePasswordReset
- kind: code
  role: implementation
  target: ui/src/pages/resetpw/index.tsx
---

# Reset password

Get a link by email and choose a new password with it, when one has forgotten it. The link is valid for an hour; people signing in through an identity provider, disabled accounts and service accounts get none.
