# WS S09: Allowance reservation and product entitlements

**Status:** Planned  
**PI:** [PI-03 Payments, subscriptions and usage](../README.md)  
**Module:** M09  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a customer or authorized service owner, I can rely on allowance reservation and product entitlements with explicit scope, correct access and traceable outcomes.

- WS-S09-F01: Atomic quota admission, period boundaries and ledger
- WS-S09-F02: Customer usage visibility, adjustments and cost basis

## Dependencies and entry criteria

S08 confirmed entitlement periods and S02 product adapter; approved counting/failure/retry rules.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S09-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S09-T02 | Frontend/product design | Remaining/reserved/consumed usage, warnings and explicit upgrade guidance. |
| WS-S09-T03 | Backend/data | Atomic reserve/consume/release ledger and expiring reasoned entitlement exceptions. |
| WS-S09-T04 | Integration/operations | Recheck entitlement when queued work starts; share operation IDs with product execution. |
| WS-S09-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S09-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S09-AC1: Concurrent work cannot exceed allowance or settle the same operation twice.
- [ ] WS-S09-AC2: Renewal resets and retries obey defined periods; manual corrections append ledger events.
- [ ] WS-S09-AC3: Access exceptions expire without falsifying payments and costs distinguish measured from estimated.
- [ ] WS-S09-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S09-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S09-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Race requests against the last units, retry a failed job and reconcile a period transition.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
