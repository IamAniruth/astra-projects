# Architecture, ownership and setup prerequisites

Planning baseline: React + TypeScript + Vite frontend, Next.js App Router Route Handlers for customer sessions/business APIs, and a separate private Astra Python runtime. S02 pins compatible versions and deployment topology. PostgreSQL metadata and private object storage are candidate stores. Search backend selection follows a measured retrieval baseline; no vector store is assumed necessary.

Browser -> authenticated product server -> document/equipment stores and private retrieval/Astra adapters. Product authenticates the user and derives tenant/site/document grants. Never treat a browser-provided principal or tenant claim as proof. Keep runtime credentials server-side; qualify the versioned gateway contract rather than exposing legacy demo routes.

Product owns equipment registry, approval lifecycle, applicability rules, authoritative source revisions, access checks, citations, answer history and escalation. Astra supplies qualified inference/retrieval/context primitives where suitable. A library feature is not automatically a published gateway operation; any required wrapper is new integration work.

Original bytes are immutable. Parsing outputs, chunks and indexes identify the exact source hash, parser version and approval/applicability revision. Publish an index generation atomically after validation. Withdrawal or permission changes block affected passages immediately at query/answer delivery even if asynchronous index cleanup is still pending. Recheck authorization and revision state when a citation is opened.

Astra owns its accepted remote jobs and runtime budgets; the product persists remote IDs and reconciles unknown outcomes before retry. Product workers may own parsing/indexing with idempotent jobs. Assign one execution owner per effect. Cache keys include principal grants, equipment applicability, corpus generation, prompt/model and policy versions; revocation invalidates or blocks old results.

S02 records OS, Node/package manager, database/storage, Astra profile/checkpoint, OCR/parser licensing and supported limits. Prepare permitted manuals and synthetic two-tenant fixtures. Pin versions after compatibility checks and keep secrets/manuals out of source control. No installations, external paid-model fallback, equipment connectors or replacement runtime are selected by this plan.
