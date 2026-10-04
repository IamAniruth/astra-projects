# Manual and Troubleshooting Assistant: admin panel specification

Prepared: 4 October 2026  
Project: MT | Status: Planned; documentation only, implementation not started  
Reference: [Support Reply administration](../../05-support-reply-assistant/docs/09-admin-panel-specification.md) and [Invoice administration](../../02-invoice-processing-assistant/docs/09-admin-panel-specification.md)  
Delivery: [PI-08 and S22-S24](../PI/PI-08-admin-panel/README.md)

## 1. Purpose and boundaries

A focused administration area is needed to manage site/equipment access, approved manuals, applicability rules, indexing, expert escalation, team subscriptions and service recovery.

Build inside the proposed React/TypeScript frontend and Next.js business APIs with private Astra integration, subject to S02 decisions. Workspace administration manages customer sites, equipment and sources. Platform administration manages service customers and operations without default access to private manuals.

Reuse the existing source, procedure, job and entitlement services. An admin role must not create a second publication authority or bypass equipment applicability. S01 discovery and S02 feasibility remain implementation gates.

Initial delivery supports approved-source lookup, bounded cited answers, approved troubleshooting branches and internal escalation. It adds no equipment operation, remote control, invented repairs, external ticket submission, automatic messages or unqualified diagram interpretation.

## 2. Screens and navigation

Illustrative frontend routes are /settings for workspace administration and /admin for platform operations. Backend authorization protects every action and artifact independently of navigation.

| Screen | Scope | Main responsibility |
|---|---|---|
| Overview | Separate workspace/platform views | Onboarding, publication blockers, unresolved cases, usage and service health |
| Sites, equipment and access | Workspace | Membership, site/document grants, verified asset identity and assignments |
| Manual registry | Authorized document owners | Draft revisions, provenance, review, applicability and withdrawal |
| Parsing and indexing | Scoped workspace; safe platform metadata | Parser issues, page mapping, generation validation and publication status |
| Procedure governance | Domain reviewers | Approved branches, required context, applicability and version history |
| Escalations | Assigned experts | Unresolved questions, permitted evidence and explicit outcomes |
| Plans and usage | Workspace billing permissions | Team/site limits, usage, renewal and invoice references |
| Service customers | Platform | Onboarding, subscription reconciliation and restricted support |
| Supported scope | Authorized configuration owners | Qualified equipment families, languages, input classes and modalities |
| Health, audit and data requests | Scope-limited | Incidents, support access, deletion, recovery and readiness evidence |

Use search, filters, pagination, accessible forms, keyboard operation and clear loading/empty/error states. Show workspace/site context, environment, time zone and freshness. Lists, counts, source titles and search suggestions must not disclose inaccessible sources or sites.

## 3. Proposed permission model

Confirm exact role combinations during S03 and domain review.

| Role | Responsibility | Boundary |
|---|---|---|
| Workspace owner | Organization settings, memberships and separately granted billing | No platform privileges or automatic source/procedure approval |
| Site administrator | Assigned site equipment, access and onboarding | Cannot grant access beyond own authority |
| Document owner/reviewer | Review exact manual revisions and applicability; approve/withdraw | Parsing success does not establish source authority |
| Domain expert | Assigned escalations and qualified procedure review | Expert replies remain separate from published manuals until approved |
| Technician | Permitted questions, sources, observations and escalation | Cannot publish manuals or invent procedure branches |
| Viewer/auditor | Read explicitly permitted history and evidence | No mutations |
| Platform operations | Redacted job/health metadata and controlled recovery | Manual content requires a separate approved scoped grant |
| Platform billing/access permissions | Service billing or operator membership management | No implied authority to approve customer procedures |

Use individual accounts, MFA for privileged administrators and timely session/grant revocation. Server-side lookups enforce tenant/site/document scope, including nested records, jobs, citation viewers, histories and caches. A customer owner cannot grant platform privileges.

Scoped support access records operator, purpose, workspace/site/document scope, approving authority and expiry. Audit grants and content reads; exclude unrestricted impersonation. Ordinary operational logs contain safe metadata, not manual text or sensitive site details.

## 4. Site and equipment onboarding

Track customer document rights, equipment-family scope, named document/domain reviewers, supported language/input class, approved source corpus, first cited answer or explicitly labelled search-only result, and tested escalation path. Onboarding completion does not establish model quality.

Record manufacturer, model, variant and applicable serial/firmware identifiers with verification provenance. Unknown applicability is not a match. Do not guess an asset from a symptom or fault code. Equipment edits are versioned and require stale-context checks for active queries, caches, answers and procedure sessions.

Keep site country, interface/source language, time zone, subscription currency and hosting location independent. Equipment availability and supported AI scope must match actual qualification. An unfamiliar asset can enter clearly labelled document discovery, but cannot silently receive procedural guidance.

## 5. Manual registry and publication

Each immutable manual revision records publisher, source hash, owner, revision label, language, approval/effective state, allowed audience and explicit model/variant/serial/firmware rules.

