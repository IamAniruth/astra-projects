# Invoice Processing Assistant: admin panel specification

Prepared: 4 October 2026  
Project: IP | Status: Planned; documentation only, implementation not started  
Reference: [Support Reply administration](../../05-support-reply-assistant/docs/09-admin-panel-specification.md) and [Quotation administration](../../01-enquiry-to-quotation-assistant/docs/13-admin-panel-specification.md)  
Delivery: [PI-08 and S22-S24](../PI/PI-08-admin-panel/README.md)

## 1. Purpose and scope

A focused administration area is needed for accounting-firm/client access, document intake, validation policies, exception oversight, approval/export governance, subscriptions and recovery. Build inside the proposed React/TypeScript frontend with Next.js business APIs and private Astra runtime, subject to S02 decisions.

Separate workspace administration from platform operations. Within a workspace, enforce explicit client-company grants: membership of an accounting firm does not give every employee access to every client. Platform operators receive safe metadata by default, not unrestricted invoices.

Administration uses the same domain services as the processing workbench. It must not become a second approval, duplicate, PO allocation, job or usage authority. S01/S02 discovery and feasibility still govern implementation.

Initial delivery ends at reviewed CSV/JSON exports. No automatic ledger posting, invoice payment, bank-detail updates, autonomous tax determination or three-way receipt matching is added. Service-subscription billing is separate from paying the invoices being processed.

## 2. Navigation and interface

Illustrative frontend routes are /settings for workspace administration and /admin for platform operations. Enforce server permissions on every route, list, count, job and artifact independently of visible navigation.

| Screen | Scope | Purpose |
|---|---|---|
| Overview | Workspace/client or platform | Intake errors, review backlog, exceptions, processing health and usage |
| Clients and access | Workspace | Client-company profiles, invitations, roles, assignments and revocation |
| Onboarding | Workspace; platform metadata | Permitted samples, supported inputs, reviewers and first approved export |
| Intake and processing | Client-scoped | Upload batches, unsupported files, parser/OCR state, provenance and jobs |
| Suppliers and checks | Authorized client staff | Supplier aliases, duplicate suggestions, PO versions/allocations and rule profiles |
| Review governance | Client-scoped reviewers | Exception history, separation of duties, approval revisions and export mapping |
| Plan and usage | Workspace billing permissions | Service subscription, document allowance, adjustments and invoices |
| Service customers | Platform | Onboarding, subscription reconciliation and controlled support |
| Markets and exports | Configuration permissions | Qualified input/language/calculation/export profiles and availability |
| Health, audit and data requests | Scope-limited | Incidents, support-access grants, exports/deletion and restore evidence |

Use searchable, paginated lists with accessible labels, keyboard navigation, empty/error/loading states and explicit workspace/client selection. Show environment, display time zone and last refresh. Counts and search suggestions must not reveal inaccessible clients.

## 3. Proposed permissions

Roles below are permission bundles to confirm in S03/S11; client grants remain necessary for business records.

| Role | Allowed responsibility | Boundary |
|---|---|---|
| Workspace owner | Organization settings, membership and separately granted billing | No platform access; invoice approval still follows reviewer policy |
| Workspace administrator | Client assignments, imports and permitted configuration | Cannot grant platform privileges or bypass separation of duties |
| Preparer | Upload, review candidates, correct fields and submit permitted invoices | Approval only if policy explicitly permits the role combination |
| Reviewer/approver | Resolve permitted exceptions and approve exact revisions | Cannot approve unresolved critical fields or alter old approved snapshots |
| Viewer/auditor | Read permitted records/history and allowed exports | No mutations |
| Platform operations | Redacted workspace/job health and controlled recovery | Customer content needs an approved scoped grant |
| Platform billing | Service subscriptions and authorized entitlement actions | No default invoice/PO/bank-detail access |
| Platform access administrator | Operator accounts and permissions | No implicit authority over customer invoice approval |

Use individual accounts, MFA for privileged administrators, session revocation and least-privilege grants. Enforce workspace and client ownership on child records and foreign-key relationships. Recheck access before queued work executes and before its output is viewed.

Support access records purpose, workspace/client, permitted records/actions, approving authority, operator and expiry. Audit grants and content reads. Exclude unrestricted impersonation. Redact bank details and sensitive invoice fields from routine dashboards/logs.

## 4. Client onboarding and document intake

Track data-processing permission, supported market/input classes, named domain reviewer, import/export target, permitted sample batch, first reviewed invoice and first approved export. Account setup or payment does not establish extraction quality.

Keep business country, UI language, time zone, invoice currency and subscription currency separate. Client suppliers and aliases are client-owned; identical names across clients never trigger a global merge.

Show upload attempts, original hashes, detected document class, page count, parsing/OCR versions, source spans and typed failures. Preserve immutable originals and repeated-upload provenance. Retry idempotency prevents accidental duplicate operations, while an intentional repeated upload remains traceable.

Unsupported handwriting, password-protected documents, credit notes, receipts, statements, mixed-document bundles and cross-currency matching remain blocked or explicitly routed to manual handling until qualified. Poor OCR or missing pages cannot silently appear as successful complete extraction.

