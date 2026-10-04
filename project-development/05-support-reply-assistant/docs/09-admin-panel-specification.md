# Support Reply Assistant: admin panel specification

Prepared: 4 October 2026  
Project: SR | Status: Proposed documentation; implementation not started  
Related: [Product scope](01-product-scope.md), [architecture](02-architecture-and-setup.md), [data and APIs](04-data-and-api.md), [security and operations](06-quality-security-operations.md)

## 1. Decision: a focused admin area is needed

The planned product needs administration because someone must control agent access to customer cases, approve and withdraw help knowledge, recover processing failures, manage seats or usage, and investigate incidents. These responsibilities already appear in S03, S05, S06, S13 and S15.

Build administration into the authenticated product using the existing proposed React/TypeScript frontend and Next.js business APIs. A separate application or deployment is not required initially. Final technology choices remain subject to S02 feasibility.

Separate two scopes:

- **Workspace administration:** A customer organization's authorized staff manage their own teams, source publications, review policies, and usage.
- **Platform administration:** The service operator manages workspaces, commercial entitlements, infrastructure health, and controlled operational support.

An ordinary support agent uses the case queue and drafting workbench. Workspace or platform administration does not automatically grant permission to read every case, publish policy, approve replies, or disclose internal information.

For a single-team prototype, start with team settings, knowledge publication, and job visibility. Add platform workspace and billing controls when preparing paid pilots. Implementation remains conditional on the existing S01/S02 investigation gates; this document does not mark any sprint accepted.

## 2. Scope and navigation

Illustrative routes are `/settings` for workspace administration and `/admin` for platform operations. Routes are navigation conventions, not security boundaries: every API and artifact lookup must authorize the authenticated user on the server.

| Screen | Scope | Purpose | First delivery |
|---|---|---|---|
| Overview | Each scope separately | Show pending work, failures and permitted operational metrics | S06; extend S13/S15 |
| Teams and access | Workspace | Invitations, roles, team membership and case/source grants | S03 |
| Knowledge library | Workspace | Review, publish, expire and withdraw approved sources | S05 |
| Imports and indexing | Workspace | Validation errors, import conflicts and indexing state | S04-S06 |
| Review policies and history | Workspace | Qualified reply rules and exact-revision approval history | S10-S12; extend S14 |
| Jobs | Workspace; platform metadata | Progress, failure, cancellation and recovery | S06/S09; extend S15 |
| Usage and plan | Workspace | Seats, allowance, usage history and billing visibility | S13 |
| Workspaces and subscriptions | Platform | Assisted onboarding and commercial access | S13 |
| Health, audit and data requests | Scope-limited views | Incidents, privileged changes, export/deletion and recovery | S15 |
| Quality and release evidence | Authorized reviewers/operators | Evaluation records and supported configuration | S16-S18 |
| Feedback and integrations | Qualified scopes only | Governed improvement and separately authorized connectors | Optional S19-S21 |

Use searchable, paginated lists with explicit filters, empty/error states, selected workspace, environment, and display time zone. Record details should link related jobs, source revisions, usage entries and audit events. Hide unavailable actions in the interface and reject unauthorized direct requests in the backend.

## 3. Proposed permissions

Roles are bundles of explicit permissions. A small team may assign several roles to one person; all actions retain the individual's identity.

| Role | Main permissions | Boundary |
|---|---|---|
| Platform owner | Manage operator access, workspace lifecycle and configuration | Customer content access needs a separate scoped grant and audit |
| Platform operations | Inspect safe job metadata, service health and eligible recovery actions | No default case content, publication, reply approval or billing changes |
| Platform billing | Manage configured offers, subscription reconciliation and authorized billing actions | No ticket, article or draft content access |
| Workspace administrator | Manage own organization, invitations, membership and permitted settings | Cannot grant platform privileges or bypass case/source restrictions |
| Knowledge owner | Review and publish exact source/example revisions in assigned scope | Publication does not establish current account/order facts |
| Support lead/reviewer | Review assigned cases and approve permitted reply revisions | Cannot override missing facts, stale dependencies or disclosure blockers |
| Support agent | Work on permitted cases, edit drafts and hand off authorized approved replies | Approval requires a separately granted permission |

Require individual accounts, multi-factor authentication for privileged administrators, secure sessions, and prompt revocation. Enforce tenant, team, case and source grants on imports, retrieval, generation, histories, exports and diagnostics. Recheck grants when queued jobs start and before their output is viewed.

