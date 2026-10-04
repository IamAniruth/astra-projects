# IP S24: Admin commerce and operational readiness

PI-08 | Module M24 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized service operator, I can use admin commerce and operational readiness with explicit client boundaries, source evidence and accountable actions.

- IP-S24-F01: Service billing, usage, markets and reconciled processing recovery
- IP-S24-F02: Health, audit, data requests and integrated readiness evidence

## Dependencies and entry criteria

S22/S23 administration; S06 jobs/allowances, S13 commerce, S14 market/export qualification and S15 operations/retention. Consume S16-S18 evidence when available, without making completed launch an entry dependency. Confirm usage/page/retry/reset rules, provider/grace policy, retention and thresholds.

Assign named product/domain, React, Next.js/data, Astra integration and QA/operations owners. Confirm data permissions, contract versions and capacity. Fixtures may unblock UI development but cannot prove real-model/provider/host readiness. PI-07 is not required.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| IP-S24-T01 | Product/backend: implement service-subscription/ledger views, verified-event reconciliation, atomic allowances and expiring reasoned adjustments; separate invoice currency from charge currency. |
| IP-S24-T02 | React/Astra integration: build safe job/reconcile/retry/cancel and market controls; persist remote IDs, invoke existing effect owners and block unqualified configurations. |
| IP-S24-T03 | Operations/data: deliver timestamped health/incidents, scoped audit/support and verified data-request flows; reapply revocations/deletions and reconcile usage/PO allocations after restore. |
| IP-S24-T04 | QA/domain/operations: run provider sandbox duplication/out-of-order cases, concurrency and lost-remote-response scenarios, deletion/restore drill and full reviewed-export journey; deliver runbooks and pending/failed/accepted readiness views. |

Reuse the existing domain APIs and records in [data/API contracts](../../../docs/04-data-and-api.md), extending them through the admin specification. Validate client/workspace scope server-side for every nested lookup. Use typed validation, permission, conflict and reconciliation errors with safe correlation IDs. Privileged actions require appropriate confirmation, authorization, idempotency/concurrency and audit, not just hidden buttons.

## Acceptance

- [ ] IP-S24-AC1: Verified provider state governs access; duplicate/out-of-order events and concurrent work do not overgrant allowances or double-settle; exceptions expire without falsifying payment history.
- [ ] IP-S24-AC2: Unknown accepted Astra outcomes reconcile before retry and cancellation stays requested until confirmed; retries recheck scope/input/budget and do not overwrite approved revisions.
- [ ] IP-S24-AC3: Health distinguishes unknown/stale observations; scoped deletion/restore evidence covers originals, derivatives and artifacts and respects current grants, retained records, job/usage/PO consistency.
- [ ] IP-S24-AC4: Qualified markets/profiles and actual versioned quality evidence govern readiness; named reviewers accept integrated access, invoice approval/export, audit and recovery while missing model/host/pilot evidence stays pending.

## Verification and demonstration

Simulate a duplicate renewal, concurrent document processing and a lost response after remote acceptance; reconcile without replaying inference. Exercise an outage and deletion/restore, then complete an authorized invoice-to-reviewed-export workflow with correct usage and audit.

Use domain checks for arithmetic/state, integration checks for permissions/storage/jobs/allocations and browser checks for changed journeys. Include direct API negatives and races, not only happy-path clicks.

Retain a feature/task checklist, contract/migration record, redacted traces/screenshots, actual results including failures, and named reviewer decision. Record application, policy, mapping and applicable model/prompt/parser/corpus/host versions. No unapproved invoices or secrets belong in evidence. Mocks and provider sandbox results remain labelled and cannot imply live readiness.

## Exit and handoff

Review against the complete [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete prerequisites and failed checks explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 release.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. No ledger posting, payment initiation, supplier-bank update or automatic training is enabled by this sprint plan.
