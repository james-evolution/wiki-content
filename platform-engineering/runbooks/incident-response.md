---
title: Incident Response
order: 1
---

When a production alert fires and you're the responder, follow this sequence rather than
improvising — it keeps the incident channel useful for whoever joins after you.

1. Acknowledge the page within 5 minutes and post in `#incidents` with a one-line summary.
2. Declare a severity (SEV1–SEV3) based on the on-call guide. SEV1 pages the incident commander
   rotation immediately.
3. Start mitigating before you start root-causing. Rolling back a bad deploy is almost always
   faster than debugging it live — see **Deploy Rollback** for the exact steps.
4. Post status updates in `#incidents` every 15 minutes while the incident is open, even if the
   update is "still investigating."
5. Once resolved, schedule a post-incident review within 2 business days.

```bash
# Quick health check across the fleet during an incident
platform-cli status --all --since 30m
```

Don't skip step 5 even for incidents that resolve themselves — those are often the leading
indicator of a bigger problem the next time.
