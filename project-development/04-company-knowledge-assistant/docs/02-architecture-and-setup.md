# Architecture, ownership and setup prerequisites

Planning baseline: React + TypeScript + Vite frontend, Next.js App Router Route Handlers for authenticated business APIs, and private Astra Python runtime. S02 pins compatible versions and topology. PostgreSQL metadata and private object storage are candidate stores. Select the search backend from measured baselines; no vector database is assumed necessary.

Browser -> authenticated product service -> authoritative membership/source registry -> authorized retrieval -> private Astra adapter -> checked explanation. Product establishes user identity and derives tenant, groups, site and document grants. Request-supplied principal IDs cannot establish identity. Keep runtime credentials server-side and inspect the actual versioned gateway schema.

Product owns sessions, grants, publication, effective dates, source freshness, citations, histories, gap analytics, subscriptions and audit. Astra provides qualified inference/retrieval/context primitives. Library functionality is not necessarily an exposed gateway operation; required authenticated wrappers are new integration work. Legacy local/demo APIs stay private.

Original bytes are immutable; parser outputs, chunks and index generations identify source hash and publication/access revisions. Validate and atomically publish new index generations. Withdrawals and permission changes block source use immediately through authoritative checks even while index cleanup is pending. Recheck access/freshness before answer delivery and source viewing.

Astra owns accepted remote inference jobs and runtime budgets. Product records remote IDs and reconciles uncertain outcomes before retry. Product workers may own ingestion/indexing, with one effect owner and idempotency. Cache scope includes authenticated grants, publication/access revision, applicable context, corpus generation and model/prompt configuration.

Conversation history is another retrieval input: authorize and refresh it on every turn, strip inaccessible/obsolete material before prompt construction and do not let a follow-up bypass source rules. Sharing answer links requires recipient authorization; no public answer links in the initial scope.

S02 records OS, Node/package manager, storage/database, parser/OCR licenses, Astra profile/checkpoint and corpus limits. Prepare synthetic multi-tenant fixtures and permitted samples. Pin dependencies after compatibility checks; do not commit secrets or internal documents. No installations, external provider fallback or connector credentials are selected by this plan.