## 5. Validation profiles and exceptions

Version reviewer-approved normalization, rounding, tolerance and export profiles with owner, applicability, evidence and effective time. Profiles specify supported language/document classes and calculation structures; they are not a universal tax engine.

Preserve raw text and source references beside normalized values. Missing values remain null rather than zero; leading-zero identifiers remain strings. Ambiguous dates, currencies and quantities need review instead of inference from supplier names or symbols.

Use deterministic decimal arithmetic. Retain declared and computed totals, including line/header discounts, freight, withholding or prior payments where supported. Discrepancies become exceptions. Changing a profile must not rewrite a previously approved invoice or its export history.

An exception resolution identifies type, severity, evidence, actor, reason and exact revision. Only permitted noncritical exceptions may be accepted under documented policy. Unresolved critical fields block approval; an admin badge cannot bypass that requirement.

## 6. Duplicate and purchase-order governance

Exact file hashes identify repeated bytes, not necessarily a business duplicate decision. Duplicate suggestions use client-owned supplier identity, invoice number, amount/currency and supporting context. Fuzzy matches remain suggestions; never automatically merge, delete or suppress invoices.

Show both candidate documents and evidence only where the reviewer has access. Record false-positive and confirmed-duplicate decisions with reasons. Do not disclose another client's invoice through a duplicate alert.

PO comparisons use versioned POs, explicit units/currency, approved tolerances and cumulative allocations across partial invoices. Missing PO is an exception; received-goods matching is deferred. Bank details in extracted text do not update supplier master data or authorize payment.

Protect allocation updates transactionally under concurrent approvals. Reapprovals, reversals or new revisions must explicitly reconcile allocations so the same invoice is not counted twice and remaining PO capacity is not exceeded. Preserve allocation history and verify the current PO/version before approval.

## 7. Approval and export administration

Show source document/hash, extraction/parser/model/schema versions, corrections, exception dispositions, PO allocation evidence, reviewer and exact revision. Editing approved content appends a new unapproved revision; historical approvals remain immutable.

Enforce preparer/reviewer separation under the agreed policy. Approval atomically checks current grants, exact revision, critical fields, required exception dispositions and applicable allocation constraints. Reject stale or concurrent conflicts rather than overwriting decisions.

CSV/JSON exports bind approved revision IDs to a versioned mapping and artifact hash. Validate current access and mapping eligibility at generation/download. Sanitize formula-leading spreadsheet text under the documented mapping and verify round-trip identifiers, amounts and dates.

Re-export is idempotent for the chosen operation but remains auditable. A changed mapping creates a new artifact/history entry without rewriting the approved invoice. Exported does not mean posted to an accounting ledger, paid or reconciled. No ledger connector is enabled.

## 8. Jobs and recovery

List logical job, workspace/client, document/input version, attempt, remote Astra ID, safe failure, queue age, budget and usage settlement. Restrict originals/candidate values separately from job metadata.

Astra owns accepted inference execution and cancellation; product workers own their parsing/export effects. Persist remote IDs and reconcile an uncertain accepted outcome before retrying. A timeout alone is not proof the remote operation failed.

Retry only eligible states after current permission, input, budget, entitlement and active-attempt checks. Protect effects with idempotency and concurrency controls. Cancellation remains requested until acknowledged or reconciled. Recovery cannot mutate an approved snapshot or silently replace reviewer corrections.

Display whether an action consumes allowance under the agreed rule. Keep incomplete parsing/extraction and manual fallback clearly labelled.

## 9. Service billing and markets

The commercial hypothesis is a subscription with document allowances and optional onboarding fees. Confirm what counts as a document, page limits, failed/retried extraction treatment, export charges if any and reset boundaries before sale.

Use server-verified provider state for paid access. Verify webhook signatures, deduplicate events, reconcile out-of-order/missed updates and enforce limits at admission and execution. Display reserved, consumed, released and adjusted units; adjustments append ledger records with reasons.

Time-limited entitlement exceptions require authorization, reason and expiry without changing actual payment status. Keep suspension, subscription cancellation, service-fee refunds and data deletion separate. Initially route complex billing transactions through the configured provider dashboard and reconcile results.

Version offers and keep existing subscription terms unless explicitly migrated. Report revenue per currency, separate onboarding fees from recurring revenue, and label cost estimates.

New markets/input classes/export profiles start disabled. S14 qualification covers actual language/OCR/extraction, currency/date conventions, arithmetic rules and target import behavior, plus applicable commercial/operational readiness. Unsupported combinations cannot be sold as ready. Optional expansion stays S21.

## 10. Audit, data lifecycle and health

Audit actor, permission context, client/workspace, action, target, timestamp, operation ID, outcome and redacted before/after values. Include grant changes, sensitive reads, profile changes, exception decisions, approvals, allocation changes, recovery, exports and entitlement adjustments. Ordinary administrators cannot edit audit history.

Verified data requests identify requester, permitted scope, owner and completion evidence. Cover original invoices/POs, OCR, candidates, revisions, indexes, temporary files, artifacts and feedback where present, with documented backup expiry and justified audit/billing retention. Deleting a list row is not completion.

