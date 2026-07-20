---
title: Deploy Rollback
order: 2
---

Rolling back is the fastest mitigation for most production incidents caused by a recent deploy.
This page covers the standard path; skip to the manual section only if it fails.

## Standard rollback (Argo CD)

1. Open the service's Argo CD application.
2. Click **History and Rollback**, pick the last known-good revision.
3. Confirm the rollback — this triggers a new sync, not a revert commit, so it's immediate.
4. Watch the health checks turn green before declaring the incident mitigated.

## Manual rollback

If Argo CD itself is unhealthy, roll back via `platform-cli` directly:

```bash
platform-cli deploy rollback <service> --to <previous-revision>
```

Use `platform-cli deploy history <service>` first if you're not sure which revision was last
healthy — it lists the last 10 revisions with their deploy timestamps and the commit SHA that
triggered them.

Always follow a rollback with a short note in the incident channel stating what was rolled back
and to which revision, so the fix isn't lost when someone re-deploys later.
