---
order: 2
---

# Data Quality Checks

Every table listed in **Key Datasets** has an associated set of quality checks that run after its
load completes, before the table is marked ready for downstream consumption.

Checks fall into three categories:

- **Freshness** — did the table update within its expected window? A stale `orders_fact` blocks
  the finance close job automatically rather than letting it run on old data.
- **Volume** — is the row count within an expected range of the trailing 7-day average? Catches
  both silent drops (upstream outage) and silent duplication (bad join).
- **Schema** — do column types and nullability match the registered schema? Catches upstream
  changes before they break a downstream query.

A failed check marks the table `degraded` in the catalog rather than failing the pipeline outright
— consumers can choose whether to proceed with degraded data or wait, rather than the pipeline
making that call for everyone.

Request a new check by adding it to the dataset's `checks.yaml` in the `data-pipelines` repo.
