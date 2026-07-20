---
title: System Diagram
order: 2
---

A high-level view of how a request flows from the edge into our core services, for anyone trying
to orient themselves before diving into a specific service's own docs.

```mermaid
flowchart LR
    Client[Client] --> Gateway[API Gateway]
    Gateway --> Auth[Auth Service]
    Gateway --> Orders[Orders Service]
    Gateway --> Catalog[Catalog Service]
    Orders --> Queue[(Event Queue)]
    Queue --> Billing[Billing Service]
    Orders --> DB[(Orders DB)]
    Catalog --> Cache[(Catalog Cache)]
```

The gateway terminates TLS and handles authn/z before routing to internal services over the
service mesh (see ADR-004). Orders publishes events onto the shared queue rather than calling
Billing synchronously, which is what lets Billing be down without blocking checkout.

Each box in this diagram links to its own service README in the core-services repo, which covers
on-call ownership, SLOs, and deploy cadence — this page intentionally stays at the "how it fits
together" level rather than per-service detail.
