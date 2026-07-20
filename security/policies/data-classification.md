---
title: Data Classification
order: 2
---

# Data Classification

Every dataset and document should carry one of three classification levels, which determines who
can access it and how it must be stored.

- **Public** — safe for anyone, including outside the company, to see. Marketing content, public
  API docs.
- **Internal** — safe for any employee, but not for external sharing. Most of this wiki falls
  here by default.
- **Restricted** — customer PII, financial records, security incident details. Requires explicit
  group membership beyond general employee access, and must never be pasted into external tools
  (including AI assistants) without going through the data handling exception process.

Classification is set at creation time by the author and can be escalated (but not downgraded)
by anyone who notices it's wrong — when in doubt, classify one level higher and let the owning
team correct it down if appropriate.

Wiki pages default to Internal unless their frontmatter says otherwise; this policy document
itself is Internal.
