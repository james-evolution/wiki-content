---
title: "ADR-004: Adopt a Service Mesh"
order: 1
---

# ADR-004: Adopt a Service Mesh

**Status:** Accepted
**Date:** 2026-03-12

## Context

As the number of internal services grew past twenty, retry logic, mTLS, and traffic shaping were
being reimplemented inconsistently in each service's own HTTP client. This made incident response
slower, since debugging a timeout meant checking a different retry implementation every time.

## Decision

Adopt a sidecar-based service mesh for all internal service-to-service traffic. Retries, timeouts,
mTLS, and circuit breaking move into mesh configuration instead of application code.

## Consequences

- Services no longer need an HTTP client wrapper for retries or mTLS — one less thing to get
  wrong per service.
- Adds a sidecar container per pod, increasing baseline memory usage by roughly 50MB per instance.
- Debugging now requires familiarity with mesh configuration in addition to application logs;
  the **Incident Response** runbook has been updated with mesh-specific diagnostic commands.

## Alternatives considered

A shared internal HTTP client library was considered and rejected — it solves the consistency
problem but not the "redeploy every service to pick up a fix" problem that the mesh avoids.