Customer-content support access must identify the workspace, purpose, permitted scope, approving authority and expiry. Audit content reads as well as changes. Avoid unrestricted impersonation in the initial version.

## 4. Dashboard and workspace management

Workspace overview shows permitted counts of import errors, unpublished sources awaiting review, indexing failures, blocked/stale drafts, jobs awaiting recovery, active seats and remaining allowance. Counts must respect case grants so restricted cases are not exposed through aggregate drill-downs.

Platform overview shows onboarding progress, active/suspended workspaces, subscription failures, queue age, runtime availability and reconciliation lag. Display safe metadata by default; label unknown or stale health observations clearly.

A workspace detail page includes organization identity, contacts, plan reference, supported specialty/channel/language, onboarding owner, seats, entitlements, usage and operational history. Onboarding records permitted input sources, named support/knowledge reviewers, the first reviewed draft and manual handoff evidence.

Keep operational suspension, subscription state and onboarding state separate. Suspending processing does not automatically cancel a subscription. Explain effective dates and commercial effects before changing either state.

## 5. Team and access management

Allow authorized workspace administrators to invite users, assign permitted roles, manage teams and case/source grants, and revoke access. Validate seat limits atomically when invitations or memberships consume seats; define the invitation-counting rule in S13.

Show the affected scope before changing grants. Reassignment or revocation must update retrieval permissions and prevent access through cached responses, old artifact links, history screens and active sessions. Pending jobs must not make their output visible to a revoked user.

Preserve historical reviewer identity in audit and approval records after membership removal. Current access to those records still requires authorization.

## 6. Knowledge publication and imports

The knowledge library records owner, source type, immutable revision/hash, product/version applicability, language, audience, effective dates, review state and index generation. Distinguish approved policy/help articles from redacted reusable examples and raw historical tickets.

Publication workflow:

1. Import a draft with provenance, processing permission and visibility metadata.
2. Validate parsing, applicability, dates and proposed audience.
3. Have an authorized knowledge owner review the exact revision.
4. Publish the revision and track indexing readiness separately.
5. Retrieve it only while publication, access and applicability checks remain valid.

Withdrawal immediately blocks new use and invalidates dependent summaries/drafts and approvals. Index cleanup can proceed asynchronously, but current eligibility checks must prevent use of withdrawn content meanwhile. Display affected dependencies without exposing cases the viewer cannot access.

A replacement policy or changed fact can make a previously approved reply stale. Administrators cannot clear that state by changing a badge: a new review of current evidence is required.

Import management shows format, stable case/message IDs, counts, public/private metadata validation, chronology warnings and conflicts. Repeated imports must not duplicate messages; conflicting content under an existing ID requires explicit reconciliation. Do not silently convert private notes to public messages.

Reusable examples require separate review and removal of unrelated customer identifiers. Neither successful replies nor raw imported tickets automatically become policy or training data.

## 7. Reply governance and manual handoff

Configure only qualified language, tone, supported workflow and disclosure rules. Version changes, record their owner and effective time, and require the applicable evaluation before activation. Arbitrary runtime prompt/model editing is outside the initial admin interface.

Approval history shows the reviewer, exact draft and case revision, source versions, fact snapshot times, unresolved issues, and export artifact hash where available. Internal evidence remains in the protected workbench, separate from public reply content.

Before approval and copy/export, recheck current grants, case revision, source validity, fact freshness and disclosure blockers. Editing a reply creates a new revision requiring approval. New messages, withdrawn policy or expired facts invalidate dependent approval.

Handoff records mean **copied** or **exported**. They must never imply sent, delivered, refunded, closed or resolved. The admin panel includes no send, refund-to-end-customer, account-change or ticket-close controls. Service-subscription billing is a separate operational concern.

When no live-fact connector is configured, show missing account/order facts for authorized agent verification. An administrator cannot turn customer assertions or imported historical promises into verified live facts by approving the draft.

## 8. Jobs and operational recovery

Show logical job ID, workspace, type, permitted case/source references, creation time, state, remote Astra ID, queue wait, attempts, safe failure category and usage settlement state. Keep raw customer text and credentials out of operational lists and logs.

Support import, indexing, summary, draft and export jobs with explicit ownership. Astra owns accepted remote inference work and budgets; product workers own import/export effects. The panel invokes the owning service instead of creating a second execution path.

For a timeout or lost connection, display an unknown/reconciling state and reconcile the persisted remote ID before allowing another inference submission. A transport timeout is not proof the remote job failed.

