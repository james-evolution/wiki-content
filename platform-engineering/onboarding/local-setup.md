---
order: 1
---

# Local Setup

Follow these steps to get a working development environment on your first day.

1. Install the toolchain: Node 22, Docker Desktop, and the `platform-cli` via Homebrew or the
   Windows installer linked in #platform-eng.
2. Clone the core services repo and run the bootstrap script:

```bash
git clone git@github.com:example-org/core-services.git
cd core-services
./scripts/bootstrap.sh
```

3. Copy `.env.example` to `.env` in each service you plan to run locally, and request secrets
   from the `#platform-secrets` bot if the defaults don't work.
4. Run `platform-cli doctor` to verify Docker, your VPN connection, and cluster credentials are
   all healthy before you start developing.

If `bootstrap.sh` fails on a fresh machine, it's almost always a Docker resource limit — bump
memory to at least 8GB in Docker Desktop's settings and retry.

Once `doctor` passes, you're ready to run any service locally with `platform-cli run <service>`.
