---
references:
- kind: code
  role: implementation
  target: server/repository/session-repository.go
- kind: code
  role: implementation
  target: server/router/auth-router.go#CreateSession
---

# Session

One signed-in device of a User, listed among their active sessions until they sign out or it expires.

## Information kept

- **Device** — the browser and operating system the session was opened from
- **Created** — when the User signed in
