# Development templates

These are optional product-infrastructure examples retained from the initial draft, not setup work to execute now. Use only if the S01/S07 architecture decision calls for them. They do not start an application, package Astra, or reinstate Astra's stopped Compose Sprint 188. The main deliverable is the PI/sprint plan.

- [compose.dev.yaml](compose.dev.yaml): localhost-only development PostgreSQL and Redis.
- [.env.infra.example](.env.infra.example): development infrastructure placeholders.
- [.env.api.example](.env.api.example): backend configuration names.
- [.env.worker.example](.env.worker.example): worker configuration names.

Replace secrets locally, use matching DB credentials, and keep real environment files out of Git. The application must implement validation of these variables. PostgreSQL/Redis major tags are illustrative development baselines; verify support, licenses, and exact image digests at implementation. Persistent named volumes survive stopping containers.

