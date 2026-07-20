---
title: Access Requests
order: 2
---

# Access Requests

Most access in the org is granted through Azure AD group membership rather than one-off manual
grants, so requesting the right group gets you into every system that trusts it.

Common groups to request in your first week:

- `platform-eng-readonly` — read access to dashboards, logs, and this wiki.
- `platform-eng-write` — write access to non-production infrastructure and this wiki's editable
  content.
- `prod-deploy` — required to run deploys against production; requires manager approval.

Submit requests through the internal Access Portal, tagging your manager as approver. Standard
groups are usually granted within one business day; `prod-deploy` can take longer since it
requires a second approver from the on-call rotation.

If you need access to something not covered by an existing group, post in `#platform-eng` before
filing a request — there's often already a group that covers your use case, and creating
one-off grants makes the next audit slower for everyone.
