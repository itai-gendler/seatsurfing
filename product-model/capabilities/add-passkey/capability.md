---
availability:
- place: web::booking-site
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go#beginPasskeyRegistration
- kind: code
  role: implementation
  target: server/router/passkey-router.go#finishPasskeyRegistration
- kind: spec
  role: intent
  target: specs/passkeys.md
---

# Add passkey

Register a passkey on one's account, from the Organization's primary address, to sign in without a password or as the second factor after it. People who sign in through an identity provider have no passkeys.