Recovery actions must recheck authorization, input availability, current revisions, entitlements, budget and existing attempts. Use idempotency and concurrency checks to prevent duplicate work, exports or usage settlement. Show whether retrying consumes allowance under the defined counting policy.

Cancellation remains requested until acknowledged or reconciled. A paused workspace prevents new processing according to the incident policy while preserving review and history where allowed. Rollbacks and restored indexes must respect current withdrawals, deletion records and grants.

## 9. Seats, usage and subscriptions

Preserve the project's commercial hypothesis: per-agent subscription or usage-based business plan. Pricing and the usage unit remain open S13 decisions; do not assume quotation-job pricing from another product.

Show plan/version, seat allowance, active/invited seats under the selected counting rule, billing period, consumed/reserved/remaining units, renewal/cancellation state and invoice references. Define whether summaries, generated drafts, manual revisions, retries and failed jobs consume units before publishing an offer.

Maintain a usage ledger with job reference, operation ID, period, unit, quantity and settlement/adjustment reason. Reserve capacity atomically and settle exactly once through the owning workflow. Manual corrections append ledger entries rather than overwrite history.

Backend-confirmed provider state governs paid access. Verify webhook authenticity, deduplicate events, reconcile out-of-order or missing events, and do not activate access from a browser success redirect. Keep billing credentials server-side.

For the first paid pilot, use the provider's authorized dashboard for complex refunds and subscription changes, with reconciliation back to the product. Any temporary entitlement exception needs a reason, expiry and audit entry; it must not change the payment record to paid.

Report collected revenue by currency and separate one-time fees from recurring revenue. Identify estimates in runtime-cost reports. Cancellation, processing suspension, service-fee refunds and data deletion remain distinct operations.

## 10. Audit, retention and service health

Audit actor, permission context, workspace, target, action, reason, time, request/operation ID, outcome and safe before/after values. Record sensitive reads, grant changes, publication/withdrawal, approval/export, recovery, billing overrides and data requests. Ordinary administrators cannot edit audit history.

Export/deletion requests record verified requester, authorized scope, owner, status and completion evidence. Cover cases, attachments, summaries, drafts, indexes, caches, artifacts and feedback, with documented handling of backups, audit and billing records. Restores must reapply current deletions and grants before returning the service to use.

Health views include product API, private Astra runtime, workers, queue age, import/index failures, storage, billing synchronization, backup outcome and last restore drill. Show observation times and named incident ownership. Restrict diagnostics by role and redact sensitive payloads.

Use explicit confirmation for role changes, publication/withdrawal, workspace suspension, entitlement overrides and destructive data operations. Describe the actual target and effect. Apply server-side validation, request-forgery protection where applicable, rate limits and optimistic concurrency; UI confirmations alone do not enforce permissions.

## 11. Quality and later improvement

Authorized reviewers can inspect evaluation records containing checkpoint, prompt/configuration version, source/index hashes, corpus scope, host, thresholds, sample sizes, reviewer decision and unresolved failures.

Report factual support, attribution, disclosure errors, critical omissions, corrections, acceptance, handling time including review, latency and cost. Do not infer customer satisfaction from offline ratings or show draft acceptance as proof of correctness. Observed cross-customer disclosure or critical unsupported commitments remain release blockers under the existing quality plan.

S19/S20 may add permissioned feedback review and candidate release/rollback workflows after qualification. Training permission is separate from service processing and feedback collection. S21 may add individually qualified help-desk or fact connectors; no connector, outbound action or external model fallback is enabled by this specification.

## 12. Backend contracts and records

Extend the existing proposed data model instead of introducing duplicate case, knowledge, approval or job stores. Add explicit permission assignments, onboarding records, entitlement/usage adjustments, scoped support-access grants, data requests and operational incidents where needed.

The following routes are proposals, not implemented endpoints:

| Proposed route | Purpose and authorization |
|---|---|
| GET /api/admin/workspaces | Platform-scoped metadata list |
| GET /api/workspaces/{id}/admin/overview | Workspace-scoped permitted metrics |
| POST /api/workspaces/{id}/invitations | Authorized invitation with seat/idempotency checks |
| PATCH /api/workspaces/{id}/memberships/{memberId} | Scoped role/grant change with version check |
| GET /api/workspaces/{id}/usage | Authorized seats and usage history |
| POST /api/admin/workspaces/{id}/entitlement-adjustments | Time-limited, audited operator adjustment |
| POST /api/jobs/{id}/reconcile | Authorized request to the job's owning service |
| POST /api/jobs/{id}/retry | Eligible, reconciled, idempotent recovery |
| POST /api/jobs/{id}/cancel | Scoped cancellation request; acknowledgement tracked |
| GET /api/workspaces/{id}/audit | Filtered and redacted authorized history |
| POST /api/workspaces/{id}/data-requests | Verified, scoped export/deletion workflow |

