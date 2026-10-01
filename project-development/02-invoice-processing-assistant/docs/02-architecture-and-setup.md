# Architecture, ownership and setup prerequisites

Planning baseline inherited from project 01: React + TypeScript + Vite screens, Next.js App Router Route Handlers for authenticated business APIs, private Astra Python runtime. S02 pins compatible versions and deployment topology. PostgreSQL metadata and private object storage are candidate stores, subject to that decision. No installation or application skeleton is part of this documentation task.

Browser -> authenticated product server -> client-scoped stores and private Astra adapter. The server derives workspace/client grants from authenticated membership. Request-supplied tenant claims never establish access. Runtime credentials stay on the server. Inspect exact gateway schemas and typed errors; do not expose legacy demo APIs as customer endpoints.

Product owns document/revision state, deterministic checks, approvals, exports, entitlements and audit. Astra owns accepted remote inference jobs, budgets and cancellation. Persist product job ID, remote ID and correlation ID. Reconcile uncertain outcomes before replay. Product parsing/export workers must not independently retry Astra-owned effects. S06 defines dispatch/outbox and reconciliation semantics.

Parser/OCR workers process bounded untrusted files with restricted filesystem/network access. Originals are immutable; derived text, candidates and revisions are versioned. LLM output is untrusted candidate data. Decimal calculations and access checks are independent of model responses.

S02 records OS, Node/package manager, database/store, Astra interpreter/profile, checkpoint, parser/OCR dependencies and licensing. Pin exact versions only after compatibility checks. Reuse Astra's actual profile instructions; no generic replacement runtime or external paid-model fallback is selected.

Prepare synthetic two-client fixtures, permissioned real samples, scoped credentials, private gateway endpoint and bounded limits. Keep invoices and secrets out of source control. Spike: verify authentication, parse native PDF and poor scan, extract a schema, trace source fields, run arithmetic and cross-client negatives, measure latency and failures. Mocks may develop screens but cannot close feasibility.
