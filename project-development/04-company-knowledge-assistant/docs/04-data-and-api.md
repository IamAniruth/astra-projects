# Data model and proposed API contracts

These product contracts are proposed, not existing Astra endpoints.

| Entity | Information and invariants |
|---|---|
| Workspace / User / Group / Membership | Authenticated identity, grants, group revision, revocation and tenant scope |
| Document / SourceRevision | Owner, immutable hash, original locator, format, language and version |
| SourcePolicy / Publication | Allowed users/groups, applicable audience/site, effective dates, review status and expiry |
| Approval / Withdrawal | Reviewer, source/access revision, reason and time; separate from successful parsing |
| ParseRun / Chunk | Parser version, exact span, page/heading locator, source hash and provenance |
| IndexGeneration | Eligible corpus, access/publication revisions, build result and atomic publication |
| Conversation / Query / Answer | Private owner, authorized context, model/prompt/corpus identity, typed outcome and claims |
| Citation | Exact source revision/hash, span and page/section locator; resolve under current access |
| GapReport / Feedback | Restricted question, permitted evidence, category, reviewer assignment and retention |
| Job / Audit / Entitlement | Idempotency, remote ID, correlation, settlement and operational history |

Source states: draft -> in_review -> published -> superseded/withdrawn/expired. Effective dates and audience applicability can preserve an older revision for historical questions or another site. Historical mode must be explicit and cannot imply that an old policy applies now. A reviewed future policy is not yet current.

Answer outcomes: answered / needs_clarification / insufficient_evidence / conflicting_sources / unavailable. Do not reveal whether an inaccessible document exists through titles, counts, error details or unanswered-question categories. Model confidence and retrieval scores are not evidence of authorization or correctness.

| Proposed route | Behavior |
|---|---|
| POST /api/workspaces/{id}/documents | Bounded authorized upload as draft; hash and idempotency |
| PATCH /api/documents/{id}/access | Validate delegated access owner and expected revision; revoke affected derived access |
| POST /api/documents/{id}/revisions/{revision}/publish | Validate owner review, audience, effective dates and index readiness |
| POST /api/documents/{id}/revisions/{revision}/withdraw | Block serving immediately and queue derived cleanup |
| POST /api/search | Authorized, current/context-applicable source results with safe snippets |
| POST /api/questions | Create query/job and return typed answer with checked citations |
| GET /api/answers/{id} | Check current grants, freshness and conversation ownership |
| GET /api/sources/{revision} | Scoped original/derived source view with stable page/section locator |
| POST /api/answers/{id}/feedback | Restricted feedback; not automatic source publication |
| POST /api/gaps | Employee-authorized submission to an explicitly named review scope |
| GET /api/gaps | Authorized gap queue; administrative role alone does not reveal questions |
| GET /api/jobs/{id} | Scoped progress, failures and reconciliation state |

Use optimistic concurrency for publication/grants, idempotency for effects and explicit failures for invalid/stale requests. Generic inaccessible responses must not expose restricted metadata. Audit metadata access is also scoped. No API here edits external systems or makes employment/policy decisions.