Reuse the existing [knowledge publish/withdraw and approval/export contracts](04-data-and-api.md). Require current authorization regardless of supplied workspace or record IDs. Return typed permission, stale-version, blocked-dependency, limit and pending-reconciliation failures without leaking another tenant's records.

## 13. Delivery mapping

Administration now has a dedicated [PI-08 delivery plan](../PI/PI-08-admin-panel/README.md), added on 4 October 2026 at the user's request. Existing sprints below retain domain-service ownership; PI-08 owns admin UI, authorized action orchestration and integrated verification. No implementation or acceptance is claimed.

| Admin sprint | Scope | Service dependencies |
|---|---|---|
| [S22](../PI/PI-08-admin-panel/S22-admin-access-workspaces/sprint-plan.md) | Admin shell, workspaces, teams and scoped support access | S03; S13 seat enforcement before commercial use |
| [S23](../PI/PI-08-admin-panel/S23-admin-knowledge-governance/sprint-plan.md) | Imports, publication, settings and approval/handoff history | S04-S12; S14 setting qualification |
| [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Jobs, billing, usage, health, audit, data requests and quality evidence | S06/S09, S13-S15; consume S16-S18 evidence as available |

PI-08 does not depend on optional PI-07. Coordinate required controls with the owning service sprints before S17 paid-pilot acceptance; S18 includes final admin readiness. Missing quality evidence stays pending rather than creating a dependency on an already completed release.

| Existing sprint | Admin deliverable | Required evidence |
|---|---|---|
| S03 | Team settings, scoped roles/grants and revocation | Two-tenant and restricted-case access checks |
| S04-S06 | Import errors, publication review, indexing/job views | Stable imports, publication eligibility and recovery traces |
| S10-S12 | Review-policy visibility, approval/handoff history | Exact-revision, freshness and public-export checks |
| S13 | Workspace onboarding, seats, usage and billing views | Entitlement and duplicate-event scenarios |
| S14 | Qualified language/tone/policy settings | Domain-review evidence for enabled configuration |
| S15 | Platform health, audited access, recovery and data requests | Restore/deletion drills and job reconciliation |
| S16-S18 | Evaluation evidence and pilot/release readiness | Named reviewer decisions and target-host results |
| S19-S21 | Optional feedback, improvement and integrations | Separate permission, evaluation and connector qualification |

## 14. Admin acceptance checklist

- [ ] Ordinary agents and workspace administrators cannot access platform operations through direct API calls.
- [ ] Tenant/team/case/source restrictions apply to lists, counts, search, files, jobs, history and exports.
- [ ] Revoked membership and seat access cannot be recovered using caches, old links or in-flight output.
- [ ] Unpublished, expired, withdrawn or inapplicable knowledge cannot support a new reply.
- [ ] Withdrawal blocks use immediately, including while index cleanup is pending.
- [ ] New messages, edits and material source/fact changes invalidate affected approvals; administrators cannot force stale export.
- [ ] Public artifacts exclude internal notes, private source URLs and unrelated customer data.
- [ ] Handoff is recorded only as copied/exported; no administrative action sends a reply or executes a customer remedy.
- [ ] Unknown remote-job outcomes reconcile before retry; repeated actions do not duplicate work or usage.
- [ ] Seat and usage limits remain correct under concurrent requests and duplicate billing events.
- [ ] Temporary access exceptions expire and leave actual payment history intact.
- [ ] Privileged changes and sensitive reads produce attributable, redacted audit evidence.
- [ ] Restore and index rollback respect current grants, deletions, withdrawals and stale approvals.
- [ ] Health views distinguish unknown/stale status, and evaluation records do not imply unmeasured quality.
- [ ] A permitted pilot completes import, approved-source retrieval, drafting, exact-revision approval and manual export with traceable administration.

## 15. Open decisions before implementation

Confirm named role owners, allowed role combinations, whether agents may approve their own replies, the support-access approval authority, invitation/seat counting, draft/retry usage rules, payment provider and grace policy, retention periods, operational thresholds and the first supported specialty/channel/language.

Record these decisions in [the decision register](08-decisions-and-references.md) during the owning sprints. S01 discovery and S02 feasibility remain the next project steps. No UI, backend, integration or verification run is claimed by this document.
