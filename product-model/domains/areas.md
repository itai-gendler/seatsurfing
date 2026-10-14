---
references:
- kind: code
  role: implementation
  target: ui/src/components/SideBar.tsx
---

# Areas

The administration section where Areas, their floor plans and the Spaces on them are laid out, together with who may book them, who approves their bookings and the attributes they carry.

## Boundary

Areas owns Areas, Spaces, attributes and the approver and allowed booker lists. It does not own the Groups those lists name, the bookings made in its Spaces, or deciding pending bookings.
