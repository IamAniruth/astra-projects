# IP S22: Admin access and client management

PI-08 | Module M22 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized workspace administrator, I can use admin access and client management with explicit client boundaries, source evidence and accountable actions.

- IP-S22-F01: Workspace/platform navigation, scoped client overview and onboarding
- IP-S22-F02: Administrative memberships, client grants, revocation and support access

## Dependencies and entry criteria

Accepted S01 discovery and S02 feasibility decisions; S03 identity/workspace/client contracts. Integrate S13 commercial onboarding and any seat policy before commercial use. Confirm separation of duties, role combinations, support-access authority, MFA and client assignment rules.

Assign named product/domain, React, Next.js/data, Astra integration and QA/operations owners. Confirm data permissions, contract versions and capacity. Fixtures may unblock UI development but cannot prove real-model/provider/host readiness. PI-07 is not required.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| IP-S22-T01 | Product/security: approve the role-action-client matrix, onboarding checklist, support-access scope/expiry and named owners. |
| IP-S22-T02 | React/Next.js: build scoped workspace/client navigation, lists/counts, membership actions and onboarding; reject cross-client IDs, stale edits and platform privilege escalation on the server. |
| IP-S22-T03 | Backend/data: enforce MFA/session revocation, expiring support grants and audit; propagate current scope to jobs, exports, cached results and private files. |
| IP-S22-T04 | QA/security: execute two-workspace/two-client access negatives, revoked in-flight access, conflicting membership edits and support-grant expiry; capture browser/API evidence. |

Reuse the existing domain APIs and records in [data/API contracts](../../../docs/04-data-and-api.md), extending them through the admin specification. Validate client/workspace scope server-side for every nested lookup. Use typed validation, permission, conflict and reconciliation errors with safe correlation IDs. Privileged actions require appropriate confirmation, authorization, idempotency/concurrency and audit, not just hidden buttons.

## Acceptance

- [ ] IP-S22-AC1: Workspace owners cannot invoke platform actions; membership alone never exposes unassigned clients through list/count/search/file/job/export/audit paths.
- [ ] IP-S22-AC2: Revocation and support-grant expiry block old links, sessions and in-flight output; permitted sensitive reads are audited and ordinary operators see safe metadata only.
- [ ] IP-S22-AC3: Onboarding, subscription and processing states remain separate; stale membership edits conflict and unfinished commercial dependencies remain visible.
- [ ] IP-S22-AC4: Named reviewers accept accessible loading/error/empty states and direct-API/race evidence with actual versions; fixture-only results remain labelled.

## Verification and demonstration

Onboard accounting workspace A with clients X/Y, assign a preparer only X, deny Y and workspace B, then revoke the assignment and expire an operator support grant while processing is active.

Use domain checks for arithmetic/state, integration checks for permissions/storage/jobs/allocations and browser checks for changed journeys. Include direct API negatives and races, not only happy-path clicks.

Retain a feature/task checklist, contract/migration record, redacted traces/screenshots, actual results including failures, and named reviewer decision. Record application, policy, mapping and applicable model/prompt/parser/corpus/host versions. No unapproved invoices or secrets belong in evidence. Mocks and provider sandbox results remain labelled and cannot imply live readiness.

## Exit and handoff

Review against the complete [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete prerequisites and failed checks explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 release.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. No ledger posting, payment initiation, supplier-bank update or automatic training is enabled by this sprint plan.
