---
availability:
- place: web::booking-site
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go#deletePasskey
---

# Remove passkey

Remove one of one's passkeys. Where the Organization enforces a second factor, a User's last passkey stays unless they have an authenticator app.
