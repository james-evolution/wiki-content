---
title: Post-Incident Review
order: 2
---

Every confirmed security incident gets a written review within 5 business days of resolution,
regardless of severity. This is separate from the containment work itself — the review's job is
to make the next incident less likely or easier to handle, not to assign blame.

## Required sections

1. **Timeline** — first detection through resolution, with timestamps.
2. **Root cause** — what actually happened, not just what was observed.
3. **Impact** — what was accessed, exposed, or affected, and for how long.
4. **What went well** — genuinely, not as a formality. Fast detection and clean containment are
   worth naming so the practices that produced them keep happening.
5. **Action items** — each with a named owner and a due date, tracked to completion.

Reviews are Restricted classification by default and shared on a need-to-know basis, but the
action items derived from them are tracked in the normal engineering backlog so they don't get
lost.

Reviews are not blameless in the sense of ignoring process gaps — a missing safeguard is exactly
the kind of finding the review exists to surface.
