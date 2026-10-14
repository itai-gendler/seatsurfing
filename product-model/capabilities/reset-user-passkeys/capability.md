---
availability:
- place: web::administration
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#adminResetPasskeys
---

# Reset user's passkeys

Remove every passkey of another person.
