# Data model and proposed API contracts

These product routes and entities are proposed, not existing Astra endpoints.

| Entity | Information and invariants |
|---|---|
| Workspace / Site / Membership | Authenticated grants, role, revocation and document access |
| EquipmentFamily / Asset | Manufacturer, model, variant, serial/firmware and verified identity |
| Manual / ManualRevision | Immutable hash, publisher, revision label, language, approval, effective dates and owner |
| ApplicabilityRule | Explicit model/variant/serial/firmware constraints; unknown is not a match |
| Approval / Withdrawal | Reviewer, time, scope, reason and source revision; auditable lifecycle |
| ParseRun / Chunk | Parser/OCR version, page index and printed label, section path, spans and linked prerequisites |
| IndexGeneration | Corpus and permissions revision, source hashes, build state and publication record |
| QueryRun / Answer | User scope, equipment context, model/prompt, corpus version, typed outcome and cited claims |
| Citation | Source revision/hash, chunk/span, physical page and printed page label, viewer target |
| ProcedureSession | Approved procedure version, required prerequisites, branch observations and stop conditions |
| Escalation / Feedback | Question, authorized evidence snapshot, unresolved reason, assignment and explicit reviewer outcome |
| Job / Audit / Entitlement | Idempotency, remote IDs, correlation ID, state and usage settlement |

Manual states: draft -> under_review -> approved -> superseded or withdrawn. Supersession is applicability-specific; an older valid asset range must not disappear by accident. Approval is recorded by an authorized document owner and is distinct from parsing success. Index states: building/validated/published/failed/retired.

Answer outcomes: answered / needs_clarification / insufficient_evidence / conflicting_sources / escalated / unavailable. A runtime outage is not a knowledge gap. Retrieval scores are not probabilities of correctness. Retain immutable historical metadata, while access to historical content obeys current permissions and retention policy.

| Proposed route | Behavior |
|---|---|
| POST /api/sites/{siteId}/manuals | Bounded private upload with hash, permissions and draft state |
| POST /api/manuals/{id}/revisions/{revision}/approve | Validate reviewer, applicability and expected revision; publish only after index validation |
| POST /api/manuals/{id}/revisions/{revision}/withdraw | Block new use immediately; trigger derived-store invalidation |
| GET /api/equipment | List only authorized asset identities and supported scopes |
| POST /api/questions | Resolve equipment and access, persist query/job ID, return typed outcome when ready |
| GET /api/answers/{id} | Recheck permission/freshness; withhold obsolete procedural answer as appropriate |
| GET /api/sources/{revision}/pages/{page} | Scoped original-page viewer with source identity |
| POST /api/procedure-sessions | Start approved version with verified context and prerequisite checklist |
| POST /api/procedure-sessions/{id}/observations | Validate expected state/version; never actuate equipment |
| POST /api/escalations | Create an internal review ticket from user-authorized question/evidence |
| GET /api/jobs/{id} | Authorized progress, cancellation/failure and reconciliation states |

Enforce scoped lookups on all routes and storage URLs. Use optimistic concurrency for approvals, asset edits and procedure observations; idempotency for uploads/jobs/escalations. No unsolicited email or external ticket submission is included in the initial workflow.
