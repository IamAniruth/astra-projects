# WS S01: Offer, buyer and market discovery

**Status:** Planned  
**PI:** [PI-01 Commercial scope and secure foundation](../README.md)  
**Module:** M01  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a product/commercial owner, I can rely on offer, buyer and market discovery with explicit scope, correct access and traceable outcomes.

- WS-S01-F01: Choose one product/buyer, pilot scope and success criteria
- WS-S01-F02: Record seller/market/provider eligibility and commercial decisions

## Dependencies and entry criteria

None; source documents are the proposed scope, not accepted business evidence.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S01-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S01-T02 | Frontend/product design | Product selection, seller entity, initial market/language/currency, setup/pilot/subscription terms, budget and permitted samples. |
| WS-S01-T03 | Backend/data | Buyer/offer decision register and market eligibility evidence checklist. |
| WS-S01-T04 | Integration/operations | Review current official provider contracts during implementation; no provider or price is selected by this plan. |
| WS-S01-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S01-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S01-AC1: No unvalidated price, availability, capacity or testimonial is published.
- [ ] WS-S01-AC2: A named buyer/domain reviewer accepts scope and measurable pilot criteria.
- [ ] WS-S01-AC3: Unknown eligibility or product feasibility blocks taking payment.
- [ ] WS-S01-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S01-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S01-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Compare the agreed offer with actual buyer evidence and show an unsupported-market case.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
