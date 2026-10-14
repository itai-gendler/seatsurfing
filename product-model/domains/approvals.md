---
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/approvals/index.tsx
---

# Approvals

The administration section where approvers decide bookings that wait for approval.

## Boundary

Approvals owns approving and declining pending bookings. It does not own which Groups approve a Space, which belongs to Areas, nor making or cancelling bookings.
