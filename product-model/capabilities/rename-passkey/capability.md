---
availability:
- place: web::booking-site
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go#renamePasskey
---

# Rename passkey

Give one of one's passkeys another name.
