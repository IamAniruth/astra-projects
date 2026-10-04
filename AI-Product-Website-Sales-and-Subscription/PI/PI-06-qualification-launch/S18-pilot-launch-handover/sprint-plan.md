# WS S18: Paid pilot, release evidence and handover

**Status:** Planned  
**PI:** [PI-06 Market qualification, recovery and launch](../README.md)  
**Module:** M18  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a customer or authorized service owner, I can rely on paid pilot, release evidence and handover with explicit scope, correct access and traceable outcomes.

- WS-S18-F01: Measured buyer pilot and commercial end-to-end validation
- WS-S18-F02: Controlled launch checklist, ownership and rollback handover

## Dependencies and entry criteria

S01-S17 applicable acceptance plus chosen product quality/commercial-license evidence; no release until blockers close.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S18-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S18-T02 | Frontend/product design | Reviewed supported-scope/pricing/help content and customer handover. |
| WS-S18-T03 | Backend/data | Pilot scorecard, versioned release manifest, checklist and actual support/incident owners. |
| WS-S18-T04 | Integration/operations | Controlled publish/deploy only during authorized implementation; verify purchase-to-reviewed-result and cancellation. |
| WS-S18-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S18-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S18-AC1: A real permitted pilot meets agreed useful-task/review/renewal/cost criteria or launch stays blocked.
- [ ] WS-S18-AC2: Release evidence identifies actual app/model/config/host/market versions and outstanding limits.
- [ ] WS-S18-AC3: No page/checkout/demo success substitutes for product quality, restore or commercial readiness.
- [ ] WS-S18-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S18-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S18-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Demonstrate the full buyer journey and failure paths, review pilot results and hand over rollback/support ownership.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
