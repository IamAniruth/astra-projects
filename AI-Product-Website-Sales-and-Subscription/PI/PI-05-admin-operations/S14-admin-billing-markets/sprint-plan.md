# WS S14: Admin billing, offers and market controls

**Status:** Planned  
**PI:** [PI-05 Owner administration and support](../README.md)  
**Module:** M14  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a responsible service operator, I can rely on admin billing, offers and market controls with explicit scope, correct access and traceable outcomes.

- WS-S14-F01: Billing event review, reconciliation and temporary access controls
- WS-S14-F02: Offer/version migration previews and market readiness administration

## Dependencies and entry criteria

S06-S09 commerce and S13 admin shell; market activation requires S16 evidence.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S14-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S14-T02 | Frontend/product design | Subscription/invoice/event detail, adjustments and configuration readiness screens. |
| WS-S14-T03 | Backend/data | Reasoned expiring overrides, operation IDs, version checks and audited change outcomes. |
| WS-S14-T04 | Integration/operations | Preview provider-calculated changes; use authorized provider tools for deferred financial operations. |
| WS-S14-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S14-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S14-AC1: Replaying an event or clicking twice cannot duplicate credits, charges or entitlements.
- [ ] WS-S14-AC2: Existing customers keep offer terms unless explicit migration occurs; temporary access preserves payment truth.
- [ ] WS-S14-AC3: New markets stay disabled without evidence and disabling new sales does not terminate existing subscriptions.
- [ ] WS-S14-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S14-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S14-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Reconcile a failed event, expire access exception and preview a price migration without applying it implicitly.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
