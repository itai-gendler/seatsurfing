---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#loginPassword
- kind: code
  role: implementation
  target: server/router/auth-router.go#callback
- kind: code
  role: implementation
  target: server/router/auth-router.go#verify
- kind: code
  role: implementation
  target: server/router/passkey-router.go#finishPasskeyLogin
- kind: code
  role: implementation
  target: ui/src/pages/login/index.tsx
---

# Sign in

Sign in to the Organization with email address and password, adding an authenticator code or a passkey where the User has one, with a passkey alone, or through one of the Organization's identity providers. Password sign-in exists while the installation has not turned it off.
