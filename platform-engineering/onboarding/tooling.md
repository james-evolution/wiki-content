---
title: Developer Tooling
order: 3
---

# Developer Tooling

A quick reference for the tools the platform team maintains and expects you to use day to day.

- **platform-cli** — wraps common Docker Compose, cluster, and secrets workflows. Run
  `platform-cli --help` for the full command list.
- **This wiki** — the engineering portal you're reading right now. Content lives in git; edits
  go through the built-in editor and are committed directly to the docs repo.
- **Grafana** — dashboards for every service, linked from each service's README.
- **Argo CD** — deployment status and rollout history for everything running in the cluster.

New tools should be proposed in an architecture decision record before being adopted org-wide —
see the **Architecture** category for the template and past examples.

A tip that saves a lot of confusion: `platform-cli run <service>` uses your local `.env`, while
`platform-cli run <service> --staging` proxies to the shared staging environment instead of
starting a local container. Mixing the two up is the most common source of "why is my change not
showing up" questions in `#platform-eng`.
