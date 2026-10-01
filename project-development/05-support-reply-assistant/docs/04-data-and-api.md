# Data model and proposed API contracts

These proposed product routes are not existing Astra endpoints.

| Entity | Information and invariants |
|---|---|
| Workspace / Team / Agent / Membership | Authenticated tenant/team grants, role and revocation |
| Case / CaseRevision | Stable external/import ID, customer reference, product/context, version and visibility |
| Message / Attachment | Author/role, original timestamp/time zone, public/private flag, immutable content/hash and source ID |
| KnowledgeRevision / Publication | Owner, approved version, product/language applicability, effective dates, audience and withdrawal |
| ReusableExample | Explicitly reviewed/redacted historical material; not automatic policy authority |
| FactSnapshot | Authorized system/account/order identity, observed time, source/version and expiry/error |
| Summary / DraftRevision | Case version, model/prompt, source versions, fact snapshots, uncertain claims and issues |
| Citation / ClaimEvidence | Internal locator to message/passage/fact; separates customer claims from verified facts |
| Approval / Handoff | Exact draft revision, reviewer, time, freshness checks and artifact hash; not delivery status |
| Job / Audit / Usage | Idempotency, remote IDs, correlation ID, state and settlement |

Draft states: generating/needs_review/blocked/approved/stale/superseded. A new case message or material source/fact change makes dependent approval stale. Editing creates a new draft revision. Handoff states record copied/exported only; do not label them sent, delivered or customer-resolved.

Summary distinguishes customer-reported symptoms, verified facts, prior responses, unresolved questions and claimed versus completed actions. Missing timestamps or ambiguous chronology must be flagged. Imported quoted messages cannot create duplicate events without provenance.

| Proposed route | Behavior |
|---|---|
| POST /api/cases/import | Validate documented format and public/private fields; idempotent stable IDs |
| GET /api/cases/{id} | Scoped timeline and current case revision |
| POST /api/knowledge | Import draft source with owner and applicability |
| POST /api/knowledge/{id}/publish | Authorized review of exact revision and audience |
| POST /api/knowledge/{id}/withdraw | Block new use and invalidate dependent summaries/drafts |
| POST /api/cases/{id}/summaries | Create scoped job pinned to case revision |
| POST /api/cases/{id}/drafts | Generate from eligible evidence; mark missing facts |
| PATCH /api/drafts/{id}/revisions/{revision} | Optimistic version check, new revision and audit |
| POST /api/drafts/{id}/approve | Validate role, exact case/draft/source/fact freshness and unresolved issues |
| POST /api/drafts/{id}/export | Recheck approved revision and disclosure rules; return public text artifact |
| POST /api/drafts/{id}/feedback | Store restricted correction/outcome evidence without automatic training |
| GET /api/jobs/{id} | Scoped progress, cancellation/error and reconciliation state |

Require current grants for all lookups and artifacts. Idempotency does not mean distinct new messages are silently deduplicated. Imported conflicts require reconciliation. No send, refund, account-change or ticket-close endpoint is included. A future live lookup must be authorized against the case customer/account, not just a supplied order number.