Restore and rollback must apply current revocations/deletions and reconcile jobs, allowances and PO allocations before resuming work. Do not resurrect suppressed access or duplicate allocation/usage effects.

Health includes product API, private Astra, parsing/OCR workers, queue age/leases, storage, error rates, billing lag, backups and last restore drill. Show observation time and distinguish unknown/stale from healthy. Incidents have an owner, impact, updates and recovery decision.

Require target/effect confirmation for privileged/destructive changes, plus backend validation, rate limits, request-forgery protection where applicable, idempotency and stale-version detection. Keep secrets server-side.

## 11. Quality and later improvements

Readiness views show actual model/prompt/parser/schema/corpus/host versions, registered thresholds, denominators, independent reviewer and unresolved failures. Track critical-field accuracy, line items, exception recall, duplicate precision/recall, false positives, review time, latency and cost.

S16-S18 supply real evaluation/pilot/release results. Missing evidence appears pending; a successful UI demonstration or accepted export does not establish extraction quality. Record unsupported input classes explicitly.

Corrections and duplicate decisions do not automatically authorize training. Optional consented feedback, evaluated model improvement and qualified expansion remain S19-S21; administration adds no automatic retraining or external model fallback.

## 12. Proposed records and API additions

Reuse [existing data/API contracts](04-data-and-api.md), especially revision, approval, export and job authorities. Add explicit policy/profile versions, support-access grants, onboarding records, entitlement adjustments, incidents and data requests where required.

| Proposed route | Behavior |
|---|---|
| GET /api/admin/workspaces | Platform-safe service customer metadata |
| GET /api/clients/{clientId}/admin/overview | Authorized client aggregates |
| PATCH /api/workspaces/{id}/memberships/{memberId} | Versioned role/client-grant change |
| POST /api/admin/support-access | Approved, scoped, expiring access |
| POST /api/clients/{clientId}/validation-profiles | Reviewed version; activation requires qualification |
| POST /api/invoices/{id}/exceptions/{exceptionId}/resolutions | Evidence/reason/revision-bound disposition under policy |
| POST /api/jobs/{id}/reconcile | Resolve outcome through the owning service |
| POST /api/jobs/{id}/retry | Eligible idempotent recovery |
| GET /api/workspaces/{id}/usage | Authorized service-usage ledger |
| POST /api/admin/workspaces/{id}/entitlement-adjustments | Expiring reasoned adjustment |
| GET /api/admin/audit | Scoped redacted events |
| POST /api/clients/{clientId}/data-requests | Verified export/deletion request |
| GET /api/admin/health | Restricted health observations |

These are proposals, not implemented endpoints. Derive tenant/client access from authenticated membership; request IDs are not proof. Return typed validation, permission, conflict, unavailable and reconciliation failures with safe correlation IDs.

## 13. Delivery and acceptance

| Sprint | Admin outcome | Existing service dependencies |
|---|---|---|
| [S22](../PI/PI-08-admin-panel/S22-admin-access-clients/sprint-plan.md) | Workspace/client access, onboarding and support grants | S03; S13 commercial onboarding |
| [S23](../PI/PI-08-admin-panel/S23-admin-invoice-governance/sprint-plan.md) | Intake, profiles, duplicate/PO exceptions and approval/export governance | S04-S12; S14 profile qualification |
| [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Jobs, billing, markets, health, audit, retention and readiness | S06/S13-S15; consumes S16-S18 evidence |

Earlier sprints own domain services; PI-08 owns admin screens and integrated operator acceptance. Optional PI-07 is not a prerequisite. Required controls precede the S17 paid pilot and feed S18 release; evidence views can display pending S16-S18 results during development.

- [ ] Workspace and client boundaries hold for lists, counts, files, duplicates, POs, jobs, exports and audit.
- [ ] Revoked users and expired support grants lose current, cached and in-flight access.
- [ ] Unsupported inputs, ambiguity and missing evidence remain visible; raw/normalized/declared/computed values remain distinct.
- [ ] Duplicate suggestions never auto-delete or merge records; PO allocation is correct under concurrent/repeated approval.
- [ ] Critical unresolved fields block approval and edits create unapproved revisions.
- [ ] Export pins approved revisions/mapping, preserves round-trip values and never implies ledger posting or payment.
- [ ] Job uncertainty reconciles before retry; repeated operations cannot duplicate usage or allocation effects.
- [ ] Verified billing, allowance limits and expiring exceptions preserve payment truth.
- [ ] Sensitive reads/changes are attributable; deletion/restore covers originals and derived records.
- [ ] Market/profile activation uses real qualification and readiness states remain honest.
- [ ] End-to-end permitted intake, review, exception resolution, approval and CSV/JSON export passes with named reviewers.

## 14. Decisions before implementation

Confirm role owners and separation of duties, client assignment policy, support-access authority, critical fields, permitted exception dispositions, duplicate rules, PO allocation/reversal semantics, tolerances, rounding/export profiles, usage/retry policy, provider/grace terms, retention and first market/input class.

Record decisions in [the project register](08-decisions-and-references.md). This specification adds planning only; no runtime, application, integration or deployment is claimed.
