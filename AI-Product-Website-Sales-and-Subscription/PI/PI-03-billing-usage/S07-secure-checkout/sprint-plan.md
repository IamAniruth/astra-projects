# WS S07: Eligible checkout and verified payment intake

**Status:** Planned  
**PI:** [PI-03 Payments, subscriptions and usage](../README.md)  
**Module:** M07  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a customer or authorized service owner, I can rely on eligible checkout and verified payment intake with explicit scope, correct access and traceable outcomes.

- WS-S07-F01: Provider-hosted checkout using server-selected offers
- WS-S07-F02: Verified idempotent webhook ingestion and billing references

## Dependencies and entry criteria

S03 identity, S06 validated offer and actual provider approval/configuration; sandbox first.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S07-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S07-T02 | Frontend/product design | Checkout/pending/success/failure screens without raw card collection. |
| WS-S07-T03 | Backend/data | Server checkout creation, signed-event verification, unique event IDs and safe references. |
| WS-S07-T04 | Integration/operations | Integrate eligible provider sandbox, secure secrets and restricted receipt logs. |
| WS-S07-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S07-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S07-AC1: Tampered client prices/market IDs cannot change authoritative charges.
- [ ] WS-S07-AC2: A success redirect grants no paid access without server confirmation.
- [ ] WS-S07-AC3: Invalid signatures fail and repeated checkout/event requests do not duplicate effects.
- [ ] WS-S07-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S07-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S07-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Test success, failed and abandoned checkout plus forged redirect/signature and repeated events.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
