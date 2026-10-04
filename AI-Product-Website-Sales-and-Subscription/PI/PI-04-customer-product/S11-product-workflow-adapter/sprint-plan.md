# WS S11: Entitled AI workflow and reviewed result integration

**Status:** Planned  
**PI:** [PI-04 Customer onboarding and product integration](../README.md)  
**Module:** M11  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a customer or authorized service owner, I can rely on entitled ai workflow and reviewed result integration with explicit scope, correct access and traceable outcomes.

- WS-S11-F01: Connect one qualified product from input through review/result
- WS-S11-F02: Private job correlation, cancellation and unknown-outcome reconciliation

## Dependencies and entry criteria

S02 ownership/contracts, S09 quota and S10 setup; chosen product's real workflow and quality evidence are external prerequisites.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S11-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S11-T02 | Frontend/product design | Product entry, progress/result links and clear unavailable/manual-fallback states. |
| WS-S11-T03 | Backend/data | Scoped product handoff, operation/remote IDs and result references. |
| WS-S11-T04 | Integration/operations | Integrate the actual private runtime through product-owned services; reconcile accepted remote work before retry. |
| WS-S11-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S11-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S11-AC1: Payment leads to the purchased qualified workflow, not merely an empty dashboard.
- [ ] WS-S11-AC2: Cross-tenant input/results and revoked entitlements fail at admission/execution/delivery.
- [ ] WS-S11-AC3: Timeout/duplicate handoff cannot duplicate inference, exports or usage; review remains product-owned.
- [ ] WS-S11-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S11-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S11-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Run an authorized input-to-reviewed-result flow, then simulate lost remote acceptance and revoke access.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
