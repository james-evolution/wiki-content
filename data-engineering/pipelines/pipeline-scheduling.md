---
order: 2
---

# Pipeline Scheduling

All production pipelines are scheduled through the shared Airflow instance rather than ad hoc
cron jobs, so ownership, retries, and alerting are consistent across teams.

## Requesting a new DAG

1. Open a PR against the `data-pipelines` repo with your DAG definition.
2. Tag `#data-eng-review` — DAGs need a review focused on retry policy and resource limits before
   merging, since a misconfigured DAG can starve the shared worker pool.
3. Once merged, DAGs deploy automatically on the next sync cycle (every 10 minutes).

## Retry policy defaults

Unless overridden, DAGs inherit:

- 3 retries with exponential backoff starting at 5 minutes
- A hard timeout of 2 hours per task
- Failure alerts routed to the owning team's on-call, not a shared channel

Override these only with a comment explaining why — the defaults exist because under-retrying
causes unnecessary pages, and over-retrying masks real failures for hours.
