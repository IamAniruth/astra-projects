# Architecture, ownership and setup prerequisites

Planning baseline: React + TypeScript + Vite frontend, Next.js App Router Route Handlers for business APIs and private Astra Python runtime. S02 pins compatible versions and topology. PostgreSQL metadata and private object storage are candidate stores. Choose retrieval from measured baselines; do not assume a vector database is required.

Browser -> authenticated product service -> scoped case/source stores -> private retrieval/Astra adapter -> checked summary/draft -> agent approval -> explicit copy/export. Product authenticates tenant, agent/team, case access and source grants. Never use a browser-provided tenant/principal claim as proof.

Product owns message visibility, chronology, case revisions, source publication, fact snapshots, drafts, approval, handoff, entitlements and audit. Astra provides qualified inference/retrieval/context primitives. General gateway endpoints do not imply complete case-import or help-desk integration contracts. New authenticated wrappers are explicit integration work; legacy demo APIs remain private.

Store originals and revisions immutably. Summaries and drafts identify exact case version, source hashes, retrieved passages, prompt/model and any live-fact timestamp. New messages, policy withdrawal or changed facts mark dependent drafts stale and invalidate approval. Recheck case/source permissions and freshness before generation, viewing, approval and export.

Astra owns accepted remote inference jobs and budgets. Product persists remote IDs and reconciles unknown outcomes before retry. Product workers own import/export tasks with idempotency; one owner per effect. Cache keys include tenant, agent grants, case/version, source generation, live-fact versions and model/prompt configuration.

Keep internal evidence separate from customer-facing text. Export only approved public reply content and allowlisted public links; internal notes, source URLs and other customers' examples must not leak. Access to an internal fact does not imply permission to disclose it externally.

S02 records OS, Node/package manager, stores, parsers, Astra profile/checkpoint and case/context limits. Use permitted samples plus synthetic two-tenant/two-customer cases. No installation, external model fallback, mailbox credential or sending connector is selected here.
