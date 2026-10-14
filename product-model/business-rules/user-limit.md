---
appliesTo:
- type: capability
  id: create-user
- type: capability
  id: book-space
references:
- kind: code
  role: implementation
  target: server/repository/user-repository.go#CanCreateUser
---

# Without the unlimited users feature an Organization holds at most ten accounts

An Organization whose plan does not include unlimited users takes no account beyond its tenth, however it would be added.
