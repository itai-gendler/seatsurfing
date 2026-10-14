---
availability:
- place: web::administration
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#adminResetTotp
---

# Reset user's authenticator app

Remove another person's authenticator app, for example when they lost their phone.
