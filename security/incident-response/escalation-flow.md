---
order: 1
---

# Escalation Flow

How a suspected security incident moves from first report to resolution. This is distinct from
the platform team's general **Incident Response** runbook — use this flow specifically for
anything involving unauthorized access, data exposure, or suspected compromise.

```mermaid
sequenceDiagram
    participant Reporter
    participant SecurityOnCall as Security On-Call
    participant IC as Incident Commander
    participant Legal

    Reporter->>SecurityOnCall: Report suspected incident
    SecurityOnCall->>SecurityOnCall: Triage severity
    SecurityOnCall->>IC: Escalate if confirmed
    IC->>Legal: Notify if data exposure suspected
    IC->>SecurityOnCall: Coordinate containment
    SecurityOnCall->>Reporter: Status update
    IC->>Legal: Final report
```

Report suspected incidents to `#security-oncall`, not the general `#incidents` channel — security
incidents have separate handling requirements around evidence preservation that the general
incident process doesn't cover.

Never attempt to contain a suspected compromise yourself before Security On-Call has triaged it;
premature action (like killing a process or rotating a credential) can destroy evidence needed for
the investigation.
