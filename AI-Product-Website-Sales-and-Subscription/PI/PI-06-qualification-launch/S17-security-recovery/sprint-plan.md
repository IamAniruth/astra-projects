# WS S17: Security, retention and target-host recovery

**Status:** Planned  
**PI:** [PI-06 Market qualification, recovery and launch](../README.md)  
**Module:** M17  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a responsible service operator, I can rely on security, retention and target-host recovery with explicit scope, correct access and traceable outcomes.

- WS-S17-F01: Authorization/privacy hardening and reviewed data lifecycle
- WS-S17-F02: Restore/rollback, capacity and incident runbooks

## Dependencies and entry criteria

S03-S16 implementation; approved retention and data-flow policy; real target-host/model readiness.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S17-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S17-T02 | Frontend/product design | Operator data-request/audit status and restricted recovery evidence views. |
| WS-S17-T03 | Backend/data | Deletion/export across originals/derived records/caches/artifacts with backup/billing exceptions. |
| WS-S17-T04 | Integration/operations | Restore current grants/tombstones, reconcile jobs/usage/subscriptions and measure target-host capacity. |
| WS-S17-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S17-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S17-AC1: Two-tenant/role negatives and redacted logs hold across background work and support access.
- [ ] WS-S17-AC2: Verified data requests produce evidence; restores do not resurrect deleted or unauthorized data.
- [ ] WS-S17-AC3: Backup restore, failed-job recovery and actual host capacity meet agreed targets or remain blockers.
- [ ] WS-S17-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S17-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S17-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Execute a scoped export/deletion and restore drill, model outage and rollback with consistent billing/usage.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