Workflow:
1. Upload privately as a draft with rights and provenance.
2. Parse using a qualified bounded parser; inspect missing pages, warnings, source mapping and unsupported structures.
3. Have an authorized reviewer assess the exact revision and applicability.
4. Build and validate an index generation with source hashes and permission/applicability revisions.
5. Publish atomically only after required review and index validation.

Approval, parsing success and index readiness are distinct states. Preserve physical page index and printed page label in citation previews. Chunking must retain section/procedure boundaries and cross-page prerequisites, warnings, steps, units, negation and stop conditions.

Only approved, applicable, accessible revisions support answers. Upload date alone cannot determine precedence: an older revision may still govern an older serial range. Conflicting applicability must be resolved through an explicit documented rule or domain escalation rather than silently choosing the newest file.

Unreadable scans, uncertain tables, diagrams/schematics, handwriting, videos and translated procedures remain unsupported for interpretation until separately qualified. Viewing an original diagram is distinct from interpreting it.

## 6. Withdrawal, supersession and history

Show a scoped impact preview of affected assets, index generations, answers, caches and procedure sessions before a lifecycle action. Record reviewer, scope, reason and revision/version; protect against concurrent stale updates.

Withdrawal blocks affected passages immediately at retrieval and answer delivery, even if index cleanup is asynchronous. Citation openings, saved answers, follow-up questions and active procedures recheck current access, source validity and applicability. Invalidate or withhold obsolete guidance; preserve authorized historical metadata without presenting it as current procedure.

Supersession is applicability-specific. Replacing the revision for one serial range must not disable an older valid revision for another range. A rollback or restored index must apply current withdrawal tombstones and grants before becoming available.

A platform operator cannot clear a withdrawal by retrying a job, restoring a backup or changing an admin badge. Re-publication requires the authorized lifecycle and qualification process.

## 7. Procedure and escalation governance

A procedure session pins the approved version, equipment context, required qualifications/prerequisites, branch observations and stop conditions. Preserve approved step order and mandatory context; do not merge incompatible manuals into a new procedure.

Unknown observations remain unknown. Missing prerequisites, conflicting evidence, changed equipment or withdrawn sources pause affected guidance and request clarification or expert review. Administrators cannot use a generic force-continue action to bypass these checks.

Expert escalation shows the question, authorized evidence snapshot, unresolved reason, assigned role, updates and explicit reviewer outcome. Recheck permissions before revealing source-bearing records. Expert replies are case-specific feedback until separately reviewed as approved knowledge. Closing an escalation does not certify that equipment was repaired or safe to operate.

The initial workflow creates internal cases only. No equipment commands, unsolicited email or external ticket integration is enabled. Service feedback does not grant training permission.

## 8. Jobs and operational recovery

Track parsing, indexing, retrieval and answer jobs with environment, workspace/site, input/corpus/equipment versions, attempts, remote Astra ID, safe errors, budget and usage settlement.

Astra owns accepted remote inference execution and cancellation. Product workers may own parsing/indexing effects. Persist remote IDs and reconcile uncertain outcomes before resubmission; a lost response alone does not establish failure.

Retry only eligible work after current access, source state, applicability, input version, entitlement, budget and active-attempt checks. Use idempotency and concurrency to prevent duplicate effects or usage. A retry cannot republish withdrawn material.

Cancellation stays requested until acknowledged or reconciled. Distinguish runtime unavailable from insufficient evidence, conflicting sources, needs clarification and escalation. If the evidence exceeds the context budget, narrow the query or show the approved full source rather than omit mandatory context.

## 9. Subscriptions, usage and supported scope

The commercial hypothesis is per-site or team subscription plus document onboarding. Confirm seat/site counting, included queries or processing, storage/page limits, retry/failure/index-build treatment and period resets before publishing offers.

Billing access follows server-verified provider state. Verify signatures, deduplicate events, reconcile missed/out-of-order updates and enforce limits when accepting and starting work. Show reserved, consumed, released and adjusted usage. Append reasoned adjustments instead of rewriting history.

Temporary access exceptions require permission, reason and expiry and do not change payment truth. Keep processing suspension, subscription cancellation, service-fee refunds and data deletion separate. Initially use the configured provider dashboard for complex financial actions, then reconcile back to the product.

Version offers and retain agreed terms unless an explicit migration is scheduled. Report revenue by currency and distinguish onboarding fees from recurring revenue. Label processing costs as measured or estimated.

Supported equipment/language/input/modality combinations require S14 evidence and later release qualification. Unknown or failed combinations stay disabled or explicitly limited to approved passage search. Do not average a failed equipment family into a passing overall score. Optional expansion remains S21.

## 10. Audit, retention and health

Audit actor, role/scope, target, action, time, operation ID, outcome and safe before/after values for grants, source publication/withdrawal, applicability edits, procedure settings, sensitive reads, support, recovery and entitlements. Ordinary admins cannot edit the event history.

Verified data requests identify requester, scope, owner, policy and completion evidence. Cover originals, OCR, chunks, indexes, cached prompts/answers, temporary files and source-bearing escalations/feedback, with documented backup expiry and justified audit/billing retention.

