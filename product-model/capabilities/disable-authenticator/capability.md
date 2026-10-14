---
availability:
- place: web::booking-site
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#disableTotp
---

# Disable authenticator app

Remove the authenticator app from one's account.
