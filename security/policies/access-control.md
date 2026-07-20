---
title: Access Control Policy
order: 1
---

# Access Control Policy

All access to internal systems is granted via Azure AD group membership, following the principle
of least privilege — request the narrowest group that lets you do your job, not the broadest one
that saves you asking again later.

## Group review cadence

Every AD group governing production access is reviewed quarterly by its owning team lead. Members
who haven't used the access in 90 days (per audit logs) are flagged for removal, not removed
automatically — this catches both genuinely stale access and legitimate low-frequency use like
quarterly finance exports.

## Requesting elevated access

Elevated access (production data, prod-deploy, admin consoles) requires:

1. A written justification tied to a specific task, not "might need it later."
2. Manager approval.
3. A defined expiry — elevated grants default to 30 days unless renewed.

## Service accounts

Service accounts follow the same least-privilege rule as humans, plus a hard requirement: every
service account must have a named human owner in its description field, checked as part of the
quarterly review.