Restores and index rollbacks must apply current deletions, withdrawals and grants before service resumes, then reconcile jobs/usage. Retained history must not become a path to obsolete or unauthorized procedure guidance.

Monitor API/private Astra/workers, queue age/leases, index generation health, storage, error rates, billing-sync lag, backups and last restore drill. Show timestamps and distinguish unknown/stale from healthy. Incidents have named owners, customer impact and recovery evidence.

Require precise target/effect confirmations for sensitive actions and backend validation, request-forgery controls where applicable, rate limits, idempotency and optimistic concurrency. Secrets stay in server infrastructure.

## 11. Quality and release evidence

Readiness views show model/prompt/parser/corpus/index/asset-profile/host versions, thresholds, denominators, independent reviewer and pending/failed/accepted outcomes. Measure applicability, retrieval recall, claim support, citation correctness, mandatory-context retention, abstention/escalation, information-location time, latency and cost.

A valid citation proves a page resolves, not that the answer is supported. Search-only results cannot satisfy synthesized-answer acceptance. Critical unsupported procedural instructions or access leaks remain release blockers under the existing quality plan.

S16-S18 supply actual evaluation, pilot and release evidence. Until available, show pending rather than a readiness score implying success. Optional S19/S20 feedback and improvement require separate permission and evaluated release; no automatic training or external model fallback is added.

## 12. Proposed API and record additions

Reuse [data/API contracts](04-data-and-api.md), especially manual approval/withdrawal, questions, source viewers, procedures and escalation. Extend with scoped support grants, onboarding records, versioned supported-scope configuration, entitlement adjustments, incidents and data requests where needed.

| Proposed route | Contract |
|---|---|
| GET /api/admin/workspaces | Platform-safe service customer metadata |
| GET /api/sites/{siteId}/admin/overview | Authorized aggregates without source-title leakage |
| PATCH /api/workspaces/{id}/memberships/{memberId} | Versioned site/document grants |
| PATCH /api/equipment/{assetId} | Expected-version identity change with context invalidation |
| GET /api/manuals/{id}/revisions/{revision}/impact | Permission-filtered lifecycle impact |
| POST /api/admin/support-access | Approved scoped grant with expiry |
| POST /api/jobs/{id}/reconcile | Ask the existing owner to resolve uncertainty |
| POST /api/jobs/{id}/retry | Eligible idempotent recovery |
| GET /api/workspaces/{id}/usage | Authorized service ledger |
| POST /api/admin/workspaces/{id}/entitlement-adjustments | Reasoned expiring adjustment |
| GET /api/admin/audit | Scoped redacted history |
| POST /api/sites/{siteId}/data-requests | Verified export/deletion request |
| GET /api/admin/health | Restricted health and observation times |

These are proposals, not implemented endpoints. Derive grants from authentication; IDs are not proof. Use typed validation, permission, conflict, unavailable and reconciliation failures without leaking inaccessible source metadata.

## 13. Delivery and acceptance

| Sprint | Admin delivery | Existing service dependencies |
|---|---|---|
| [S22](../PI/PI-08-admin-panel/S22-admin-sites-equipment-access/sprint-plan.md) | Sites, equipment, access, onboarding and support grants | S03; S13 commercial onboarding |
| [S23](../PI/PI-08-admin-panel/S23-admin-manual-procedure-governance/sprint-plan.md) | Manual publication/applicability, withdrawal, procedures and escalation | S04-S12; S14 qualification |
| [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Jobs, billing, scope controls, health, audit, data lifecycle and readiness | S06/S13-S15; consumes S16-S18 evidence |

Earlier sprints own domain services; PI-08 owns administration surfaces and integrated operator acceptance. It does not depend on optional PI-07. Required controls precede S17 paid-pilot acceptance and feed S18 release; pending quality results do not create a circular entry dependency.

- [ ] Tenant/site/document access holds for lists, counts, search, viewers, histories, jobs and escalations.
- [ ] Revocation and support-grant expiry block cached and in-flight access.
- [ ] Unknown equipment requires clarification; asset changes invalidate incompatible active context.
- [ ] Only approved/applicable revisions with validated indexes support answers.
- [ ] Withdrawal blocks use immediately across indexes, caches, answers and active procedures; valid older asset ranges remain supported.
- [ ] Procedures retain required context/order and stop conditions; expert replies cannot auto-publish.
- [ ] Remote uncertainty reconciles before retry without duplicate effects, usage or re-publication.
- [ ] Verified billing and expiring access exceptions preserve payment truth.
- [ ] Deletion/restore respects current grants, tombstones and source-bearing derived records.
- [ ] Scope activation uses real evidence and unknown/failed readiness remains explicit.
- [ ] A permitted upload-review-publish-query-cite-escalate-withdraw journey passes with named reviewers.

## 14. Open decisions

Confirm role owners, support-access authority, asset verification, applicability precedence, publication/withdrawal and procedure review policies, escalation ownership, usage/site/team counting, provider/grace policy, retention, thresholds and first equipment/language/input scope.

Record outcomes in [decisions](08-decisions-and-references.md). No maintenance instruction, certification, runtime installation, application implementation or deployment is supplied by this planning document.
